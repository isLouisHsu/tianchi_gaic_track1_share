**大家好，我是来自华东理工大学的“单键”团队的单键丶，很荣幸能拿到本周的周周星。**

方案分享如下

- 模型结构选用nezha-cn-base，尝试使用nezha-cn-large，线下过拟合严重；
- 预训练MLM模型，参数重新初始化，试错调整默认mask参数，lr=5e-5, epochs=10，mlm损失最终0.17左右；
- 微调多标签分类模型，即`pooled_output`接MLP进行各标签二分类，采用二分类交叉熵作为损失函数；
- 随机划分五折交叉验证，线下单模型logloss=0.995左右，线上0.908左右，差距较大，五折融合后达到0.910左右；
- 线上线下数据差距较大，可以尝试不同的划分方法(当然也有可能是数据量不足的问题)；
- 调参！调参！调参！数据增强、对抗训练；
- EDA无效、添加tfidf特征无效。

最后，祝大家LB暴涨！
