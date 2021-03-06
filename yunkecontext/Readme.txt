问题描述：

某 互联网公司收集了文章供用户阅读。经分析，有些文章很好，有些很差，该公司给每篇文章一个 unique ID，然后把好的文章标记为 +1，差的文章标记为 -1。该公司进一步分析出有 23 个文章特性有可能对文章的好坏有影响，比如文章的长度，文章作者的学历等等。

现有已知文章4000篇，它们的 ID，好坏(+1 或 -1)，还有 23个特性的数值在文件 data1.txt 里。格式如下：

MzMjg -1 1:5224625678 2:0.000000 3:1 4:0.693147 5:1.609438 6:0.000000 7:0.000000 8:0.000000 9:0 10:0 11:3.401197 12:2 13:1 14:0 15:0 16:0 17:0 18:1 19:0 20:6 21:2.197225 22:0.000000 23:0.000000

XtkZ8 +1 1:10201109606823 2:2.254881 3:1 4:3.737670 5:4.691348 6:95.000000 7:0.000000 8:0.000000 9:0 10:0 11:4.454347 12:1 13:1 14:0 15:0 16:1 17:1 18:1 19:0 20:3 21:2.079442 22:0.000000 23:0.000000

w4OPW +1 1:10366219380758 2:1.828315 3:0 4:2.079442 5:2.890372 6:0.000000 7:0.000000 8:0.000000 9:0 10:0 11:0.693147 12:0 13:0 14:0 15:0 16:0 17:0 18:1 19:0 20:2 21:1.945910 22:0.000000 23:0.000000

...

以上是三篇文章的数据，列之间用空格隔开，第一列为 ID，第二列为好坏的标记，用 +1 或 -1 表示，后面 23 列格式为：特性序号：特性数值。共 4000 行。

另有500篇文章未知好坏，它们的 ID 和 23 个文章特性在文件 data2.txt 里：

izyeQ 1:684194079394 2:0.000000 3:1 4:1.609438 5:3.637586 6:0.000000 7:2.567478 8:0.000000 9:0 10:0 11:4.605170 12:5 13:1 14:0 15:1 16:1 17:1 18:0 19:0 20:0 21:1.098612 22:0.000000 23:0.000000

83X7K 1:1772986376382 2:3.530621 3:1 4:3.332205 5:5.398163 6:0.000000 7:0.000000 8:0.000000 9:0 10:0 11:3.332205 12:2 13:1 14:0 15:1 16:0 17:1 18:1 19:0 20:3 21:3.295837 22:0.000000 23:0.000000

wDqjK 1:953303656 2:0.000000 3:1 4:0.000000 5:0.693147 6:0.000000 7:0.000000 8:0.000000 9:0 10:0 11:3.784190 12:3 13:1 14:0 15:0 16:0 17:0 18:0 19:0 20:42 21:5.068904 22:0.000000 23:0.000000

...

以上是三篇文章的数据，列之间用空格隔开，第一列为 ID，后面 23 列格式为：特性序号：特性数值。共 500 行。

我们的任务是根据已知好坏的4000篇文章，判断未知的500篇文章的好坏。具体要求见下。



程序限制：

1. 用任何可以免费取得编译器或解释器的语言，包括 Java, Python, C++, C#, Golang, JavaScript，等等。但 MatLab, LabView 等付费程序不可以。

2. 只提交预测程序，不提交其它程序（见下文，提交要求部分）

3. 只使用语言基本类库，不使用第三方类库。除基础编译器或解释器外，执行预测程序不应要求安装其它程序。



提交：

1. 按照 example_solution.txt 的格式，将预测结果写在一个新文件 'solution.txt' 中

2. 可执行程序，该程序从 stdin 读取 data2.txt，从 stdout 输出 solution.txt，禁止执行与本练习无关的操作。

3. Readme.txt. 首先详细描述如何编译和运行可执行程序。然后描述模型预测的原理，尽可能让具有初步数据挖掘知识的人能理解。最后描述你训练模型的过程，尽可能让其它机器学习工程师能重复你的工作。


我的解决方法：

python脚本文件编译运行方式：python 脚本名字

我不确定example_solution.txt中是正确结果，所以我的程序跑出的预测结果的正确率无法求出，我这里用了两种方法来进行预测。

因为这道题目的训练集不是很大，所以我考虑使用KNN算法，KNN算法的思想就是根据相邻的点的类别来推断自己的类别，相邻的k个点中哪一种类别的点最多就认为自己属于哪一种类别。附件中对应的脚本文件是ForestByKNN.py,用到了numpy、pandas库，预测结果保存在solutionByKNN.txt中,内容格式和example_solution.txt是一致的。

决策树模型对于这道题的效果也不错，决策树中关键点是信息熵的计算，即以哪种特征进行往下分，对应的脚本文件是ForestByDecisionTree.py，用到了sklearn、numpy和pandas库，预测结果保存在solutionByDecisionTree.txt中，内容格式和example_solution.txt是一致的。
