## 飞桨学习赛：英雄联盟大师预测2023年2月85.345分方案
### 比赛链接 - [飞桨学习赛：英雄联盟大师预测](https://aistudio.baidu.com/aistudio/competition/detail/247/0/introduction)
### 赛题介绍

本赛题属于典型的分类问题，以英雄联盟手游为背景，要求选手根据英雄联盟玩家的实时游戏数据，预测玩家在本局游戏中的输赢情况。

### 数据说明

数据集中每一行为一个玩家的游戏数据，数据字段如下所示：

- id：玩家记录id
- win：是否胜利，标签变量
- kills：击杀次数
- deaths：死亡次数
- assists：助攻次数
- largestkillingspree：最大 killing spree（游戏术语，意味大杀特杀。当你连续杀死三个对方英雄而中途没有死亡时）
- largestmultikill：最大mult ikill（游戏术语，短时间内多重击杀）
- longesttimespentliving：最长存活时间
- doublekills：doublekills次数
- triplekills：doublekills次数
- quadrakills：quadrakills次数
- pentakills：pentakills次数
- totdmgdealt：总伤害
- magicdmgdealt：魔法伤害
- physicaldmgdealt：物理伤害
- truedmgdealt：真实伤害
- largestcrit：最大暴击伤害
- totdmgtochamp：对对方玩家的伤害
- magicdmgtochamp：对对方玩家的魔法伤害
- physdmgtochamp：对对方玩家的物理伤害
- truedmgtochamp：对对方玩家的真实伤害
- totheal：治疗量
- totunitshealed：痊愈的总单位
- dmgtoturrets：对炮塔的伤害
- timecc：法控时间
- totdmgtaken：承受的伤害
- magicdmgtaken：承受的魔法伤害
- physdmgtaken：承受的物理伤害
- truedmgtaken：承受的真实伤害
- wardsplaced：侦查守卫放置次数
- wardskilled：侦查守卫摧毁次数
- firstblood：是否为firstblood

测试集中label字段win为空，需要选手预测。

### 比赛难点

本次比赛难点主要在于数据处理和模型选择上

- 比赛数据既没有缺失值也没有特别明显的异常值，数据分布比较正常，特征工程上找不到很多能增长准确率的地方
- 事实上就算不做任何数据处理直接用随机森例、LightGBM和xgboost模型都能够非常轻松的拿到82-84分神经网络模型也并不能够有很大程度的进步甚至不如树模型

### 项目亮点

- 采用遗传算法构造了更多特征并利用PCA算法进行特征降维

- 提前训练了几种数模型并利用`stacking`集成学习进一步提高准确率


### 代码仓库

https://github.com/ZhangzrJerry/paddle-lolmp

### 项目总结

事实上项目仍然有很多能够改进的地方

- 模型可以利用`Network-in-Network`进一步优化网络结构

- 尽管`180000`条样本可以一次性训练，修改训练批数仍有可能进步

- 项目并没有做明确的训练集/测试集划分，可以尝试采用交叉验证来减少过拟合