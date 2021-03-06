### 模型验证

> 重复唠叨听到的，并不意味着你已经学到了什么。

模型验证是构造任何模型的核心步骤。它能够说明“预测与观测数据之间的符合程度”问题。如果没有足够多的数据，模型无法做到精准，但是如果有太多的数据，又可能让模型局限在数据中。如果模型训练时太过注重数据的细节，会无法做到对训练数据外的场景进行准确预测，这叫做模型过度拟合。

已存在许多技术能够解决模型过度拟合问题。最简单的一种是将你的数据集分成训练集、测试集和验证集。训练数据用于构建模型，模型构建完后去估计测试数据，估计的结果用于降低模型误差。这样其实就是间接地在模型构建使用测试数据去降低模型过度拟合可能性。最后，用模型在验证数据的估计结果去评价其普适性。

训练数据用于构建模型，模型构建完后去估计测试数据，估计的结果用于降低模型误差。这样其实就是间接地在模型构建使用测试数据去降低模型过度拟合可能性。最后，用模型在验证数据的估计结果去评价其普适性。另外有一些方法是将数据只分成训练集和测试集，例如：k-fold cross-validation（k折交叉验证），Leave-One-Out cross validation（弃一法交叉验证），bootstrap（引导）法和resampling（重抽样）法。其中，Leave-One-Out cross-validation 方法通常能让模型得到比较理想的表现。操作步骤如下：在训练集中抽样出一部分数据作为测试集，其余数据作为训练集，模型在测试集中预测出现的误差会保存下来，然后再进行下一轮的抽样，训练，测试，不断循环一直到数据集中的所有数据都被抽样过，最后计算平均误差作为模型的误差。 

还有其它的方法用于评估你的假设和数据之间的相关性。统计学方法中通常是去计算决定系数，通常也被称作R平方值，用于确定你模型所预测的数据的准确性。

值得注意的是，随着你特征空间中维度增多，R平方值也会增加。校正后R平方值能通过对模型复杂度进行惩罚而补偿这种现象。当校验整个回归结果时，用解释方差除以非解释方差获得F校验值。如果一个回归结果有很高的F统计值和大于0.7的校正后R平方值。