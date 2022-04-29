



> 生产环境浏览器
>
> https://expedition.dev/?rpcUrl=https://opbningxia.bsngate.com:18602/api/7683ab9fd8ba4edbbcbba2824a646f41/rpc

> 测试环境浏览器
>
> http://161.189.177.106:3000/



> 文件改动记录  .substring(0,66)

1. expedition-1.11.2\src\components\BlockView\BlockView.tsx     **hexToString(extraData.substring(0,66))；**
2. expedition-1.11.2\src\components\MinerStatsTable.tsx     **return hexToString(item.extraData.substring(0,66));**
3. expedition-1.11.2\src\components\BlockCard \BlockCard.tsx  **hexToString(block.extraData!.substring(0,66))**
4. expedition-1.11.2\src\components\MinerStats.tsx   **hexToString(b.extraData.substring(0,66)))**
5. expedition-1.11.2\src\components\BlockList\BlockList.tsx  **hexToString(b.extraData).substring(0, 20)**
5. 首页 页面：expedition-1.11.2\src\App.tsx

默认ExtraData：  https://github.com/ethereum/wiki/wiki/Default-Extra-Data-Standard

https://ropsten.etherscan.io/



C:\Users\DELL\Desktop\ETH_OPB文档\browser\expedition-1.11.2\expedition-1.11.2\src\components\BlockList\BlockList.tsx

# Expedition



### Configurations

#### Set rpc via url

`?rpcUrl=` [武汉链网关地址].

例如: https://localhost:3000/?rpcUrl=https://services.jade.builders/core-geth/kotti/1.11.2

#### Configure default urls via environment variables

Override eth url

```
REACT_APP_ETH_RPC_URL=https://services.jade.builders/core-geth/mainnet/1.11.2 npm start


REACT_APP_ETH_RPC_URL=https://opbtest.bsngate.com:18602/api/ethproject/rpc/ npm start

REACT_APP_ETH_RPC_URL=http://161.189.177.106:3004/ npm start &

```

**OR**

Override service runner url

```
REACT_APP_SERVICE_RUNNER_URL=https://services.jade.builders/ npm start

https://opbtest.bsngate.com:18602/api/59efa0aacb1e477e9718f3df0e795ddc/rpc
?rpcUrl=https://opbtest.bsngate.com:18602/api/59efa0aacb1e477e9718f3df0e795ddc/rpc


REACT_APP_SERVICE_RUNNER_URL=https://opbtest.bsngate.com:18602/api/59efa0aacb1e477e9718f3df0e795ddc/rpc/ npm start
```

### 生产部署配置

```
src\hooks\useEthRPC.ts
第 24 行修改：let baseUrl= "http://161.189.177.106:3004";


src\hooks\useChainList.ts
第 13 行修改：rpc: ["https://opbningxia.bsngate.com:18602/api/7683ab9fd8ba4edbbcbba2824a646f41/rpc"],
```



