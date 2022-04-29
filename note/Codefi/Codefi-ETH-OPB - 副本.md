



##  Orchestrate  测试



### 连接ETH_OPB（武汉链）

*************************************


----------------------------------
List endpoints and services
----------------------------------
JSON-RPC HTTP service endpoint                 : http://localhost:8545
JSON-RPC WebSocket service endpoint            : ws://localhost:8546
Web block explorer address                     : http://localhost:25000/
Prometheus address                             : http://localhost:9090/graph
Grafana address                                : http://localhost:3000/d/XE4V0WGZz/besu-overview?orgId=1&refresh=10s&from=now-30m&to=now&var-system=All



#### 注册链

> ```apl
> TENANT_ID=foo npm run generate-jwt
> 
> 
> 租户jwt 
> tenantID=foo：
> eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsiaHR0cHM6Ly9hdXRoMC5jb20vYXBpL3YyLyJdLCJleHAiOjE2Mjg5MTkxMzEsImlhdCI6MTYyODgzMjczMSwiaXNzIjoiT3JjaGVzdHJhdGUiLCJqdGkiOiIyYjE3ZDQ2ZS05NDBmLTQ5M2QtOTdlNC0zY2I1ZTk2OGRkMDYiLCJuYmYiOjE2Mjg4MzI3MzEsIm9yY2hlc3RyYXRlLmluZm8iOnsidGVuYW50X2lkIjoiZm9vIn0sInNjcCI6WyJyZWFkOnVzZXJzIiwidXBkYXRlOnVzZXJzIiwiY3JlYXRlOnVzZXJzIl0sInN1YiI6ImUyZS10ZXN0In0.Jc_KPamspmfrS8NstI6IzljJY_GXHIt0d3D9KYdEOoYdK2M_V99oSol22f4iep0h6Wsd7KaBKLCMXdba00CqjL-bXQkr2sedglUML2KcXhAT3e84eynNdCZAEtSXIjD4GDe5nww5kdts9Huv1pwGguJ0pgjwtcKisA1epGP86nRaykSspEoKLSJ2DweCNHdg_6-kOQjYYZccZ6JfQ1sovVXvdMpFN76UlpQNO40WRGJkqUuavjs2WIKTBcR-Ko9iL0a3ikkDNDyb-wqlPn-cqtTVYCmWcghxSE3hZtULUIfUkTBLrjxb1w5hz-hx1EgFV4MfhJklJQbbi70kBXUW_Q
> 
> tenantID=_：
> eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsiaHR0cHM6Ly9hdXRoMC5jb20vYXBpL3YyLyJdLCJleHAiOjE2Mjg5MTk3NTcsImlhdCI6MTYyODgzMzM1NywiaXNzIjoiT3JjaGVzdHJhdGUiLCJqdGkiOiIwMGU4ZTVlNS0yNWJiLTQ1MzUtOGNiMS1jMTI5ZjkzZTZiYTIiLCJuYmYiOjE2Mjg4MzMzNTcsIm9yY2hlc3RyYXRlLmluZm8iOnsidGVuYW50X2lkIjoiXyJ9LCJzY3AiOlsicmVhZDp1c2VycyIsInVwZGF0ZTp1c2VycyIsImNyZWF0ZTp1c2VycyJdLCJzdWIiOiJlMmUtdGVzdCJ9.J1ziOPfrNY32Akpg-RBAMOixcNuoCt4jnCSyjAs9_Bi02ybkCP8wxV0i6fm5jft1hihFZhtZrUrgGLaWwObZxq_ijsLmbN3PhijVjzfgLRax_gRj8oYtv7Mg3ORfWhusBJXEaFBBKpaOQD4e7MAQRnFXMlGddzR50uR5666aDX8wG2jRwyEsks_unzLDt5l7XRube00joUgbGbxHghwvBiNcMmF-fLuCiDJk9T_1Pv7Yi4jAS3GiqzjGSFXzOiajHBkVe4yDHqkDKGXDnLufdm4tlWmRU5i3ozhUcGDoE4cke_hgyI_lUfCaeub46hXb8bAwqhEawGnMA0MFYQghSQ
> ```



------



#### 注册链

```erlang
请求：{{baseUrl}}/chains
租户ID：tenantID=foo
响应：
{
    "uuid": "62384e0a-e416-42c1-83ce-88eabcee505e",
    "name": "ethfoo",
    "tenantID": "foo",
    "urls": [
        "http://52.83.148.57:3002"
    ],
    "chainID": "5555",
    "listenerDepth": 0,
    "listenerCurrentBlock": 732986,
    "listenerStartingBlock": 732986,
    "listenerBackOffDuration": "1s",
    "listenerExternalTxEnabled": false,
    "privateTxManager": {
        "UUID": "120ae09c-c5f3-4250-8fb3-d08e06976b42",
        "ChainUUID": "62384e0a-e416-42c1-83ce-88eabcee505e",
        "URL": "http://tessera:3000",
        "Type": "Tessera",
        "CreatedAt": "2021-08-13T06:08:13.186055Z"
    },
    "createdAt": "2021-08-13T06:08:13.186055Z",
    "updatedAt": "2021-08-13T06:08:13.186055Z"
}


```

```js
请求：{{baseUrl}}/chains
租户ID：tenantID=_
响应：
{
    "uuid": "1f3110ec-a173-4ce3-a8f1-43da54e60f87",
    "name": "eth_",
    "tenantID": "_",
    "urls": [
        "http://52.83.148.57:3002"
    ],
    "chainID": "5555",
    "listenerDepth": 0,
    "listenerCurrentBlock": 733026,
    "listenerStartingBlock": 733026,
    "listenerBackOffDuration": "1s",
    "listenerExternalTxEnabled": false,
    "privateTxManager": {
        "UUID": "bbf08b88-adaa-42c5-8f49-f9692c500974",
        "ChainUUID": "1f3110ec-a173-4ce3-a8f1-43da54e60f87",
        "URL": "http://tessera:3000",
        "Type": "Tessera",
        "CreatedAt": "2021-08-13T06:14:49.886928Z"
    },
    "createdAt": "2021-08-13T06:14:49.886928Z",
    "updatedAt": "2021-08-13T06:14:49.886928Z"
}

```





### 创建用户

```json
请求：npm run get-accounts

使用住户ID：_ 的token
{
    "alias": "account_all",
    "address": "0x778444308F48136672895F15235E215F37E43d88",
    "publicKey": "0x04b6fc86d16a137df4a78fb08e225f3fe67ddbc1a9c1f591acf659a51cd2a23a5ccfd5424f622dd759fee8e1440afdb1783c434fb465da3f3b459cbafb441d9a1e",
    "compressedPublicKey": "0x02b6fc86d16a137df4a78fb08e225f3fe67ddbc1a9c1f591acf659a51cd2a23a5c",
    "tenantID": "_",
    "attributes": {
        "property1": "string",
        "property2": "string"
    },
    "createdAt": "2021-08-13T06:30:32.028195Z",
    "updatedAt": "2021-08-13T06:30:32.028195Z"
}

使用住户ID：foo 的token
{
    "alias": "account_foo",
    "address": "0xEDd6Cb0Fdb33Ae15D0AACC6848932c588036BFf0",
    "publicKey": "0x04b10372859bc4c9beab1619f065cee2a1fd5b0ceb9718b8288b5b1fca25057a2b2f1f6295031012b2ec8d9399c395e264e54d55d63478a618aeaff04645c0a02d",
    "compressedPublicKey": "0x03b10372859bc4c9beab1619f065cee2a1fd5b0ceb9718b8288b5b1fca25057a2b",
    "tenantID": "foo",
    "attributes": {
        "property1": "string",
        "property2": "string"
    },
    "createdAt": "2021-08-13T06:32:09.360844Z",
    "updatedAt": "2021-08-13T06:32:09.360844Z"
}
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

