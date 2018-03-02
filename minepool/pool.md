挖矿三种方式:
1,POS机制,持有的权益越多,时间越长。每产生一个区块数据的奖励获得的越多。
2,POW机制 solo方式挖矿,单枪匹马挖矿,直接获取主链上交易信息,完成区块数据信息之后发到主链上等待主链确认,如果确认成功,就可以获取奖励。

3.POW机制 矿池挖矿。


矿池是分布式计算,中心化数据架构,节点(矿机)越多矿池的算力就越大。

btcpool 架构图 
https://raw.githubusercontent.com/btccom/btcpool/master/docs/btcpool.png


https://github.com/btccom/btcpool
https://github.com/zone117x/node-open-mining-portal  支持多币种挖矿
支持混合挖矿，源码地址https://github.com/sigwo/powerpool
https://github.com/p2pool/p2pool






矿池模式：PPLNS和PPS,DGM,P2Pool四种种模式
PPLNS :Pay Per Last N Shares缩写 被称为真正的组队挖矿，根据每个矿机贡献的股份数量来分配奖励,按劳分配本次总收益。矿池收益高分配的就多,矿池收益低分配的就少。(收入不稳定，追求高收入的)
PPS:Pay Per Share 缩写,类似于上班工作,上一月班,发一个月的工资,收益稳定并不是很高。按照算力在矿池算力的占比,分配奖励。无论矿池收益高低,矿工都可以收到固定奖励.为了解决PPLNS 收益忽高忽低的情况。
DGM:Double Geometric Method. 双几何制. 结合了 PPLNS 和几何奖励类型, 使得矿池运营者能规避一部分风险. 矿池运营者在短期内收取部分挖出的货币, 然后在之後以正规化过的值返还给矿工，像电容充放电, 运气好每 block 少给你点, 运气差多给你点。 
P2Pool:P2Pool的挖矿节点工作在类似比特币区块链的一种shares链上。由于没有中心，所以也不会受到DoS攻击。和其他现有的矿池技术都不一样---每个节点工作的区块，都包括支付给前期shares的所有者以及该节点自己的比特币。99%的奖励（50BTC+交易费用）会平均分给矿工，另外0.5%会奖励给生成区块的人。
