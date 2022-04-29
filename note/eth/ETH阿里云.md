
---

> node1

```
geth --networkid 9999 --datadir node1 --syncmode 'full' -verbosity 3 --ipcdisable --port 30311 -unlock '0x6d6844b9E972E15a07f640430b12Db3C1D765D12' --password node1/password.txt --mine console 2>> node1/node1.log

```

> node2

```
geth --networkid 9999 --datadir node2 --syncmode 'full' -verbosity 3 --ipcdisable --port 30312 --rpc --rpcaddr 127.0.0.1 --rpcport 8547 --rpcapi 'eth,net,web3' --ws --ws.port 8557 --ws.addr 127.0.0.1 --ws.api 'eth,net,web3'  --allow-insecure-unlock console 2>> node2/node2.log

geth --networkid 9999 --datadir node2 --syncmode 'full' -verbosity 3 --ipcdisable --port 30312 -unlock '0xc63cc046a2e7e40bfc1e071f7557d058346b0098' --password node2/password.txt --mine console 2>> node2/node2.log

```

> node3

```
geth --networkid 9999 --datadir node3 --syncmode 'full' -verbosity 3 --ipcdisable --port 30313 --rpc --rpcaddr 127.0.0.1 --rpcport 8548 --rpcapi 'eth,net,web3' --ws --ws.port 8558 --ws.addr 127.0.0.1 --ws.api 'eth,net,web3'  --allow-insecure-unlock console 2>> node3/node3.log

```

> 
