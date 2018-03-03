#### 挖矿三种方式:
1,POS机制,持有的权益越多,时间越长。每产生一个区块数据的奖励获得的越多。    
2,POW机制 solo方式挖矿,单枪匹马挖矿,直接获取主链上交易信息,完成区块数据信息之后发到主链上等待主链确认,如果确认成功,就可以获取奖励。   
![solo](https://github.com/ocaku/blockchain/blob/master/minepool/solo.png)   

3.POW机制 矿池挖矿,矿池是分布式计算,中心化数据架构,节点(矿机)越多矿池的算力就越大。   
![pool](https://github.com/ocaku/blockchain/blob/master/minepool/pool.png) 


矿工网络一般有:矿机、矿池、钱包等主要部分.递增遍历nNonce，必要时候可以微调nTime字段

#### getwork RPC  
其最大的意义是：数据与计算彻底分离。计算属于埋头苦干型,对区块数据一无所知。 逐渐被废弃的的协议,也有很多矿池兼容这个协议.      

主要工作是节点与主链之间的通讯同步区块数据.轮训 (实际上矿工只是改变header中的nNonce和nTime位置的数据, nNonce是一个随机数)


#### getblocktemplate RPC 
getwork 只是改进版. 区块数据是透明的,提高了搜索空间(Merkle树对每个交易记录查询的,筛选出未确认完的交易记录).      
矿池与主链之间通讯同步区块数据。矿工主动通过HTTP方式调用RPC接口(轮训),矿工只是改变header中的nNonce和nTime位置的数据,然后把所有的交易转换成Merkel树,来推导在区块标头中用到的Merkle root。每当额外的nonce字段需要改变，采矿软件就会重建Merkle的必要部分并更新块头中的时间和Merkle root的区域。     
数据冗余,获取交易记录不实时。

#### Stratum 协议
解决了getblocktemplate的数据冗余,获取交易记录不实时.
矿工与矿池之间的通讯,一般是tcp长连接。只需要发送少量的数据给矿工计算(只有区块数据header),矿工做完任务后同步到矿池. 区块数据完成之后 由矿池同步到主链上。 

Stratum侧重于给矿工自己构建标头所需的最少信息。无法在区块上增加或者检查交易信息.


### 矿池模式    
PPLNS和PPS,DGM,P2Pool四种种模式

##### PPLNS
PPLNS :Pay Per Last N Shares缩写 被称为真正的组队挖矿，根据每个矿机贡献的股份数量来分配奖励,按劳分配本次总收益。矿池收益高分配的就多,矿池收益低分配的就少。(收入不稳定，追求高收入的)

##### PPS
PPS:Pay Per Share 缩写,类似于上班工作,上一月班,发一个月的工资,收益稳定并不是很高。按照算力在矿池算力的占比,分配奖励。无论矿池收益高低,矿工都可以收到固定奖励.为了解决PPLNS 收益忽高忽低的情况。

##### DGM
DGM:Double Geometric Method. 双几何制. 结合了 PPLNS 和几何奖励类型, 使得矿池运营者能规避一部分风险. 矿池运营者在短期内收取部分挖出的货币, 然后在之後以正规化过的值返还给矿工，像电容充放电, 运气好每block少给你点, 运气差多给你点。 

##### P2Pool
P2Pool:P2Pool的挖矿节点工作在类似比特币区块链的一种shares链上。由于没有中心，所以也不会受到DoS攻击。和其他现有的矿池技术都不一样---每个节点工作的区块，都包括支付给前期shares的所有者以及该节点自己的比特币。99%的奖励（50BTC+交易费用）会平均分给矿工，另外0.5%会奖励给生成区块的人。



#### btcpool 架构图       
![btcpool](https://github.com/ocaku/blockchain/blob/master/minepool/btcpool.png)


1.GBTMakter 从主链获取最新的交易数据,打包数据发给MQ     
2.JobMaker 从MQ中获取打包数据,生成任务数据发给MQ      
3.Stratum Server 模块从MQ中获取任务,之后与miners数据通讯      
4.矿机提交slovedlog 到MQ     
5.BlockMaker 找到符合难度的sharelog数据,打包区块数据并广播       
6 PoolWatcher 监听其他矿池    
7.Mysql中sharelog user info    
8.Web    

##### 参考
btcpool  https://github.com/btccom/btcpool   
支持多币种挖矿 https://github.com/zone117x/node-open-mining-portal      
支持混合挖矿，源码地址https://github.com/sigwo/powerpool    
p2pool  https://github.com/p2pool/p2pool    
比特币开发指南    
由于GetWork已淘汰，其RPC的数据来源：https://bitcointalk.org/index.php?topic=51281.msg611856#msg611856              
Difficulty: https://en.bitcoin.it/wiki/Difficulty   
精通比特币 http://zhibimo.com/read/wang-miao/mastering-bitcoin/index.html    
 
> 本文遵照[CC-BY-NC-SA](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.zh)  协议规定，如果有侵犯到您的权益或者有其他意见想法，请及时联系我.欢迎遵照[CC-BY-NC-SA](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.zh) 协议规定转载.
