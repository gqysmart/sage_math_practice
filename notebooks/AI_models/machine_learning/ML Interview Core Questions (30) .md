ML Interview Core Questions (30) — Entry Level Cheat Sheet
Level 1 — Foundations
1. Linear regression vs Logistic regression

Linear：预测连续数值（房价），输出为实数

Logistic：分类问题，输出概率（0–1），再按阈值分类

2. Classification vs Regression

Regression：预测连续值

Classification：预测类别标签

3. Supervised vs Unsupervised

Supervised：有标签（x → y）

Unsupervised：无标签，发现结构（聚类、降维）

4. Train / Validation / Test

Train：训练模型参数

Validation：调参 / 选模型

Test：最终泛化能力评估

5. Bias vs Variance

Bias 高：模型太简单（欠拟合）

Variance 高：模型对数据太敏感（过拟合）

6. Underfitting vs Overfitting

Underfitting：train 表现差

Overfitting：train 好但 val/test 差

7. Cross Validation

数据少时更稳定评估模型

用于选模型 / 调超参

Level 2 — Model Behaviour
8. 为什么会 Overfitting

模型学到了噪声，泛化能力下降

9. 如何减少 Overfitting

更多数据

正则化

降低模型复杂度

early stopping

cross validation

10. Regularization 是什么

在 loss 中加入惩罚项，限制模型复杂度

11. L1 vs L2

L1：产生稀疏（特征选择）

L2：整体平滑，参数变小但不为0

12. 为什么要 feature scaling

防止大尺度特征主导模型

提升梯度下降稳定性

13. Normalization vs Standardization

Normalization：缩放到固定区间（0–1）

Standardization：均值0，方差1

Level 3 — Model Selection
14. 为什么不用 neural network

数据量小

可解释性差

成本高

简单模型足够

15. 什么时候用 Tree model

非线性强

表格数据

特征混合类型

16. 什么时候 Logistic regression 更好

数据量小

可解释性要求高

基线模型

17. 数据很小怎么办

简单模型

正则化

cross validation

特征工程

18. 类别不平衡怎么办

precision / recall / F1

重采样

class weight

调整 threshold

Level 4 — Evaluation
19. Accuracy vs Precision vs Recall

Accuracy：整体正确率

Precision：预测为正中真实正比例

Recall：真实正中预测出的比例

20. F1 score

precision 和 recall 的折中

21. ROC curve

TPR vs FPR 曲线

22. AUC

分类器区分能力

23. 为什么 accuracy 有时无效

类别极不平衡时误导性强

Level 5 — System Design (Mini Cases)
24. Spam classifier 设计

数据收集

文本特征

baseline 模型

precision/recall 评估

25. Recommendation system

用户行为数据

协同过滤

排序模型

A/B test

26. Anomaly detection

规则阈值

无监督模型

分类模型（有标签）

27. CV pipeline

数据 → 标注 → 训练 → 评估 → 部署

28. 数据噪声大

清洗

正则

增强

降复杂度

29. 特征太多

正则

特征选择

PCA

30. 模型上线后效果变差

数据漂移检测

回滚

重新训练

持续监控

使用方式（重要）

不要背答案，要练“口语解释”：

面试目标 = 能解释
不是背定义

练习方式：

每天选 5 题

自己口述回答

用工程语言表达

强调 tradeoff

下一步（最有效）

如果你愿意，我可以直接带你刷：

每天 5 题

模拟真实面试问法

我帮你把答案修成“工程表达版”

从最常考的 5 题开始：

bias vs variance

overfitting 怎么解决

logistic vs linear

precision vs recall

dataset split 为什么必要