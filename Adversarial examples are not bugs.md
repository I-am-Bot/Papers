### Adversarial Examples Are Not Bugs, They Are Features
2.The Robust Features Model
定义模型

Standard Training
训练一个分类器，loss function -》特征加权求和和标签之间的相关性。
对于这个分类器的训练过程来讲，鲁棒不鲁棒不重要，只能区分出是否useful。任意的p - useful feature都会被


3 找出鲁棒（和非鲁棒）特征

核心假设：鲁棒和非鲁棒特征对于standard training都有效。
支撑假设的实验：区分两种特征

1）建立一个鲁棒dataset，训练鲁棒模型。展示了去除一些特征可以提高模型的鲁棒性。更多的，提供了更多的证据证明非鲁棒特征才是对抗脆弱性的原因，而非模型的固有特征。
2）建立了新训练集，使得输出只和非鲁棒特征相关。足以训练出使得standard testset有较好的表现的模型。
这展示出在模型模型用非鲁棒特征来做预测。

3.1 如何建立模型区分鲁棒特征和非鲁棒特征

Motivation: 如果我们能确定只有鲁棒特征有用，standard training就应该训练出鲁棒的分类器。
但是不能操纵高纬度的特征。
Goal: 搞了一个模型来修改dataset，使数据集只含有和模型相关的特征。

How to achieve：给出一个鲁棒模型C，我们建立一个分布Dr，使得其满足：


Result:

3.2非鲁棒特征足够分类
Motivation: 试图证明只在非鲁棒特征上训练的分类器也可以在标准测试集上有高正确率。

Goal: 搞了一个全是非鲁棒特征的dataset(ρ-useful and non-robust.)

How to achieve this: 

两类非鲁棒数据集：



在这两类训练集上做standard training。
Result: 训练出的分类器对原始测试集的效果都较高。

3.3 非鲁棒特征的可移植性
Motivation: Intriguing properties: transfer across models with different architectures and independently sampled training sets.
非鲁棒特征存在下的自然结果：
这些特征是数据分布中固有的，所以不同的分类器可能使用了同一部分非鲁棒特征。 因此，某个分类器学出来的非鲁棒特征所构成的对抗样本可以transfer到不同的用相似特征的分类器。

How to corroborate this hypothesis:
用ResNet-50训练出的adv-example with deterministic labels 放到五个不同结构的分类器。