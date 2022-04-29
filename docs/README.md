# Hey Boy 

> An awesome project.

<img src="https://s2.loli.net/2022/04/29/q2wCnubro91WURj.jpg" alt="1" style="zoom: 25%;" />

### 武汉链

####  合约批量转账

```
// SPDX-License-Identifier: BSN
pragma solidity ^0.8.0;

import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
import "@openzeppelin/contracts-upgradeable/access/OwnableUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable/proxy/utils/UUPSUpgradeable.sol";
import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";

contract BsnOfficialRechargeEther is
    Initializable,
    OwnableUpgradeable,
    UUPSUpgradeable
{
    event BatchRecharge(
        address indexed operator,
        address[] toList,
        uint256[] amounts
    );

    event Receive(address indexed from, address indexed to, uint256 amount);

    constructor() payable initializer {}

    function initialize() public initializer {
        __Ownable_init();
        __UUPSUpgradeable_init();
    }

    function _authorizeUpgrade(address newImplementation)
        internal
        override
        onlyOwner
    {}

    function batchRecharge(address[] memory toList, uint256[] memory amounts)
        public
        payable
        onlyOwner
        returns (bool)
    {
        require(
            toList.length > 0 && toList.length == amounts.length,
            "BsnOfficialRechargeEther: Invalid parameters"
        );
        for (uint32 i = 0; i < toList.length; i++) {
            require(
                toList[i] != address(0),
                "BsnOfficialRechargeEther: zero address"
            );
            payable(toList[i]).transfer(amounts[i]);
        }
        emit BatchRecharge(_msgSender(), toList, amounts);
        return true;
    }

    function balance() public view returns (uint256) {
        return address(this).balance;
    }

    function version() public pure returns (string memory) {
        return "v1.0";
    }

    fallback() external payable {}

    receive() external payable {
        emit Receive(_msgSender(), address(this), msg.value);
    }
}
```



#### 交易

##### 错误示例

><font face="微软雅黑" size=8 color=#130c0e >nonce </font>
>
>* 使用打包交易的nonce
>
>> {"jsonrpc":"2.0","id":2,"error":{"code":-32000,"message":"nonce too low"}}
>
>* 并发交易(其中一笔已经进去交易池，但还未打包)
>
>> {"jsonrpc":"2.0","id":5,"error":{"code":-32000,"message":"already known"}}
>
>* 覆盖pending的交易，gasPrice低于原来的110%：覆盖掉一笔处于pending状态的交易gas price需要高于原交易的110%
>  如果覆盖成功原交易hahs无效。
>
>> {"jsonrpc":"2.0","id":5,"error":{"code":-32000,"message":"replacement transaction underpriced"}}
>
>* 使用超前的nonce
>
>> * 会生成交易Hash，但是交易不会被打包，该交易会处于pending状态<font face="微软雅黑" size=4 color=#f00 >【非可执行交易在该节点交易池中保存3小时，超时将会从queue 队列中移除】</font>，且只会在发起交易的节点上<font face="微软雅黑" size=4 color=#f00 >【非可执行交易，不会被广播至其他节点】</font>
>>
>> * 使用：eth_getTransactionByHash 在交易的节点上可查看交易信息
>>
>> * 使用：eth_getTransactionReceipt  查看回执
>>
>>   ```
>>   # 该返回值被eth-proxy 包装过
>>   {"jsonrpc":"2.0","id":0,"error":{"code":403,"message":"Proxy Error","name":"InternalProxyError","internalError":"Both rpc err and result are null"}}
>>   ```
>>
>>   ```
>>   # 该返回值是eth原生响应
>>   {"jsonrpc":"2.0","id":0,"result":null}
>>   ```
>>
>>   <font face="微软雅黑" size=5 color=#339933>解决办法</font>
>>
>>   >* nonce 补全
>>
>> >  补全前面跳过的nonce，pending的交易会自动被共识节点打包。



><font face="微软雅黑" size=5 color=#130c0e >gasPrice</font>
>
>* gasPrice 低于武汉链的 **1Gwei**
>
> > * 由于低于最低 **1Gwei**，该交易不会被共识节点处理一直处于pending状态且会同步至其他节点。
> >
> > * 使用：eth_getTransactionByHash 可以查看该交易。
> >
> > * 使用：eth_getTransactionReceipt  查看回执
> >
> >   ```
> >   # 该返回值被eth-proxy 包装过
> >   {"jsonrpc":"2.0","id":0,"error":{"code":403,"message":"Proxy Error","name":"InternalProxyError","internalError":"Both rpc err and result are null"}}
> >   ```
> >
> >   <font face="微软雅黑" size=5 color=#339933>解决办法</font>
> >
> >   > * 该笔交易，使用更高的gasPrice去覆盖【nonce相同】。
> >   >   注意：原交易Hash被新的Hash覆盖，相当于原Hash作废，节点上查不到任何信息。



><font face="微软雅黑" size=5 color=#130c0e >gasLimit</font>
>
>* gasLimit 低于该笔交易的使用量
>
> > 交易响应：{"jsonrpc":"2.0","id":2,"error":{"code":-32000,"message":"intrinsic gas too low"}}
>
>* gasLimit 太高
>
> > * 超过配置上限 **(1.00 ether)**
> >   交易响应：{"jsonrpc":"2.0","id":2,"error":{"code":-32000,"message":"tx fee (200000.00 ether) exceeds the configured cap (1.00 ether)"}}





#### 节点配置

##### 创始块文件

```json
{
  "config": {
    "chainId": 5555,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip150Hash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "clique": {
      "period": 10,
      "epoch": 30000
    }
  },
  "nonce": "0x0",
  "timestamp": "0x60a62e6d",
  "extraData": "0x0000000000000000000000000000000000000000000000000000000000000000d17f7a5ae36efaf77d2192569346539ba2498c980000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit": "0x47b760",
  "difficulty": "0x1",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "alloc": {
    "d17f7a5ae36efaf77d2192569346539ba2498c98": {
      "balance": "0x200000000000000000000000000000000000000000000000000000000000000"
    }
  },
  "number": "0x0",
  "gasUsed": "0x0",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```



### 浏览器

### 运维

| 服务名称     | 服务器IP | 端口号 | 部署目录                                 | 配置路径                       |
| ------------ | -------- | ------ | ---------------------------------------- | ------------------------------ |
| 运维接口-主  | 172      | 17506  | /bsn/yunwei	jar                       |                                |
| 运维接口-从  | 172      | 17506  | /bsn/yunwei	jar                       |                                |
| 运维管理系统 | 172      | 17503  | /home/tomcat-yunwei/war                  |                                |
| 账单定时任务 | 172      | 17510  | /home/tomcat-yunwei-bill	Tomcat/warcd |                                |
| 监控中心     | 172      | 17500  | /chainnet/tomcat-monitor	Tomcat/war   |                                |
| OPB 采集器   | 161      | 29021  | /bsn/go/src/node-collect/                | cd /bsn/opb/tx                 |
| OPB_定时监控 | 172      | 17504  | /bsn/tomcat-task                         | cd /bsn/tomcat-task_conf/conf/ |



### 公链



