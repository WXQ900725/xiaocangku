# Hey Boy 

> laugh every day haha.

<div  style="width: auto; height: 50%; align-content: center;" >
<img src="https://s2.loli.net/2022/04/29/q2wCnubro91WURj.jpg"  />
</div>



### ETH

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

#### 合约事件签名

### 武汉链合约事件

> Charge

- 合约：0xf1b4db42b9a96ca2943c8e047552fd6e05d55396

| 合约事件                                                  | Topic                                                        |
| --------------------------------------------------------- | ------------------------------------------------------------ |
| PAY_EVENT = "Pay(address,address,bytes4,uint32,uint256)"; | 0x750e56f33a72767cd99db8943f4d04ca416c55fb783003107a869f5d5062dbab |
| SET_FEE_EVENT = "SetFee(address,byte4,uint)";             | 0x0f3aa16b3bb26e63f0052d988927aada372116b47d22b747a4b15175159fced3 |
| DELETE_FEE_EVENT = "DelFee(address,bytes4)";              | 0x2f93e067617701594eddb2443d90441c5bb959df555ae8e4d150f0a8bf8b006d |
| DELETE_DDC_EVENT = "DelDDC(address)";                     | 0x0ba05d508af447342f624920545278b6e2d2320ee40cb9eff56b89d21e1b25e8 |
| RECHARGE_EVENT = "Recharge(address,address,uint256)";     | 0x5472616e7366657228616464726573732c616464726573732c75696e7432353629 |

> ERC 721

- 合约：0xb4b46d6b2c7bc4389759f9ebe141cfe086771561

| 合约事件                                             | Topic                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| TRANSFER_EVENT = "Transfer(address,address,uint256)" | 0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef |
| FREEZE_EVENT = "EnterBlacklist(address,uint256)";    | 0x027b0995c9aa454830a50ece99b9507432deb5f7ff0173efc4429282c1710a36 |
| UNFREEZE_EVENT = "ExitBlacklist(address,uint256)";   | 0xaddb66f781fad31382e12b8ad189f90d41b9590625a6736ef67a2792f094874f |
| SET_URI_EVENT = "SetURI(uint256,string)";            | 0xee1bb82f380189104b74a7647d26f2f35679780e816626ffcaec7cafb7288e46 |

> ERC 1155

- 合约：0x5bf9e07abbf0cfbf21d02065529ae10e2ef0a375

| 合约事件                                                     | Topic                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TRANSFER_SINGLE_EVENT = "TransferSingle(address,address,address,uint256,uint256)"; | 0xc3d58168c5ae7397731d063d5bbf3d657854427343f4c083240f7aacaa2d0f62 |
| TRANSFER_BATCH_EVENT = "TransferBatch(address,address,address,uint256[],uint256[])"; | 0x4a39dc06d4c0dbc64b70af90fd698a233a518aa5d07e595d983b8c0526c8f7fb |
| FREEZE_EVENT = "EnterBlacklist(address,uint256)";            | 0x027b0995c9aa454830a50ece99b9507432deb5f7ff0173efc4429282c1710a36 |
| UNFREEZE_EVENT = "ExitBlacklist(address,uint256)";           | 0xaddb66f781fad31382e12b8ad189f90d41b9590625a6736ef67a2792f094874f |
| SET_URI_EVENT = "SetURI(uint256,string)";                    | 0xee1bb82f380189104b74a7647d26f2f35679780e816626ffcaec7cafb7288e46 |

> 权限

- 合约：0xb746e96bc24bc9bc11515b6f39cbe135d1b67a59

| 合约事件                                                     | Topic                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ADD_ACCOUNT_EVENT = "AddAccount(address,address)";           | 0xd246aa772c5574778b374ed1202c22bac9c87a04fd3624439c2642fa6ca62171 |
| DEL_ACCOUNT_EVENT = "DelAccount(address)";                   | 0xbcfb00e434003d9e7e1de894fbb844687d60d8c5c6d16ce452e91ca309483fdd |
| UPDATE_ACCOUNT_STATE_EVENT = "UpdateAccountState(address,uint8,uint8)"; | 0x3a99d1f905eb66fd0850dd6e2156668b6ae1f16f41cd49dd7c6d4fb5147f784f |





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



