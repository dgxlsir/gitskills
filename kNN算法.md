# kNN算法初探

k-近邻算法：

优点：无数据输入假定，运算精度高，异常值不敏感；

缺点：计算复杂度和空间复杂度高；

适用范围：数值型和标称型；

伪代码：对未知类别属性的数据集中的每个点执行以下操作，

1）计算已知类别数据集中的点与当前点之间的距离；

2）按照距离递增次序排序；

3）选取与当前距离最小的k个点；

4）确定前k个点所在类别的出现频率；

5）返回前k个点出现频率最高的类别作为当前点的预测分类；

k-近邻算法的python代码参考：

```
def classify0(inX, dataSet, labels, k):
	dataSetSize = dataSet.Shape[0]
	diffMat = tile(inX, (dataSetSize, 1)) - dataSet
	sqDiffMat = diffMat2 ** 2
	aqDistances = sqDiffMat.sum(axis=1)
	distances = sqDistances ** 0.5
	sortedDistIndicies = distances.argsort()
	#距离计算
	classCount={}
	for i in range(k):
		voteIlabel = labels[sortedDistIndicies[i]]
		classCount[voteIlabel] = classCount.get(voteIlabel, 0) + 1
		#选择距离最小的k个点
	sortedClassCount = sorte(classCount.iteritems(),
	key = operator.itemgetter(1), reverse=True)
	#排序
	return sortedClassCount[0][0]
```

从文本文件中解析数据

```
def file2matrix(filename):
	fr = open(filename)
	arrayOLines = fr.readlines()
	numberOfLines = len(arrayOLines)
	returnMat = zeros((numberOLines,3))
	#得到文件行数
	classLabelVector = []
	#创建返回的numpy矩阵
	index = 0
	for line in arrayOLines:
		line = line.strip()
		listFromLine = line.split('\t')
		returnMat[index,:] = listFromLine[0:3]
		#解析文件数据到列表
		classLabelVector.append(int(listFromLine[-1]))
		index += 1;
	return returnMat,classLabelVector
```

