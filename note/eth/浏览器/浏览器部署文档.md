# 浏览器部署说明



## 下载地址

-   https://github.com/xops/expedition

## 环境要求

- node `v10.15.3` or later
- npm `v6.4.1` or later

## 安装

克隆或下载项目，并安装依赖

```
git clone https://github.com/xops/expedition.git && cd expedition && npm install
```

## 用法

#### 启动浏览器

```
npm start
```

*默认访问地址 http://localhost:3000/.*

#### 配置

##### 通过Url设置RPC

`?rpcUrl=` https://opbningxia.bsngate.com:18602/api/[projectId]/rpc.

例如:

http://localhost:3000/?rpcUrl=https://opbningxia.bsngate.com:18602/api/[projectId]/rpc

#### 通过环境变量设置默认的武汉链网关地址

```
REACT_APP_ETH_RPC_URL=https://opbningxia.bsngate.com:18602/api/[projectId]/rpc npm start
```



## 关于网关地址中的 [projectId]

##### 请参考网关接入说明：[BSN Gateway](https://bsnbase.com/static/tmpFile/bzsc/openper/7-3-3.html)
