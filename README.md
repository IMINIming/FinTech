# FinTech数据组
一、题目要求
  本次大赛为参赛选手提供了两个数据集（训练数据集和评分数据集），包含用户标签数据、过去60天的交易行为数据、过去30天的APP行为数据。
希望参赛选手基于训练数据集，通过有效的特征提取，构建信用违约预测模型，并将模型应用在评分数据集上，输出评分数据集中每个用户的违约概率。
二、评价标准
  本次比赛使用AUC作为评价标准。
三、数据说明
  1.训练数据集_tag.csv，评分数据集_tag.csv提供了训练数据集和评分数据集的用户标签数据；
  2.训练数据集_trd.csv，评分数据集_trd.csv提供了训练数据集和评分数据集的用户60天交易行为数据；
  3.训练数据集_beh.csv，评分数据集_ beh.csv提供了训练数据集和评分数据集的用户30天APP行为数据；
  4.数据说明.xlsx文件是数据集字段说明和数据示例；
  5.提交样例：
    5.1采⽤UTF-8⽆BOM编码的txt⽂件提交，⼀共提交⼀份txt⽂件。
    5.2输出评分数据集中每个用户违约的预测概率，输出字段为：用户标识和违约预测概率，用\t分割，每个用户的预测结果为一行，注意不能有遗漏的数据或多出的数据。
