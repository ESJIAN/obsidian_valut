**目录**

[一、安装前期准备](https://blog.csdn.net/YYDS_WV/article/details/137825313#t0)

[（1）查看电脑支持CUDA版本](https://blog.csdn.net/YYDS_WV/article/details/137825313#t1)

[1）方法一，终端查看](https://blog.csdn.net/YYDS_WV/article/details/137825313#t2)

[2）方法二，NVIDIA控制面板查看](https://blog.csdn.net/YYDS_WV/article/details/137825313#t3)

[（2）注册NVIDIA账号](https://blog.csdn.net/YYDS_WV/article/details/137825313#t4)

[二、CUDA的安装与配置](https://blog.csdn.net/YYDS_WV/article/details/137825313#t5)

[（1）CUDA的下载](https://blog.csdn.net/YYDS_WV/article/details/137825313#t6)

[（2）CUDA的安装与配置](https://blog.csdn.net/YYDS_WV/article/details/137825313#t7)

[（3）检查CUDA是否安装成功](https://blog.csdn.net/YYDS_WV/article/details/137825313#t8)

[（4）CUDA安装失败](https://blog.csdn.net/YYDS_WV/article/details/137825313#t9)

[1）方法一，设置环境变量](https://blog.csdn.net/YYDS_WV/article/details/137825313#t10)

[2）方法二，重装CUDA](https://blog.csdn.net/YYDS_WV/article/details/137825313#t11)

[三、CUDNN的安装与配置](https://blog.csdn.net/YYDS_WV/article/details/137825313#t12)

[（1）CUDNN的下载](https://blog.csdn.net/YYDS_WV/article/details/137825313#t13)

[（2）CUDNN的安装与配置](https://blog.csdn.net/YYDS_WV/article/details/137825313#t14)

[（3）检查CUDNN是否安装成功](https://blog.csdn.net/YYDS_WV/article/details/137825313#t15)

---

博主最近在学习深度神经网络模型时，用CPU跑的速度太低于是想着使用GPU，使用GPU就离不开CUDA以及CUDNN的下载，博主花了两天时间看了许多博客，走了一些弯路最终成功安装，现在将以自己安装过程为例，对CUDA和CUDNN的安装进行详细介绍，让大家少浪费些时间

## 一、安装前期准备

### （1）查看电脑支持CUDA版本

#### 1）方法一，终端查看

1.同时点击win+r，输入cmd点击“确定”，进入终端窗口，输入nvidia-smi[查看CUDA版本](https://so.csdn.net/so/search?q=%E6%9F%A5%E7%9C%8BCUDA%E7%89%88%E6%9C%AC&spm=1001.2101.3001.7020)

![](https://i-blog.csdnimg.cn/blog_migrate/2cd7f153cf3aa6b11c5c9ba3cef8e28f.png)

如图所示，博主的CUDA支持版本为12.2

![](https://i-blog.csdnimg.cn/blog_migrate/e0ef9eda87f07e7542d40b817a848c0d.png)

#### 2）方法二，NVIDIA控制面板查看

1.打开NVIDIA控制面板

![](https://i-blog.csdnimg.cn/blog_migrate/c9d94587fd16c86886e8834a5cce47f2.png)

2.打开后点击“帮助”，点击“系统信息”

![](https://i-blog.csdnimg.cn/blog_migrate/6e676ad57bf9d99907e90e0bd224fecd.png)

3.打开系统信息后点击“组件”，查看NVIDIA CUDA支持版本，下载时选择前两位即可，比如说博主CUDA 12.2.146 那么只要下载 CUDA 12.2.X 即可使用

![](https://i-blog.csdnimg.cn/blog_migrate/a9fe810e4231e9cebb6725231a6c271d.png)

### （2）注册NVIDIA账号

1.进入NVIDIA官网，点击“立即加入”进行注册

![](https://i-blog.csdnimg.cn/blog_migrate/7499f5c76a7cc375d5501efe14867956.png)

2.随后输入自己的邮箱完成登录即可

## 二、CUDA的安装与配置

### （1）CUDA的下载

1.CUDA官网下载地址：[CUDA Toolkit Archive](https://developer.nvidia.com/cuda-toolkit-archive "CUDA Toolkit Archive")

2.选择电脑支持CUDA版本进行下载，因为博主是12.2.146,所以只要是 CUDA Toolkit 12.2.X 都可以进行下载,博主在这里选择的是 CUDA Toolkit 12.2.1

![](https://i-blog.csdnimg.cn/blog_migrate/9110562a2c69197dc12e430c621dfe5c.png)

3.点击后等待一会即可进行下载，因为博主是Windows操作系统所以选择“Windows”，选择本地下载“exe(local)”，最后“Download”进行本地下载

![](https://i-blog.csdnimg.cn/blog_migrate/0adb81f2dbf28beb6dd3f7336d040bdd.png)

4.下载完成后运行exe文件进行下载

![](https://i-blog.csdnimg.cn/blog_migrate/8cb50245d3d263036692d58aeef8a65d.png)

### （2）CUDA的安装与配置

1.**选择CUDA下载路径：这里博主建议按照文件提供路径下载到C盘，因为博主第一次下载时选择是D盘结果导致安装失败，这里我们选择C:\User\25896\AppData\Local\Temp\cuda

![](https://i-blog.csdnimg.cn/blog_migrate/b0f1d08242d5afb90b4b07751d6a4fd9.png)

2.**系统检查：选择“同意并继续”

![](https://i-blog.csdnimg.cn/blog_migrate/a6577875362f801b7ec936d45c8bdbf8.png)

3.**许可协议：**选择“自定义”，然后点击“下一步”

![](https://i-blog.csdnimg.cn/blog_migrate/e749e29e4d66cce9d7ce49b9476e8d4e.png)

4.**选项，自定义安装选项：**CUDA必选，点击加号，如果Other components和Driver components的新版本比当前版本低的话就不用勾选，否则会导致安装失败

![](https://i-blog.csdnimg.cn/blog_migrate/6567f86ed0c69ba11e02dbbc1051daa1.png)

这里博主Other components和Driver components的当前版本高于或等于新版本号所以不勾选，然后点击“下一步”

注意：不同版本的CUDA相关的安装选择的组件不同，大家注意甄别

5.**选项，自定义安装位置：**可以选择 CUDA Development 和CUDA Documentation文件的安装路径，这里博主也是选择提供的路径，这里我们选择的是C:\Program Files\NVIDIA Computing Toolkit\CUDA\v12.2,随后点击“下一步”进行安装，等待安装成功

![](https://i-blog.csdnimg.cn/blog_migrate/a48bc4aefef38d2335bf1117d51bd52a.png)

### （3）[检查CUDA](https://so.csdn.net/so/search?q=%E6%A3%80%E6%9F%A5CUDA&spm=1001.2101.3001.7020)是否安装成功

安装成功后，同时点击win+r，输入cmd进入终端窗口输入nvcc -V（注意用大写V，博主使用小写v无法成功运行），若结果如图所示则证明CUDA安装成功

![](https://i-blog.csdnimg.cn/blog_migrate/7f29a5b0cface4fce71127a782fa5a55.png)

### （4）CUDA安装失败

若nvcc -V无法返回结果，则表明CUDA安装失败

#### 1）方法一，设置环境变量

1.我们打开“编辑系统环境变量”

![](https://i-blog.csdnimg.cn/blog_migrate/4cf65dc4e156355f7c940338c347babe.png)

2.点击“环境变量”

![](https://i-blog.csdnimg.cn/blog_migrate/5f23caa8496c20fc78cc35cb19b9b082.png)

3.查看系统变量中是否有变量CUDA_PATH和CUDA_PATH_V12_2（不同版本V后数字不同），并检查路径是否正确

![](https://i-blog.csdnimg.cn/blog_migrate/91938559a47148373d931f2849d0c330.png)

若没有则添加两变量并添加正确路径；若错误则修改成正确路径（路径为**选项，自定义安装位置**时选择的路径）

4.查看系统变量中的Path是否有v12.2\bin，若没有则添加正确路径；若错误则修改成正确路径（路径为**选项，自定义安装位置**时选择的路径）

![](https://i-blog.csdnimg.cn/blog_migrate/c78c79c2a6b6aae5fbf385c055d3f975.png)

#### 2）方法二，重装CUDA

1.**卸载CUDA：**打开“控制面板”，点击“程序”，点击“程序和功能”

![](https://i-blog.csdnimg.cn/blog_migrate/dab841843ba6ff5b9c8ca0d9243e27ec.png)

![](https://i-blog.csdnimg.cn/blog_migrate/37410133e24ce637d57541bcf2e16ee8.png)

找到“NVIDIA CUDA”相关程序，右击进行卸载

![](https://i-blog.csdnimg.cn/blog_migrate/da3748ff779101613e8c95f6ec833377.png)

2.**删除系统变量：**打开“编辑系统环境变量”，点击“环境变量”，删除系统变量中CUDA_PATH和CUDA_PATH_V12_2，以及系统变量Path中名为“NVIDIA GPU Computing Toolkit”相关变量

![](https://i-blog.csdnimg.cn/blog_migrate/dcfe7e81b5b72d7e2aed2cfe41599284.png)

![](https://i-blog.csdnimg.cn/blog_migrate/78d18ef00f8d358470058e8c3627ee0f.png)

3.**CUDA下载：**按照 “二、CUDA的安装与配置” 重新配置，博主当时因为下D盘导致CUDA安装失败，所以进行卸载重新下载到C盘才成功安装CUDA

## 三、CUDNN的安装与配置

### （1）CUDNN的下载

1.CUDNN官网下载地址：[CUDNN Archive](https://developer.nvidia.com/rdp/cudnn-archive "CUDNN Archive")

2.选择CUDNN支持CUDA版本下载，博主下载的CUDA版本为12.2在这里选择的CUDNN版本为v8.9.3

![](https://i-blog.csdnimg.cn/blog_migrate/f94db0a13f7ee81f9fd442a78dbb0639.png)

3.因为博主是Windows系统所以选择“Local Installer of Windows”进行下载

### （2）CUDNN的安装与配置

1.下载好CUDNN的压缩包后进行解压，得到如图所示文件

![](https://i-blog.csdnimg.cn/blog_migrate/b154b681ac13394215a7ccedbfe4085c.png)

2.打开\NVIDIA Computing Toolkit\CUDA\v12.2，将CUDNN对应bin、lib、include三个文件与CUDA对应的bin、lib、include进行合并，将CUDNN内文件全部复制到CUDA对应文件夹内

![](https://i-blog.csdnimg.cn/blog_migrate/28e6b72528db09c4953f2805a3d7b071.png)

如图博主将CUDNN\lib\x64的文件全部复制到CUDA\v12.2\lib\x64中

3.打开“编辑系统环境变量”，点击“环境变量”，点击“系统变量”中Path添加C:\Program Files\NVIDIA Computing Toolkit\CUDA\v12.2\lib和v12.2\libnvvp以及v12.2\include，点击“确定”完成配置

![](https://i-blog.csdnimg.cn/blog_migrate/f65fc812027ed4eadbc6f36bf867b133.png)

### （3）检查CUDNN是否安装成功

打开C:\Program Files\NVIDIA Computing Toolkit\CUDA\v12.2\extras\demo_suite，查看是否有文件bandwidthTest.exe以及deviceQuery.exe，若存在则在该文件中打开cmd运行两.exe文件

![](https://i-blog.csdnimg.cn/blog_migrate/2f77ae1317c57c99664ad6174bb6ad3b.png)

运行bandwidthTest.exe结果

![](https://i-blog.csdnimg.cn/blog_migrate/ddbe969ebec20a11b60156fec2d4b8db.png)

运行deviceQuery.exe结果

![](https://i-blog.csdnimg.cn/blog_migrate/bf96a58393234d59c990ef46a9d06907.png)

若都能成功运行就恭喜你CUDNN安装成功了