# 转化visit矩阵
transform_test 和 transform_train 分别把训练和测试的visit，转化为了一个矩阵，这个矩阵是一维的，代表第0天的0小时，第0天的1小时，或者第5天的6小时...有多少人访问，这个矩阵的维度可以后面再进行reshape，但是现在至少转化出来了。

# 数据集扩充
每个种类的图片均扩充至1万，共9万。验证集从中完全随机取样4500张，剩下的图片为训练集。
注意由于扩充时有些图片有重复，如果随机采样验证集采到了重复图片，那么训练集不会选择这些重复的图片，故得到的训练集个数会少于85500张，大概在72000张左右。

# 疑问
原本的想法是，首先对图片做一次筛选，将所有对比度低/全黑的图片筛选出来，不删除它们，但是在扩充数据集时保证不扩充这些图片。后讨论否定，理由是要保证它们是独立同分布。但是我依然对此有所疑问，因为观察数据集（不管是训练集还是最后的测试集）时发现有些图片故意设置成全黑色。。。我也不知道，后面会做实验看两种区别。