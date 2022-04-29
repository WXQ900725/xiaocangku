```
web3j solidity generate C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721\DDC721.bin C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721\DDC721.abi -o C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721 -p com.a.c
```

展开

### solidty 转 java

1. 进入web3j所在目录

   ```
   E:\web3j-3.4.0\web3j-3.4.0\bin
   ```

2. 打开CMD

3. 输入要转换的命令：web3j solidity generate <编译的bin文件地址> <编译的abi文件地址> -o <输出目录> -p <java包名>

   ```txt
   web3j solidity generate C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721\DDC721.bin C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721\DDC721.abi -o C:\Users\DELL\Downloads\contracts\contracts\logic\DDC721 -p com.a.c
   ```

   ```
   web3j solidity generate E:\web3j-3.4.0\contracts\contracts\logic\Charge\Charge.bin E:\web3j-3.4.0\contracts\contracts\logic\Charge\Charge.abi -o E:\web3j-3.4.0\contracts\contracts\logic\Charge\ -p com
   
   
   ```

   ```
   web3j solidity generate E:\web3j-3.4.0\tool\BsnBatchTransfer.bin E:\web3j-3.4.0\tool\BsnBatchTransfer.abi -o E:\web3j-3.4.0\tool\ -p com
   ```
   
   
   
   #### 权限
   
   ```
   web3j solidity generate -a E:\web3j-4.5.5\contracts\contracts\logic\Authority\Authority.abi -b E:\web3j-4.5.5\contracts\contracts\logic\Authority\Authority.bin -o E:\web3j-4.5.5\contracts\contracts\logic\Authority\ -p com
   ```
   
   #### 充值
   
   ```
   web3j solidity generate -a E:\web3j-4.5.5\contracts\contracts\logic\Charge\Charge.abi -b E:\web3j-4.5.5\contracts\contracts\logic\Charge\Charge.bin -o E:\web3j-4.5.5\contracts\contracts\logic\Charge\ -p com
   ```
   
   #### 721
   
   ```
   web3j solidity generate -a E:\web3j-4.5.5\contracts\contracts\logic\DDC721\DDC721.abi -b E:\web3j-4.5.5\contracts\contracts\logic\DDC721\DDC721.bin -o E:\web3j-4.5.5\contracts\contracts\logic\DDC721\ -p com
   ```
   
   #### 1155
   
   ```
   web3j solidity generate -a E:\web3j-4.5.5\contracts\contracts\logic\DDC1155\DDC1155.abi -b E:\web3j-4.5.5\contracts\contracts\logic\DDC1155\DDC1155.bin -o E:\web3j-4.5.5\contracts\contracts\logic\DDC1155\ -p com
   ```
   
   

