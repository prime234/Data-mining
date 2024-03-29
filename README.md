# Data-mining
## BulletTrajectory
### 场景：
  现有一子弹由不同仪器测量，得到多个数据表，数据表字段有 T	x	y	z	Vx	Vy	Vz	V	Ax	Ay	Az	A 代表的含义是：时间，子弹在某时刻三维空间不同坐标位置，不同方向上的速度、速度、三维轴上的加速度，子弹加速度。现在需据某算法建立出拟合函数，从三个维度：速度、加速度、位移三个方向输出其与拟合的子弹运行轨迹数据的偏差，并将其新建三列输出至原始数据表里。
### 算法设计：  
1. 加权平均法
* 读取所有数据表，并将其存储为 Pandas DataFrame 的形式。
* 对于每个数据表，计算每个子弹的平均速度和平均加速度。这可以通过计算每个子弹所有时间点上的速度和加速度的平均值来完成。
* 将每个子弹的平均速度和平均加速度作为该仪器的性能评估指标。对于每个仪器，计算所有子弹的平均速度和平均加速度的平均值，作为该仪器的总体性能评估指标。
* 选择具有最高总体性能评估指标的仪器作为最优仪器。
2. 算法  
* 数据预处理：将每个数据表中的数据合并成一个大的数据集，并根据时间戳进行排序。
* 特征提取：使用统计学和机器学习方法提取每个数据点的特征，例如平均速度、加速度、位置等。
* 模型选择：选择一个适当的模型，该模型可以根据**提取的特征来预测子弹运动轨迹**。可以尝试不同的模型，如决策树、随机森林、神经网络等，并根据交叉验证或其他方法来评估模型的性能。
* 参数优化：根据模型选择的结果，对模型进行参数调整和优化，以提高模型的准确性和泛化能力。
* 最优仪器选择：使用训练好的模型来预测每个数据点的子弹运动轨迹，并根据预测结果来确定最优的仪器。
* 遍历每个数据表，根据预测误差来确定最优的仪器。在循环中，首先读取数据表，然后对数据表进行特征提取。接下来，将特征作为输入数据，使用训练好的模型来预测每个数据点的子弹运动轨迹。最后，我们计算预测结果与实际值之间的均方根误差（RMSE），并将其与之前的最小误差进行比较。如果当前误差更小，则将当前仪器设为最优仪器。
### 实现
* 应用多项式回归和高斯过程回归两种算法进行数据拟合
* 使用网格搜索自动搜索两种模型的最优超参数组合
* 定义多项式回归的degree和高斯过程回归的length scale与noise level作为超参数
* 通过交叉验证选择得分最高的超参数组合
* 比较不同模型对同一数据的拟合效果
* 根据MSE指标选择保存拟合效果更好的一种模型
* 绘制原数据和预测数据的散点图,直观比较不同模型的拟合效果
* 散点图通过不同颜色和图例对数据进行可视化区分
* 散点图上的拟合曲线有助于选择拟合效果更好的模型
