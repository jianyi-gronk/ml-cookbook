- 主要是用来介绍人工智能的核心步骤，是以 kaggle 实践为例，整个学习笔记也是围绕着这个展开

## 1. 数据预处理

- 可能存在的问题
  - **数据质量决定模型上限**，噪音，缺失值，格式混乱（ 多时区时间戳 ）等问题都会导致模型偏差
  - **原始数据可能不符合模型的输入要求**，比如 部分决策树模型要求分类编码，神经网络要求数值型 等
  - **不规整的数据会导致梯度下降收敛速度降低**，影响训练速度，当特征尺度差异较大时（ 如特征 A 取值 0-1，特征 B 取值 1000-10000 ），损失函数等高线会呈现狭长椭圆形，这种导致：
    - 梯度方向偏移：实际最优方向与梯度方向形成夹角
    - 震荡路径：梯度下降在陡峭维度频繁震荡
    - 迭代次数倍增：需要更多"之"字形路径才能到达最低点
- 数据预处理主要分五个步骤：
  - **数据清洗**
    - 核心是将不符合预期的数据进行处理
  - **数据扩充**
    - 核心利用当前数据集，创造新的数据集，解决数据集过小的场景
  - **数据转换**
    - 核心是将数据转换成更适合模型输入的类型
  - **特征工程**
    - 核心是在特征数量少，或者特征信息量不足的情况，进行特征构造；在冗余特征多的情况，进行特征选择
  - **数据分割**
    - 核心是将原始数据划分为独立的 训练集，验证集 和 测试集

## 2.  模型训练

- 因为不同算法的参数和训练过程差距大，所以不细说
- 之后会更新模型选择，目前了解不多，暂留个坑

## 3. 模型调优

- **模型评估**
  - 评估方法：交叉验证
  - 评估指标
    - 分类：准确率、F1-score、AUC-ROC 等
    - 回归：R²、MAE、RMSE 等
- **超参数优化**
  - 网格搜索，随机搜索，贝叶斯优化，TPE 等
- **模型集成**
  - 当单个模型 CV 分数达到排行榜 80%-90% 分位时，再继续优化单模型的边际收益会显著下降，可以开始构建集成
  - 集成的模型最好得分不要太低，且之间关联性最好较弱
  - 常见方法：Voting/Averaging，Bagging，Boosting，Stacking 和 Blending
