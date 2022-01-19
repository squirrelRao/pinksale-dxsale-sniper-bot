# Pinksale & DxSale sniper bot

## 
实现基于Pinksale 或 DxSale 发布平台上预售加密货币的竞购

## 
* 可设定相关参数如： gas price, gas limit, etc
* 支持竞购多个交易地址
* 支持毫秒级竞购

## 需要环境
* npm 6.0.0 or above
* NodeJS 10.0.0 or above

## 安装
* 安装Node环境，进入Node官网下载安装即可：https://nodejs.org/en/ 
 （由于现在node已自带npm,无需单独安装）,安装完成后使用npm -v验证即可
* 克隆项目,进入项目目录，执行命令安装相关依赖包：npm install
* 安装完毕

## 用法
进入项目目录，执行: node sniper-bot.js <参数>   ( pm2使用方法可参考pm2相关命令）
参数之间使用空格分割

#### 必填参数
* presaleContractAddress - 预售项目在pinksale或DxSale上的合约地址（ contract address )
* buyingBnbAmount - 抢购预售货币支付的BNB数量，整数或小数
* senderPrivateKey - 个人钱包的PrivateKey
  支持多个钱包竞购，当有多个钱包时，privateKey之间使用逗号分隔，  senderPrivateKey=0x8da4ef21b864d2cc526dbdb2a120bd2874c36c9d0a1fb7f8c63d7f7a8b41de8f,0x3da3ef21b123d2cc526dbdb2a120bd2874c36c9d0a1fb7f8c63d7f7a8b42de8E

#### 可选参数
* node - 竞购项目所处的区块链节点，默认为标准的BSC节点，该节点用以提供交易加签等服务，也可以是自己搭建通过Geth的RPC节点中断服务（类似：https://localhsot:8458)
* gasLimit - 在交易中愿意消耗的最大gas,默认是:500000.
* gasPrice - 交易中Gas的Gwei价格, 默认是:10 Gwei.
* createLogs - 如果未true,将日志记录到./logs 目录里
* cronTime - 设置执行竞购的定时器时间，表达式遵循cron规则.默认是`'*/100 * * * * * *'` 每100毫秒执行一次竞购.
* botInitialDelay - 首次启动竞购时的延迟时间，默认为10秒延迟，如果设置为0则无延迟，直接按cron规则执行竞购
* name - 默认为空，可用于区分竞购不同的加密货币Token

#### 例子:
* BSC测试链环境下竞购：

  node sniper-bot.js node=https://data-seed-prebsc-1-s1.binance.org:8545 presaleContractAddress=合约地址 buyingBnbAmount=BNB数量 senderPrivateKey=个人钱包KEY createLogs=true

* BSC链环境下竞购: 
  
  node sniper-bot.js node=https://bsc-dataseed.binance.org/ presaleContractAddress=合约地址 buyingBnbAmount=BNB数量 senderPrivateKey=个人钱包KEY createLogs=true
  

