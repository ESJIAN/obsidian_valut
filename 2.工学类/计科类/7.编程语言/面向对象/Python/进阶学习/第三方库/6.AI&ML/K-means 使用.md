- [手把手教你用Python玩转K-means聚类（附踩坑指南）-CSDN博客](https://blog.csdn.net/binbinaijishu88/article/details/147653535)


### 一、先来点刺激的——聚类到底有多猛？

各位老铁们！（敲黑板）今天咱们要搞的这个[K-means算法](https://so.csdn.net/so/search?q=K-means%E7%AE%97%E6%B3%95&spm=1001.2101.3001.7020)，那可是数据挖掘界的扛把子！不知道你们有没有遇到过这些场景：

- 电商平台要给用户打标签（土豪/佛系/羊毛党）
- 城市交通要划分拥堵区域
- 甚至你手机相册的自动分类功能…

这些看似高大上的操作，背后可能都在用我们今天要讲的这个算法！而且最骚的是——用Python实现只要不到20行代码！（后面有代码实操，别急）

### 二、算法原理大揭秘（小学生都能懂版）

#### 2.1 核心思想三步走

1. 随机选K个点当老大（专业点叫初始质心）
2. 小弟们找最近的老大站队（计算距离）
3. 老大重新选位置（更新质心）

重复2-3步直到老大们不挪窝了（收敛）为止。是不是比[微积分](https://so.csdn.net/so/search?q=%E5%BE%AE%E7%A7%AF%E5%88%86&spm=1001.2101.3001.7020)简单多了？！

#### 2.2 举个栗子🌰

假设我们要给学校里的学生分群：

原始数据：

- 张三：身高175，月消费2000
- 李四：身高160，月消费800
- 王五：身高180，月消费5000
- …

通过K-means可能会得到：

1. 高消费高个子群体（富二代）
2. 中等消费群体（普通学生）
3. 低消费群体（节俭党）

（注意：这里只是示例，实际业务场景要复杂得多！）

### 三、代码实战环节（手别抖）

#### 3.1 环境准备

```python
# 必备三件套
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
```

#### 3.2 造点假数据（方便可视化）

```python
# 生成500个二维数据点
np.random.seed(666)  # 固定随机种子方便复现
data = np.concatenate([
    np.random.normal(loc=[0,0], scale=0.5, size=(150,2)),
    np.random.normal(loc=[5,5], scale=1, size=(250,2)),
    np.random.normal(loc=[-5,5], scale=0.8, size=(100,2))
])

# 画个散点图看看
plt.scatter(data[:,0], data[:,1], s=10)
plt.title("原始数据分布")
plt.show()
```

#### 3.3 关键代码实现

```python
# 创建模型（K=3）
kmeans = KMeans(
    n_clusters=3, 
    init='k-means++',  # 比random更聪明的初始化方式
    max_iter=300,      # 最大迭代次数
    tol=1e-04          # 收敛阈值
)

# 训练模型（注意这里没有y！是无监督学习）
kmeans.fit(data)

# 查看结果
print("质心坐标：\n", kmeans.cluster_centers_)
print("样本所属簇：", kmeans.labels_[:10])  # 查看前10个样本的类别
```

#### 3.4 可视化结果

```python
# 设置画布
plt.figure(figsize=(10,6))

# 绘制散点图
colors = ['red', 'blue', 'green']
for i in range(3):
    plt.scatter(
        data[kmeans.labels_==i, 0], 
        data[kmeans.labels_==i, 1],
        s=20, 
        c=colors[i],
        label=f'Cluster {i+1}'
    )

# 绘制质心
plt.scatter(
    kmeans.cluster_centers_[:,0],
    kmeans.cluster_centers_[:,1],
    s=200, 
    marker='*',
    c='black',
    label='Centroids'
)

plt.title("聚类结果可视化")
plt.legend()
plt.show()
```


### 3.5. 完整代码

```python
# 必备三件套
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# 生成500个二维数据点
np.random.seed(666)  # 固定随机种子方便复现
data = np.concatenate([
    np.random.normal(loc=[0,0], scale=0.5, size=(150,2)),
    np.random.normal(loc=[5,5], scale=1, size=(250,2)),
    np.random.normal(loc=[-5,5], scale=0.8, size=(100,2))
])

# 画个散点图看看
plt.scatter(data[:,0], data[:,1], s=10)
plt.title("原始数据分布")
plt.show()

# 创建模型（K=3）
kmeans = KMeans(
    n_clusters=3, 
    init='k-means++',  # 比random更聪明的初始化方式
    max_iter=300,      # 最大迭代次数
    tol=1e-04          # 收敛阈值
)

# 训练模型（注意这里没有y！是无监督学习）
kmeans.fit(data)

# 查看结果
print("质心坐标：\n", kmeans.cluster_centers_)
print("样本所属簇：", kmeans.labels_[:10])  # 查看前10个样本的类别

# 设置画布
plt.figure(figsize=(10,6))

# 绘制散点图
colors = ['red', 'blue', 'green']
for i in range(3):
    plt.scatter(
        data[kmeans.labels_==i, 0], 
        data[kmeans.labels_==i, 1],
        s=20, 
        c=colors[i],
        label=f'Cluster {i+1}'
    )

# 绘制质心
plt.scatter(
    kmeans.cluster_centers_[:,0],
    kmeans.cluster_centers_[:,1],
    s=200, 
    marker='*',
    c='black',
    label='Centroids'
)

plt.title("聚类结果可视化")
plt.legend()
plt.show()

```




### 四、避坑指南（血泪教训）

#### 4.1 K值怎么选？（灵魂拷问）

- 肘部法则（Elbow Method）：看SSE（误差平方和）的变化
- 轮廓系数（Silhouette Score）：-1到1，越大越好
- 业务需求：比如服装店可能要分S/M/L/XL四类

```python
# 肘部法则示例
sse = []
for k in range(1, 11):
    km = KMeans(n_clusters=k)
    km.fit(data)
    sse.append(km.inertia_)

plt.plot(range(1,11), sse, marker='o')
plt.xlabel('K值')
plt.ylabel('SSE')
plt.show()
```

#### 4.2 数据预处理三大铁律

1. 特征缩放必须做！（MinMaxScaler或StandardScaler）
2. 离群值处理要谨慎（可能包含重要信息）
3. 高维数据考虑降维（PCA/t-SNE）

#### 4.3 常见报错处理

- **收敛警告**：加大max_iter或调高tol值
- **内存不足**：改用MiniBatchKMeans
- **空簇问题**：换初始化方式或调整K值

### 五、进阶玩法（装逼必备）

#### 5.1 图片压缩实战

```python
from sklearn.datasets import load_sample_image

# 加载示例图片
china = load_sample_image("china.jpg")
image_array = china / 255.0  # 归一化

# 重塑为二维数组（像素点集合）
X = image_array.reshape(-1, 3)

# 用K-means压缩颜色
kmeans = KMeans(n_clusters=32)
kmeans.fit(X)

# 重建图片
compressed_image = kmeans.cluster_centers_[kmeans.labels_]
compressed_image = compressed_image.reshape(image_array.shape)

# 对比显示
fig, ax = plt.subplots(1,2, figsize=(12,6))
ax[0].imshow(china)
ax[0].set_title('原始图片')
ax[1].imshow(compressed_image)
ax[1].set_title('32色压缩版')
plt.show()
```

#### 5.2 文本聚类套路

虽然K-means主要处理数值数据，但结合TF-IDF可以玩文本聚类：

```python
from sklearn.feature_extraction.text import TfidfVectorizer

documents = ["苹果发布新手机", 
            "华为推出5G芯片",
            "肯德基新品汉堡上市",
            "麦当劳优惠券发放"]

# 文本向量化
tfidf = TfidfVectorizer()
X = tfidf.fit_transform(documents)

# 聚类操作
kmeans = KMeans(n_clusters=2)
kmeans.fit(X)

# 查看结果
for doc, label in zip(documents, kmeans.labels_):
    print(f"「{doc}」=> 类别{label}")
```

### 六、总结与思考

K-means虽好，但也要注意它的局限性：

- 对初始质心敏感（可以多跑几次取最优）
- 只能发现球型簇（对复杂形状跪了）
- 需要预先指定K值（这是硬伤）

在实际项目中，我经常把它作为baseline，快速验证数据是否具有可分性。最近在一个用户分群项目里，配合RFM模型使用，成功把用户分成8个高价值群体，转化率提升了37%！（当然中间调参调到头秃）

最后给新人一个忠告：不要沉迷调参！特征工程才是王道！数据质量决定天花板，算法只是逼近这个天花板的方法而已。