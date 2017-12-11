# 漫谈区块链技术

![whatsblockchain](https://github.com/ocaku/blockchain/blob/master/whatsblockchain.jpeg)

## 区块链架构

![architecture](https://github.com/ocaku/blockchain/blob/master/architecture.jpg)

### 一 数据层

![block](https://github.com/ocaku/blockchain/blob/master/block.jpg)

 * 一种由有限制容量的数据块和时间戳组成的链表结构数据.是整个区块链中底层的数据存储
 * 其中包括了时间戳,非对称加密,hash算法等技术.时间戳造就了历史数据可回放性。
 * 操作特点: 随机访问和append,杜绝修改 链上信息内容“不可篡改”，一旦一个数据块变化了，会导致之后的所有数据块的变化。
 * 狭义上的区块链，是一种组织数据的结构  
 * 存的数据来源于合约层。

 ##### 规则
 * 1.最新的block的block header中必须明确指出前一个block是哪一个；
 * 2.出现分支链时只取最长链；
 * 3.分支长度相同时，只收录难度值最高的block。
 
### 二 网络层
 * P2P组网机制，区块链具有自动组网功能 
 * 分布式组网机制
 * 数据传播机制
 * 数据验证机制

### 三 共识机制
 * 分布式节点的共识机制.
 * 主要有封装了网络节点的共识机制算法,决定了主权分配问题,有谁来写入数据层.影响到可靠性和安全性.   
 * 共识算法:  
    * 工作量证明机制（PoW，Proof of Work）
    * 权益证明机制（PoS，Proof ofStake）
    * 股份授权证明机制（DPoS，Delegated ProofofStake）

### 四 激励层
 * 公链的一种博弈竞争机制(发行机制/分配机制).让更多的服务节点愿意处理数据。
 * 矿机们处理完信息之后会得到奖励.  (极端情况有的矿机永远拿不到,矿池解决这个问题) 

### 五 合约层   
 * 封装各类脚本、算法和智能合约，是区块链可编程特性的基础.
 * 智能合约 目前做法类似于jvm .已经具备编成语言的特性 ETH.  广播路由算法 . ETH 的智能合约目前是有问题的，不要轻易的拿ETH跑测试.测出问题了封账号(分叉解决)
 * 理论上可以编写实现任何功能的应用。


### 六 应用层
 * 封装了区块链的应用场景和案例 
 * 块数据中可编程货币，可编程金融,可编程社会 也将会搭建在应用层


### 总结
 * 数据层、网络层和共识层是构建区块链应用的必要因素，否则将不能称之为真正意义上的广义区块链
 * 而激励层、合约层和应用层则不是每个区块链应用的必要因素


## 扩展 

#####  数据  
* 数据存储 云存储/分布式存储代替所有节点存储数据 如 Metadisk云存储 
* 数据检索 
    存储信息日益膨胀使得“读”效率会逐步降低，中心化的检索/区块链本身复合检索功能，唯链Vechain采用后一种   
* 数据隐秘性    
    需要实现 部分公开/部分不公开 ,区块链并非是匿名的而是非实名制的   

##### 去中心化 
![nocenter](https://github.com/ocaku/blockchain/blob/master/nocenter.png)
 * 去中心化原因：1，高可用 2，容错力3，抗攻击力 4,防勾结串通,共识机制
 * 区块链是分布式系统，弱中心化服务，运行的方式比分布式网络所实现的更类似于一个去中心化网络运行的方式
 * 区块链的诞生是为了去中心化，但是不去中心化也是可以应用区块链技术的

##### 发展方向
 * 跨链技术 
    实现各种区块链的互通/流通，兑换.
 * 侧链 
    * 1,意味着比特币不仅可以在比特币区块链上流通，还可以在其他区块链上流通，其应用范围和应用前景会更加广泛；有创意的人们会研发出各种各样的应用以侧链协议与比特币主链对接，使得比特币这种基准自由货币的地位越牢固。     
    * 2,侧链（sidechains）实质上不是特指某个区块链，而是指遵守侧链协议的所有区块链，该名词是相对与主链来说的。侧链协议是指：可以安全地从主链转移到其他区块链，又可以从其他区块链安全地返回主链的一种协议。

 * 智能合约 
  1,规则引擎drools 2,虚拟机 EVM(以太坊虚拟机)

### 篇外  

##### BTC base
 * 2009年诞生 直到2140年达到2100万个的总量上限。（代码里写死的）此后，奖励机制不再产生新的比特币，而是用每笔交易抽取1%比特币的手续费形式维持系统运转。
 * 实际是20999999.97690000个
 * 10分钟一个block,之前是1M,现在是2M.
 * 闪电网络：类似于数据缓存,快速交易,减少真正到数据层的交易

##### 源代码
 * fabric https://github.com/hyperledger/fabric golang
 * chain http://github.com/chain/chain golang
 * pyethapp  https://github.com/ethereum/pyethapp python
 * Ebookcoin  https://github.com/Ebookcoin nodejs
 * BTC https://github.com/bitcoin C++
 * ETH https://github.com/ethereum golang
 * Elements https://github.com/ElementsProject/elements C++
 * BitShares http://github.com/bitshares C++
 * Factom https://github.com/FactomProject/FactomCode golang   
 * Ripple https://github.com/ripple/rippled C++   
 * Nxt https://bitbucket.org/JeanLucPicard/nxt/overview JAVA
 * Sawtooth Lake https://github.com/intelledger   Python
 * 小蚁区块链 https://github.com/antshares/antshares C#
 * Tendermint https://github.com/tendermint/tendermint golang
 * ASCH https://github.com/AschPlatform/asch js
 * Parity https://github.com/paritytech/parity rust


##### 参考连接   
https://www.zhihu.com/question/27256432   
https://www.cnblogs.com/loveling-0239/p/7028343.html   
精通比特币 http://zhibimo.com/read/wang-miao/mastering-bitcoin/index.html   
图片来源以百度图片  
 
> 本文遵照[CC-BY-NC-SA](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.zh)  协议规定，如果有侵犯到您的权益或者有其他意见想法，请及时联系我.欢迎遵照[CC-BY-NC-SA](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.zh) 协议规定转载.
