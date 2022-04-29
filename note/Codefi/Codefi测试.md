

##  Codefi Test



### 使用比速

------

```erlang
请求：npm run register-chain

响应：

{
  uuid: '83de5048-3d62-45e3-a3b7-77a3963ba956',
  name: 'devbsu',
  tenantID: '_',
  urls: [ 'http://network_member1besu_1:8545' ],
  chainID: '1337',
  listenerDepth: 0,
  listenerCurrentBlock: 4754,
  listenerStartingBlock: 4754,
  listenerBackOffDuration: '5s',
  listenerExternalTxEnabled: false,
  createdAt: '2021-08-11T06:08:24.483213Z',
  updatedAt: '2021-08-11T06:08:24.483213Z'
}


再次注册链：

{
  isHttpError: true,
  status: 409,
  headers: {
    'content-type': 'application/json',
    'x-content-type-options': 'nosniff',
    date: 'Wed, 11 Aug 2021 05:14:05 GMT',
    'content-length': '101',
    connection: 'close'
  },
  data: {
    message: 'DB101@use-casevim s.register-chain: a chain with the same name already exists',
    code: 897281
  }
}

```

***

```erlang
请求：npm run generate-account

响应：
{
  alias: 'account-16',
  address: '0xC0f50fEBBA7d83d5236AF4002252C6686f3f1f86',
  publicKey: '0x04d357fef54fa8dc11ece7e4d00a210fa7f80f9852498ab7b33f736994d3ebc1c0f2df6d746b06d9e6046a578d1fb38c134b0dbb6ef9d7392cddfa05bb65d23279',
  compressedPublicKey: '0x03d357fef54fa8dc11ece7e4d00a210fa7f80f9852498ab7b33f736994d3ebc1c0',
  tenantID: '_',
  createdAt: '2021-08-11T05:20:00.214506Z',
  updatedAt: '2021-08-11T05:20:00.214506Z'
}


再次请求：
{
  isHttpError: true,
  status: 500,
  headers: {
    'content-type': 'application/json',
    'x-content-type-options': 'nosniff',
    date: 'Wed, 11 Aug 2021 06:15:08 GMT',
    'content-length': '107',
    connection: 'close'
  },
  data: {
    message: 'FF000@: Internal server error. Please ask an admin for help or try again later',
    code: 1044480
  }
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
    alias: 'account-16',
    address: '0xC0f50fEBBA7d83d5236AF4002252C6686f3f1f86',
    publicKey: '0x04d357fef54fa8dc11ece7e4d00a210fa7f80f9852498ab7b33f736994d3ebc1c0f2df6d746b06d9e6046a578d1fb38c134b0dbb6ef9d7392cddfa05bb65d23279',
    compressedPublicKey: '0x03d357fef54fa8dc11ece7e4d00a210fa7f80f9852498ab7b33f736994d3ebc1c0',
    tenantID: '_',
    createdAt: '2021-08-11T05:20:00.214506Z',
    updatedAt: '2021-08-11T05:20:00.214506Z'
  }
]

```



```erlang
请求： npm run create-faucet
响应：
{
  uuid: '8794f197-53c7-448a-838a-93a5a375ffdb',
  name: 'devbsu-faucet',
  tenantID: '_',
  chainRule: '83de5048-3d62-45e3-a3b7-77a3963ba956',
  creditorAccount: '0xC0f50fEBBA7d83d5236AF4002252C6686f3f1f86',
  maxBalance: '100000000000000000',
  amount: '60000000000000000',
  cooldown: '10s',
  createdAt: '2021-08-11T06:19:10.844609Z',
  updatedAt: '2021-08-11T06:19:10.844609Z'
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

