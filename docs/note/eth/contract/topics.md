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

