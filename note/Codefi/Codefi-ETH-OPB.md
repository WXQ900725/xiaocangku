{

  "uuid": "e9aed5e8-0bbd-442d-8311-96a952bf0e5e",

  "name": "ethopb",

  "tenantID": "foo",

  "urls": [

​    "http://52.83.148.57:3002"

  ],

  "chainID": "5555",

  "listenerDepth": 0,

  "listenerCurrentBlock": 732952,

  "listenerStartingBlock": 732952,

  "listenerBackOffDuration": "1s",

  "listenerExternalTxEnabled": **false**,

  "privateTxManager": {

​    "UUID": "9366df14-6453-4847-b0b5-edf1ab1124b5",

​    "ChainUUID": "e9aed5e8-0bbd-442d-8311-96a952bf0e5e",

​    "URL": "http://tessera:3000",

​    "Type": "Tessera",

​    "CreatedAt": "2021-08-13T06:02:26.706716Z"

  },

  "createdAt": "2021-08-13T06:02:26.706716Z",

  "updatedAt": "2021-08-13T06:02:26.706716Z"

}





##  ETH-测试



### 使用ETH_OPB

*************************************
Quorum Dev Quickstart 
*************************************
----------------------------------
List endpoints and services
----------------------------------
JSON-RPC HTTP service endpoint                 : http://localhost:8545
JSON-RPC WebSocket service endpoint            : ws://localhost:8546
Web block explorer address                     : http://localhost:25000/
Prometheus address                             : http://localhost:9090/graph
Grafana address                                : http://localhost:3000/d/XE4V0WGZz/besu-overview?orgId=1&refresh=10s&from=now-30m&to=now&var-system=All



JSON-RPC HTTP service endpoint                 : http://106.75.16.183:8545
JSON-RPC WebSocket service endpoint            : ws://106.75.16.183:8546
Web block explorer address                     : http://106.75.16.183:25000/
Prometheus address                             : http://106.75.16.183:9090/graph
Grafana address                                : http://106.75.16.183:3000/d/XE4V0WGZz/besu-overview?orgId=1&refresh=10s&from=now-30m&to=now&var-system=All



------

```erlang
请求：npm run register-chain

响应：

{
  uuid: '1ecfc15f-f9f3-47a3-98e4-6fe98e7bf3e7',
  name: 'devopb',
  tenantID: '_',
  urls: [ 'http://52.83.148.57:3002' ],
  chainID: '5555',
  listenerDepth: 0,
  listenerCurrentBlock: 717429,
  listenerStartingBlock: 717429,
  listenerBackOffDuration: '5s',
  listenerExternalTxEnabled: false,
  createdAt: '2021-08-11T10:55:17.579835Z',
  updatedAt: '2021-08-11T10:55:17.579835Z'
}


vim .env
CHAIN_UUID=1ecfc15f-f9f3-47a3-98e4-6fe98e7bf3e7


```

***

```erlang
请求：npm run generate-account

响应：
{
  alias: 'account-97',
  address: '0x53d24C664F53fDAC11d1bd4C9B870Ea3b62EcA8A',
  publicKey: '0x0459d6ff20197936cdd64aca1c92a48066d2e507b374ae655da0a486cf03a68d6df1fb8f87909a062a1f8b5037284fd4b7153bd99c360a6bef63bbfd645783550a',
  compressedPublicKey: '0x0259d6ff20197936cdd64aca1c92a48066d2e507b374ae655da0a486cf03a68d6d',
  tenantID: '_',
  createdAt: '2021-08-11T10:56:49.27847Z',
  updatedAt: '2021-08-11T10:56:49.27847Z'
}


```

```js
请求：npm run get-latest-block
响应：
{
  "jsonrpc" : "2.0",
  "id" : 1,
  "result" : {
    "number" : "0x1310",
    "hash" : "0x2bec7d776aae84f311e81843588cf3c07d00ca72fb26b320705b1f1667e0246c",
    "mixHash" : "0x63746963616c2062797a616e74696e65206661756c7420746f6c6572616e6365",
    "parentHash" : "0xe32d8410a8b98e459fe3391d71cafad61d8afb96f7474dc1e223ccaa0b6507cc",
    "nonce" : "0x0000000000000000",
    "sha3Uncles" : "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
    "logsBloom" : "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "transactionsRoot" : "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "stateRoot" : "0xa061120042355a5e53e2b616c6568d26d60021a41f5d9787d827486840baf0df",
    "receiptsRoot" : "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "miner" : "0x06e23768a0f59cf365e18c2e0c89e151bcdedc70",
    "difficulty" : "0x1",
    "totalDifficulty" : "0x1311",
    "extraData" : "0xf90148a00000000000000000000000000000000000000000000000000000000000000000f8549406e23768a0f59cf365e18c2e0c89e151bcdedc70944592c8e45706cc08b8f44b11e43cba0cfc5892cb94ab5e7f4061c605820d3744227eed91ff8e2c890894c5327f96ee02d7bcbc1bf1236b8c15148971e1de808400000000f8c9b841c6e9abd6a83c34c10081f10462e024a2ba6874ef8a703bfb4f0c40ec3bc026a61975137f22dab536564dbb8fcced816a6243f779e09a6f145ff445ac6a8ec6f501b8419010c572d87af02452bc52eed2f60e57e6f4be2d831203f55277831c343a5d1245909687d66b5076bc38c303c78d40ed65426065e5842e19fd845215b287964a00b84196b799d69e6df023c8a4f06d025b33607046a7d9f0a14cee05936847f69bc5ca5925bc1f086beba28135e0b3424efbbf0aec81516620ea1f20f68d2e489923ac01",
    "size" : "0x34b",
    "gasLimit" : "0xf7b760",
    "gasUsed" : "0x0",
    "timestamp" : "0x61136a54",
    "uncles" : [ ],
    "transactions" : [ ]
  }
}



因为没有更新.env chainID:

dotenv -- cross-var curl -X POST -H 'Authorization: Bearer %AUTH_TOKEN%' --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest", false],"id":1}' %API_HOST%/proxy/chains/%CHAIN_UUID%

curl: (3) [globbing] error: bad range specification after pos 37
npm ERR! code ELIFECYCLE
npm ERR! errno 3
npm ERR! codefi-orchestrate-quick-start@3.1.0 get-latest-block: `dotenv -- cross-var curl -X POST -H 'Authorization: Bearer %AUTH_TOKEN%' --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest", false],"id":1}' %API_HOST%/proxy/chains/%CHAIN_UUID%`
npm ERR! Exit status 3
npm ERR! 
npm ERR! Failed at the codefi-orchestrate-quick-start@3.1.0 get-latest-block script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     /root/.npm/_logs/2021-08-11T05_44_59_390Z-debug.log

```

```erlang
请求：npm run get-accounts
响应：
[
  {
    alias: 'account-96',
    address: '0x05E59c4eBd08ECe882bb6638A2d26e816D77943D',
    publicKey: '0x043d2de2af1535e03ef5323c7979c7a47025b521e02c43e01bb47076a14d592297539cb170cadc075902271a760d707d5d9ca0750cad6dbf188a3b409f686283a7',
    compressedPublicKey: '0x033d2de2af1535e03ef5323c7979c7a47025b521e02c43e01bb47076a14d592297',
    tenantID: '_',
    createdAt: '2021-08-11T07:11:14.575001Z',
    updatedAt: '2021-08-11T07:11:14.575001Z'
  },
  {
    alias: 'account-81',
    address: '0xA4bD0701B6a4D89dEf27049a9dB681620F94B19B',
    publicKey: '0x041acc1241ce92550f592bd39db6324f6e8ab21900797a2bde51d5dfc94180787443e1f9502f116944d22aa023b2c88605823d5b8c3aaecb4347b9a11bf5681f50',
    compressedPublicKey: '0x021acc1241ce92550f592bd39db6324f6e8ab21900797a2bde51d5dfc941807874',
    tenantID: '_',
    createdAt: '2021-08-11T07:12:04.605687Z',
    updatedAt: '2021-08-11T07:12:04.605687Z'
  },
  {
    alias: 'account-97',
    address: '0xC7a54B2BC0eBD25F96406c25FCB4B0aEEABC78b1',
    publicKey: '0x04849b6d891eddfc8ba5462e15f9abeec47ed579c9272153616b4d4ce43cc0c522e819b4d806da55ee1717c92ec4daa080702675aea29053f9ffefacf984a97542',
    compressedPublicKey: '0x02849b6d891eddfc8ba5462e15f9abeec47ed579c9272153616b4d4ce43cc0c522',
    tenantID: '_',
    createdAt: '2021-08-11T07:12:11.401595Z',
    updatedAt: '2021-08-11T07:12:11.401595Z'
  }
]

```



```erlang
请求： npm run create-faucet
响应：
{
  uuid: 'b2a89dd9-1a07-4667-a167-35985778c252',
  name: 'devopb-faucet',
  tenantID: '_',
  chainRule: '1ecfc15f-f9f3-47a3-98e4-6fe98e7bf3e7',
  creditorAccount: '0x53d24C664F53fDAC11d1bd4C9B870Ea3b62EcA8A',
  maxBalance: '100000000000000000',
  amount: '60000000000000000',
  cooldown: '10s',
  createdAt: '2021-08-11T10:58:08.780222Z',
  updatedAt: '2021-08-11T10:58:08.780222Z'
}


如果不配置accountID：
{
  isHttpError: true,
  status: 400,
  headers: {
    'content-type': 'application/json',
    'x-content-type-options': 'nosniff',
    date: 'Wed, 11 Aug 2021 05:56:36 GMT',
    'content-length': '126',
    connection: 'close'
  },
  data: {
    message: "42300@: 42400@: invalid body (field validation for 'CreditorAccount' failed on the 'eth_addr' tag)",
    code: 271104
  }
}

```



```
请求：

响应：

```

### 合约部署

![image-20210811164317933](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20210811164317933.png)

如果使用bsn管理员账户提示找不到：

```
{
  isHttpError: true,
  status: 422,
  headers: {
    'content-type': 'application/json',
    'x-content-type-options': 'nosniff',
    date: 'Wed, 11 Aug 2021 08:46:29 GMT',
    'content-length': '113',
    connection: 'close'
  },
  data: {
    message: '42400@use-cases.send-tx.use-cases.send-tx.use-cases.create-job: failed to get account',
    code: 271360
  }
}

```





### 签名交易

```json
没有配置管理员：
{
    "uuid": "184638e9-eb97-434c-b171-bb42ea4af533",
    "idempotencyKey": "",
    "chain": "devopb",
    "params": {
        "from": "0xB506A542De5C5c9229D01D41E64760f27BB6d6D2",
        "to": "0xFB7b3E679D4aa518eB99f20FE368320317B52C22",
        "value": "5",
        "gasPrice": "1000000",
        "gas": "210000"
    },
    "jobs": [
        {
            "uuid": "e049e650-8123-433b-867a-d61252f1fd36",
            "chainUUID": "1ecfc15f-f9f3-47a3-98e4-6fe98e7bf3e7",
            "scheduleUUID": "184638e9-eb97-434c-b171-bb42ea4af533",
            "tenantID": "_",
            "transaction": {
                "from": "0xB506A542De5C5c9229D01D41E64760f27BB6d6D2",
                "to": "0xFB7b3E679D4aa518eB99f20FE368320317B52C22",
                "value": "5",
                "gasPrice": "1000000",
                "gas": "210000",
                "createdAt": "2021-08-12T02:35:41.934122Z",
                "updatedAt": "2021-08-12T02:35:41.934122Z"
            },
            "logs": [
                {
                    "status": "CREATED",
                    "at": "2021-08-12T02:35:41.934122Z"
                }
            ],
            "labels": {
                "property1": "wang",
                "property2": "xiaoqiang"
            },
            "annotations": {
                "gasPricePolicy": {
                    "priority": "very-high",
                    "retryPolicy": {
                        "interval": "2m0s",
                        "increment": 0.05,
                        "limit": 0.5
                    }
                }
            },
            "status": "CREATED",
            "type": "eth://ethereum/transaction",
            "createdAt": "2021-08-12T02:35:41.934122Z",
            "updatedAt": "2021-08-12T02:35:41.934122Z"
        }
    ],
    "createdAt": "0001-01-01T00:00:00Z"
}
```

