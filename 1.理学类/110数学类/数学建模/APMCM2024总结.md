
**回顾：本次比赛选择C题，作为编程手参赛，此次C题目偏向于数据价值挖掘类，难点在于找数据和描述数据。但是对于没有接触过算法的你来讲还是有些难度**


## 问题

	前言：此次C题目主要难点在于数据收集，尽管借助AI工具减少了不少工作量，但是还是出现了一些问题
### 信息搜集
#### AI选择

**描述**：国内的AI在寻找国外的信息时候普遍命中率较差，对于Kimi仅有在深度搜索模式下才能够收集到相关信息。

**思考**：检索信息前，分析信息的类别，并且决定使用AI的类型。下图比对了GPT与Kimi在对于国外信息搜集上的区别

| Kimi                                                                          | GPT                                                                           |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| ![1732449615950.png](https://www.helloimg.com/i/2024/11/24/67431435e48a9.png) | ![1732449860113.png](https://www.helloimg.com/i/2024/11/24/6743152b1a0e8.png) |
| **信息少、逻辑不清晰**                                                                 | **信息全、逻辑清晰**                                                                  |

**总结**：
>1. **先定信息国籍**
>2. **再定信息领域**
>3. **决策使用工具**


链接：[[AI对比]]



#### 购买决策

**描述**：在此次比赛中我发现，我发现一些信息是公共平台上所难以找到的，基本属于一些私有信息。而传统AI工具是找不到这些信息的

**思考**：对于这类信息，其实还有另外一种获取信息的方式，在闲鱼上去收集信息。费用也要比在平台上直接购买要强。**即绕路思想**

**总结**：
>1.**不要过度依赖AI的信息检索能力，其检索信息成立的条件是必须得在公共平台上，对于一些垄断信息，难以找到**


|     |     |
| --- | --- |
|     |     |

### 信息标定




**描述**：在本次工作中，对于信息查找时发生了一个问题，表格寻找信息时候的定位难找，导致后续确认数据来源时候花费了更多的时间



						表：未标注信息来源的数据

| ![1732451068186.png](https://www.helloimg.com/i/2024/11/24/674319e21f2b0.png) |
| ----------------------------------------------------------------------------- |
| **工作簿上没有任何来源标记信息，后续查找定位耗时**                                                   |


						表：标注了信息来源的表

| ![1732451254716.png](https://www.helloimg.com/i/2024/11/24/67431a9de3bdb.png) |
| ----------------------------------------------------------------------------- |
| **添加了链接来源，但是链接过长，可以考虑缩短名称**                                                   |


**思考**：将一个xlsx文件的工作簿划分为两大类，一类给人看，一类给机器读写

|                                                                    给人看        |
| ----------------------------------------------------------------------------- |
| ![1732451573427.png](https://www.helloimg.com/i/2024/11/24/67431bd9ae7a8.png) |
| ![1732451596254.png](https://www.helloimg.com/i/2024/11/24/67431bf073778.png) |
| **特点**：1. 标注来源 2. 参数分类    **缺点**：程序无法直接利用                                     |

>**注意**：来源可以把超链属性赋予描述性的短文字上，相应数据列下贴相应来源链接

| 给机器看                                                                          |
| ----------------------------------------------------------------------------- |
| ![1732452236431.png](https://www.helloimg.com/i/2024/11/24/67431e70f15e0.png) |
| **特点**：1. 机器可读                                                                |

**总结**
>1. **一张表格文件，在头页记录的数据必须得分类，标注来源，且来源的链接得与相应的列保持对齐**
>2. 



### 度量单位

**描述**：由于度量单位不统一，造成论文写作单位不明确，写作出错的问题


| ![1732452588518.png](https://www.helloimg.com/i/2024/11/24/67431fd1d2014.png) | ![1732452653071.png](https://www.helloimg.com/i/2024/11/24/67432012b90e8.png) |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **以英镑为单位**                                                                    | **以人民币为单位**                                                                   |

**思考**：两表单位不统一对数据记录换算有很大的不变。**一旦涉及到有单位量的统计时，一定要转换度量单位**

**总结**
>**1.有单位量需规定统一量纲**





### 问题小节

>1.**不要过度依赖AI的信息检索能力，其检索信息成立的条件是必须得在公共平台上，对于一些垄断信息，难以找到**
>1. **一张表格文件，在头页记录的数据必须得分类，标注来源，且来源的链接得与相应的列保持对齐**
>1.**有单位量需规定统一量纲，减少建模手负担**





## 继承

### 分工明确

	引言：得益于此次分工明确，论文没有像国赛那次一样没有写完



### 检查精神


## 新知

### 变量预测

	引言：之前对变量预测一直没有概念，在本次比赛后有了初步概念

**主要步骤**
	1. **缺失值处理**
	2. **Z-core标准化——去量纲影响**
	3. **关联性分析**、
	4. **变量预测——预测手法多样**

>**说明**：第四步预测方法有很多，有微分方程预测法、随机森林预测法则。微分方程的预测法则


```python
import numpy as np

import pandas as pd

from scipy.optimize import curve_fit

import matplotlib.pyplot as plt

import seaborn as sns

from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

from sklearn.linear_model import LinearRegression

  

# 读取数据

df = pd.read_excel(r"代码\亚太杯\Question4\DataCode\Problem4.xlsx", sheet_name='Sheet2')

  
  
  
  

# 提取时间序列数据

t = df['Year'].values  # 假设有一个时间列

C_domestic = df['Domestic Pet Food Scale(100 billion)'].values

C_oversea = df['Global Pet Fodd Scale(100 billion)'].values

P_domestic = df['Domestic Produce(100 billion)'].values

T_domestic = df['Domesitc pet food export tax'].values

T_oversea1 = df['Europe pet food export tax'].values

T_oversea2 = df['American Pet Food Tax'].values

P_t = df['Export(100 billion)'].values  # 目标变量

  

# 打印 P_t 的前几个值

print(f"P_t 的前几个值: {P_t[:5]}")

  
  
  
  
  
  
  
  

data = {

    'Domestic Pet Food Scale': C_domestic,

    'Global Pet Fodd Scale': C_oversea,

    'Domestic Produce': P_domestic,

    'Domesitc pet food export tax': T_domestic,

    'European Pet Food Tax': T_oversea1,

    'American Pet Food Tax': T_oversea2,

    'Export': P_t

}

  

df_data = pd.DataFrame(data)

  

correlation_matrix = df_data.corr()

print(correlation_matrix)

  

# 设置中文字体
# Notice：此步很重要，否则导致无法显示中文
plt.rcParams['font.sans-serif'] = ['SimHei']  # 使用黑体

plt.rcParams['axes.unicode_minus'] = False    # 正常显示负号

  

# 绘制热力图

plt.figure(figsize=(10, 8))

sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')

plt.xticks(rotation=45)

  

plt.show()

  

# 定义离散化的微分方程

def model(t, K1, K2, K3, K4, K5, C_domestic, C_oversea, P_domestic, T_domestic, T_oversea2):

    dt = t[1] - t[0]  # 时间步长

    P_pred = np.zeros_like(t)

    P_pred[0] = P_t[0]  # 初始值

    print(f"Initial value (P_pred[0]): {P_pred[0]}")

    for i in range(1, len(t)):

        P_pred[i] = P_pred[i-1] + dt * (K1 * C_domestic[i-1] + K2 * C_oversea[i-1] + K3 * P_domestic[i-1] + K4 * T_domestic[i-1] + K5 * T_oversea2[i-1])

        if i == 1:

            print(f"First prediction step: P_pred[1] = {P_pred[1]}")

    return P_pred

  
  
  

# 定义离散化的微分方程2
# Notice：在预测时候得调用model2，因为两次调用用到的初始值不一样

def model2(t, K1, K2, K3, K4, K5, C_domestic, C_oversea, P_domestic, T_domestic, T_oversea2):

    dt = t[1] - t[0]  # 时间步长

    P_pred = np.zeros_like(t)

    P_pred[0] = P_t[9]  # 初始值

    print(f"Initial value (P_pred[0]): {P_pred[0]}")

    for i in range(1, len(t)):

        P_pred[i] = P_pred[i-1] + dt * (K1 * C_domestic[i-1] + K2 * C_oversea[i-1] + K3 * P_domestic[i-1] + K4 * T_domestic[i-1] + K5 * T_oversea2[i-1])

        if i == 1:

            print(f"First prediction step: P_pred[1] = {P_pred[1]}")

    return P_pred

  
  

# 使用 curve_fit 进行优化

params, _ = curve_fit(lambda t, K1, K2, K3, K4, K5: model(t, K1, K2, K3, K4, K5, C_domestic, C_oversea, P_domestic, T_domestic, T_oversea2), t, P_t)

  

# 打印求解的 K 值

print(f'K1: {params[0]}, K2: {params[1]}, K3: {params[2]}, K4: {params[3]}, K5: {params[4]}')

  

# 绘制预测值和真实值的对比图

P_pred = model(t, *params, C_domestic, C_oversea, P_domestic, T_domestic, T_oversea2)

plt.figure(figsize=(10, 6))

plt.plot(t, P_t, label='Real Value')

plt.plot(t, P_pred, label='Predicted Value')

plt.xlabel('Year')

plt.ylabel('Export Value')

plt.title('Comparison of Predicted Value and Real Value')

plt.legend()

plt.show()

  

# 计算拟合评价指标

mse = mean_squared_error(P_t, P_pred)

rmse = mean_squared_error(P_t, P_pred, squared=False)

mae = mean_absolute_error(P_t, P_pred)

r2 = r2_score(P_t, P_pred)

  

print(f'Mean Squared Error: {mse}')

print(f'Root Mean Squared Error: {rmse}')

print(f'Mean Absolute Error: {mae}')

print(f'R-squared: {r2}')

  
  

# 预测未来的自变量值

future_t = np.arange(2023, 2027)

  
  

# 定义一个函数来预测未来的自变量值
# Notice：此步很关键，预测了自变量微分与因变量间的关系还不够，还得求解自变量的自增变化量
def predict_future_values(t, values, future_t):

    model = LinearRegression()

    model.fit(t.reshape(-1, 1), values)

    future_values = model.predict(future_t.reshape(-1, 1))

    return future_values

  
  
  

C_domestic_future = predict_future_values(t, C_domestic, future_t)

C_oversea_future = predict_future_values(t, C_oversea, future_t)

P_domestic_future = predict_future_values(t, P_domestic, future_t)

T_domestic_future = predict_future_values(t, T_domestic, future_t)

T_oversea2_future = predict_future_values(t, T_oversea2, future_t)

  
  

# 预测未来三年的宠物食品出口

future_P_pred = model2(future_t, *params, C_domestic_future, C_oversea_future, P_domestic_future, T_domestic_future, T_oversea2_future)

  

print(f"未来三年宠物食品出口预测结果：{future_P_pred}")

print(f"pet food export in the future 3 years: {future_P_pred}")
```

### 随机森林

**现象**：随机森林算法，或者说这类概率策略性算法都有一个特点，当数据集的特征值过少的时候会发生预测值唯一的情况

						图：随机森林预测值唯一

![1732453549745.png](https://www.helloimg.com/i/2024/11/24/6743239747258.png)




### Pandas库

**现象**：Pandas库读取xlsx数据时候，要求不能有间隔行或者间隔列，且数据不能有空缺

						     图：间隔和空缺列

![1732453716230.png](https://www.helloimg.com/i/2024/11/24/6743243bb2e4f.png)

