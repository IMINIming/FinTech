# FinTech数据组
一、题目要求  
>本次大赛为参赛选手提供了两个数据集（训练数据集和评分数据集），包含用户标签数据、过去60天的交易行为数据、过去30天的APP行为数据。
希望参赛选手基于训练数据集，通过有效的特征提取，构建信用违约预测模型，并将模型应用在评分数据集上，输出评分数据集中每个用户的违约概率。  

二、评价标准  
>本次比赛使用AUC作为评价标准。  

三、数据说明  
>1.训练数据集_tag.csv，评分数据集_tag.csv提供了训练数据集和评分数据集的用户标签数据；  
>2.训练数据集_trd.csv，评分数据集_trd.csv提供了训练数据集和评分数据集的用户60天交易行为数据；  
>3.训练数据集_beh.csv，评分数据集_ beh.csv提供了训练数据集和评分数据集的用户30天APP行为数据；  
>4.数据说明.xlsx文件是数据集字段说明和数据示例；  
>5.提交样例：  
>>5.1采⽤UTF-8⽆BOM编码的txt⽂件提交，⼀共提交⼀份txt⽂件。  
>>5.2输出评分数据集中每个用户违约的预测概率，输出字段为：用户标识和违约预测概率，用\t分割，每个用户的预测结果为一行，注意不能有遗漏的数据或多出的数据。


四、数据处理(代码见code.ipynb)  
>1、训练数据集的处理  
>>这里是用到的是用户标签数据，包括缺失值的处理、数据的标准化和类别数据的one-hot编码。缺失值的处理我这里用的是以0值填充，实际上，通常遇到缺失值，
我了解到的会有处理方法有：1、如果缺值的样本占总数比例极高，可能就直接舍弃了，作为特征加入的话，可能反倒带入noise，影响最后的结果；2、如果缺值的
样本适中，而该属性非连续值特征属性(例如表示类别的特征)，那就把缺失值作为一个新类别，加到类别特征中；3、如果缺值的样本适中，而该属性为连续值特征
属性，有时候我们会考虑给定一个step，然后把它离散化，之后把缺失值作为一个type加到属性类目中；4、有些情况下，缺失的值个数并不是特别多，这时可以试
着根据已有的值，使用回归、决策树等工具拟合一下数据，这种方法比较可靠，也是最流行的处理方法。数据的标准化的处理我这里用的是均值归一化法，对于数据
标准化，我了解到的常见方法有：1、Min-Max标准化；2、Z-Score标准化；3、小数定标（Decimal scaling）标准化；4、均值归一化法；5、向量归一化法；6、
指数转化法。数据标准化的好处有：加快模型的收敛速度、提高模型的精度。对于逻辑回归建模时，需要输入的特征都是数值型特征，通常会先对类别型的特征因子
化进行one-hot编码。  

>2、预测数据集的处理  
>>与上面训练数据集的处理类似  

>3、模型的选择、训练与预测
>>在这次比赛中，我尝试了LR（逻辑斯蒂回归）模型、GBDT（梯度提升决策树）模型、GBDT+LR模型融合、XGBoost模型和Lightgbm模型，在实验和调参的过程中，
LR模型比后者的效果会差很多，GBDT的结果会比LR有所提升，GBDT+LR融合后的结果比GBDT差一点，这个可能要根据实践的业务场景，一般在模型融合后结果会好
些，可能跟我特征工程好坏有点关系，XGBoost模型和Lightgbm模型的结果是其中最好的，Lightgbm模型给我的最大感受是比XGBoost快很多，结果也很好。
