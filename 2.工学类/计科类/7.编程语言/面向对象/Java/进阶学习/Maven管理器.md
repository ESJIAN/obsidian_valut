![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d648abe818e98b0d3ba938eb7c07d2d4.jpeg#pic_center)

#### 文章目录

- - - [一、引言](https://blog.csdn.net/qq_43410878/article/details/123812267#_6)
        - - [1.1 项目管理问题](https://blog.csdn.net/qq_43410878/article/details/123812267#11__10)
            - - [1.1.1 繁琐](https://blog.csdn.net/qq_43410878/article/details/123812267#111__17)
                - [1.1.2 复杂](https://blog.csdn.net/qq_43410878/article/details/123812267#112__21)
                - [1.1.3 冗余](https://blog.csdn.net/qq_43410878/article/details/123812267#113__25)
            - [1.2 项目管理方案](https://blog.csdn.net/qq_43410878/article/details/123812267#12__29)
        - [二、介绍](https://blog.csdn.net/qq_43410878/article/details/123812267#_41)
        - [三、Maven安装](https://blog.csdn.net/qq_43410878/article/details/123812267#Maven_59)
        - - [3.1 下载Maven](https://blog.csdn.net/qq_43410878/article/details/123812267#31_Maven_63)
            - [3.2 Maven安装](https://blog.csdn.net/qq_43410878/article/details/123812267#32_Maven_72)
            - - [3.2.1 解压](https://blog.csdn.net/qq_43410878/article/details/123812267#321__74)
                - [3.2.2 环境变量](https://blog.csdn.net/qq_43410878/article/details/123812267#322__87)
                - [3.2.3 测试](https://blog.csdn.net/qq_43410878/article/details/123812267#323__100)
        - [四、Maven配置](https://blog.csdn.net/qq_43410878/article/details/123812267#Maven_108)
        - - [4.1 本地仓库](https://blog.csdn.net/qq_43410878/article/details/123812267#41__112)
            - [4.2 JDK配置](https://blog.csdn.net/qq_43410878/article/details/123812267#42_JDK_130)
        - [五、仓库](https://blog.csdn.net/qq_43410878/article/details/123812267#_158)
        - - [5.1 概念](https://blog.csdn.net/qq_43410878/article/details/123812267#51__162)
            - [5.2 仓库分类](https://blog.csdn.net/qq_43410878/article/details/123812267#52__168)
            - [5.3 本地仓库](https://blog.csdn.net/qq_43410878/article/details/123812267#53__191)
            - [5.4 远程仓库](https://blog.csdn.net/qq_43410878/article/details/123812267#54__197)
            - - [5.4.1 中央仓库](https://blog.csdn.net/qq_43410878/article/details/123812267#541__199)
                - [5.4.2 公共仓库【`重点`】](https://blog.csdn.net/qq_43410878/article/details/123812267#542__209)
                - [5.4.3 私服【了解】](https://blog.csdn.net/qq_43410878/article/details/123812267#543__230)
        - [六、Idea-Maven](https://blog.csdn.net/qq_43410878/article/details/123812267#IdeaMaven_236)
        - - [6.1 在Idea中关联Maven](https://blog.csdn.net/qq_43410878/article/details/123812267#61_IdeaMaven_240)
            - [6.2 创建Maven项目](https://blog.csdn.net/qq_43410878/article/details/123812267#62_Maven_263)
            - - [6.2.1 新建项目](https://blog.csdn.net/qq_43410878/article/details/123812267#621__265)
                - [6.2.2 指定项目名](https://blog.csdn.net/qq_43410878/article/details/123812267#622__274)
                - [6.2.3 项目位置](https://blog.csdn.net/qq_43410878/article/details/123812267#623__281)
                - [6.2.4 项目结构](https://blog.csdn.net/qq_43410878/article/details/123812267#624__288)
                - [6.2.5 pom.xml文件](https://blog.csdn.net/qq_43410878/article/details/123812267#625_pomxml_307)
                - [6.2.6 项目类型](https://blog.csdn.net/qq_43410878/article/details/123812267#626__383)
            - [6.3 导入依赖jar](https://blog.csdn.net/qq_43410878/article/details/123812267#63_jar_404)
            - - [6.3.1 查找依赖](https://blog.csdn.net/qq_43410878/article/details/123812267#631__412)
                - [6.3.2 导入依赖](https://blog.csdn.net/qq_43410878/article/details/123812267#632__423)
                - [6.3.3 同步依赖](https://blog.csdn.net/qq_43410878/article/details/123812267#633__432)
                - [6.4.1 打包方式](https://blog.csdn.net/qq_43410878/article/details/123812267#641__445)
                - [6.4.2 web依赖](https://blog.csdn.net/qq_43410878/article/details/123812267#642_web_454)
                - [6.4.3 webapp目录](https://blog.csdn.net/qq_43410878/article/details/123812267#643_webapp_490)
                - [6.4.4 定义Servlet和Jsp](https://blog.csdn.net/qq_43410878/article/details/123812267#644_ServletJsp_509)
            - [6.5 部署web项目](https://blog.csdn.net/qq_43410878/article/details/123812267#65_web_516)
            - - [6.5.1 新增Tomcat](https://blog.csdn.net/qq_43410878/article/details/123812267#651_Tomcat_518)
                - [6.5.2 部署web项目](https://blog.csdn.net/qq_43410878/article/details/123812267#652_web_529)
                - [6.5.3 启动Tomcat](https://blog.csdn.net/qq_43410878/article/details/123812267#653_Tomcat_540)
            - [6.6 依赖生命周期](https://blog.csdn.net/qq_43410878/article/details/123812267#66__549)
            - - [6.6.1 概念](https://blog.csdn.net/qq_43410878/article/details/123812267#661__551)
                - [6.6.2 使用方式](https://blog.csdn.net/qq_43410878/article/details/123812267#662__573)
                - [6.6.3 生命周期详解](https://blog.csdn.net/qq_43410878/article/details/123812267#663__602)
        - [七、Maven指令](https://blog.csdn.net/qq_43410878/article/details/123812267#Maven_612)
        - - [7.1 命令行](https://blog.csdn.net/qq_43410878/article/details/123812267#71__616)
            - [7.2 Maven面板](https://blog.csdn.net/qq_43410878/article/details/123812267#72_Maven_646)
        - [八、私服](https://blog.csdn.net/qq_43410878/article/details/123812267#_655)
        - - [8.1 概念](https://blog.csdn.net/qq_43410878/article/details/123812267#81__659)
            - [8.2 架构](https://blog.csdn.net/qq_43410878/article/details/123812267#82__668)
            - [8.3 Nexus安装【了解】](https://blog.csdn.net/qq_43410878/article/details/123812267#83_Nexus_677)
            - - [8.3.1 下载](https://blog.csdn.net/qq_43410878/article/details/123812267#831__679)
                - [8.3.2 安装](https://blog.csdn.net/qq_43410878/article/details/123812267#832__685)
            - [8.4 启动【了解】](https://blog.csdn.net/qq_43410878/article/details/123812267#84__694)
            - [8.5 Nexus登录【了解】](https://blog.csdn.net/qq_43410878/article/details/123812267#85_Nexus_702)
            - [8.6 仓库列表【了解】](https://blog.csdn.net/qq_43410878/article/details/123812267#86__712)
            - [8.7 Maven配置私服 【`重点`】](https://blog.csdn.net/qq_43410878/article/details/123812267#87_Maven__733)
            - - [8.7.1 仓库组](https://blog.csdn.net/qq_43410878/article/details/123812267#871__737)
                - [8.7.2 Maven关联私服](https://blog.csdn.net/qq_43410878/article/details/123812267#872_Maven_748)
            - [8.8 Maven项目部署到私服](https://blog.csdn.net/qq_43410878/article/details/123812267#88_Maven_794)
        - [九、Maven分模块开发](https://blog.csdn.net/qq_43410878/article/details/123812267#Maven_824)

#### 一、引言

---

##### 1.1 项目管理问题

> 写项目时，我们需要引用各种 jar 包，尤其是比较大的工程，引用的 jar 包往往有几十个乃至上百个， 每用  
> 到一种 jar 包，都需要手动引入工程目录，而且经常遇到各种让人抓狂的 jar 包冲突，版本冲突。
> 
> 写完项目我们后面还需要把代码与各种配置文件、资源整合到一起，定型打包，如果是 web项目，还需要发布到服务器

###### 1.1.1 繁琐

> 要为每个项目手动导入所需的jar，需要搜集全部jar

###### 1.1.2 复杂

> 项目中的jar如果需要版本升级，就需要再重新搜集jar

###### 1.1.3 冗余

> 相同的jar在不同的项目中保存了多份

##### 1.2 项目管理方案

> Java项目需要一个统一的便捷的管理工具：Maven
> 
> Maven的好处  
> ​ Maven 的一个核心特性就是依赖管理。当我们涉及到多模块的项目（包含成百个模块或者子项目），管理依赖就变成一项困难的任务。Maven 展示出了它对处理这种情形的高度控制。  
> ​ 传统的 WEB 项目中，我们必须将工程所依赖的 jar 包复制到工程中，导致了工程的变得很大。maven 工程中不直接将 jar 包导入到工程中，而是通过在 pom.xml 文件中添加所需 jar 包的坐标，这样就很好的避免了 jar 直接引入进来，在需要用到 jar 包的时候，只要查找 pom.xml 文件，再通过 pom.xml 文件中的坐标，到一个专门用于”存放 jar 包的仓库”(maven 仓库)中根据坐标从而找到这些 jar 包，再把这些 jar 包拿去运行。  
> ​  
> Maven常应用于大型项目，可以提高开发效率，也就是Maven的分模块开发，例如：  
> 传统项目 按层分： dao service web  
> 互联网项目 按业务分： 用户管理 订单管理 支付管理 …

#### 二、介绍

---

> Maven这个单词来自于意第绪语（犹太语），意为知识的积累.
> 
> Maven是一个基于项目对象模型（POM）的概念的纯java开发的开源的项目管理工具。主要用来管理java项目，进行依赖管理(jar包依赖管理)和项目构建(项目编译、打包、测试、部署)。此外还能分模块开发，提高开发效率。
> 
> 项目的一键构建  
> ​ 我们的项目，往往都要经历编译、测试、运行、打包、安装 ，部署等一系列过程。  
> ​  
> 什么是构建？  
> ​ 指的是项目从编译、测试、运行、打包、安装 ，部署整个过程都交给 maven 进行管理，这个  
> 过程称为构建。
> 
> 一键构建  
> ​ 指的是整个构建过程，使用 maven 一个命令可以轻松完成整个工作。

#### 三、[Maven安装](https://so.csdn.net/so/search?q=Maven%E5%AE%89%E8%A3%85&spm=1001.2101.3001.7020)

---

##### 3.1 下载Maven

> 下载Maven

|[http://us.mirrors.quenda.co/apache/maven/maven-3/3.5.4/binaries/](http://us.mirrors.quenda.co/apache/maven/maven-3/3.5.4/binaries/)|
|---|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e63e76456317996d7bc0215af95bfc91.jpeg#pic_center)|

```
                   |
```

##### 3.2 Maven安装

###### 3.2.1 解压

> 注意： Maven 下载后，将 Maven 解压到一个没有中文没有空格的路径下，比如 D:\maven 下面
> 
> 解压后，有如下目录：

```markdown
`bin:含有mvn运行的脚本`
`boot:含有plexus-classworlds类加载器框架,Maven 使用该框架加载自己的类库。`
`conf:含有settings.xml配置文件`
`lib:含有Maven运行时所需要的java类库`
```

###### 3.2.2 环境变量

> maven依赖java环境，所以要确保java环境已配置好
> 
> 使用maven必须配置JDK。
> 
> 在环境变量 path 配置 MAVEN 安装目录的bin目录（和之前jdk的配置类似）

```markdown
`MAVEN_HOME = maven的安装目录`
`PATH = maven的安装目录下的bin目录`
```

###### 3.2.3 测试

> 查看maven版本信息

```cmd
mvn -v
```

#### 四、[Maven配置](https://so.csdn.net/so/search?q=Maven%E9%85%8D%E7%BD%AE&spm=1001.2101.3001.7020)

---

##### 4.1 本地仓库

> maven的conf目录中有 [settings.xml](https://blog.csdn.net/qq_43410878/article/details/123812267) ，是maven的配置文件，做如下配置：

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 			  	http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
  <!-- 选择一个磁盘目录，作为本地仓库 -->
  <localRepository>D:\Program Files\maven\myrepository</localRepository>
```

##### 4.2 JDK配置

> 在 [](https://blog.csdn.net/qq_43410878/article/details/123812267)标签中 增加 一个 [](https://blog.csdn.net/qq_43410878/article/details/123812267)标签，限定maven项目默认的jdk版本.
> 
> 内容如下：

```xml
<profiles>
    <!-- 在已有的profiles标签中添加profile标签 -->
	<profile>    
        <id>myjdk</id>    
        <activation>    
            <activeByDefault>true</activeByDefault>    
            <jdk>1.8</jdk>    
        </activation>    
        <properties>    
            <maven.compiler.source>1.8</maven.compiler.source>    
            <maven.compiler.target>1.8</maven.compiler.target>
            <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion> 
        </properties>    
    </profile>
</profiles>
<!-- 让增加的 profile生效 -->
<activeProfiles>
    <activeProfile>myjdk</activeProfile>
</activeProfiles>
```

#### 五、仓库

---

##### 5.1 概念

> - 存储依赖的地方，体现形式就是本地的一个目录。
>     
> - 仓库中不仅存放依赖，而且管理着每个依赖的唯一标识(坐标)，Java项目凭坐标获取依赖。
>     

##### 5.2 仓库分类

> maven 中仓库的类型：
> 
> 本地仓库 ：用来存储从远程仓库或中央仓库下载的插件和 jar 包，项目使用一些插件或 jar 包，  
> 优先从本地仓库查找  
> 默认本地仓库位置在 u s e r . d i r / . m 2 / r e p o s i t o r y ， {user.dir}/.m2/repository，user.dir/.m2/repository，{user.dir}表示windows 用户目录。  
> 注意：可在 MAVE_HOME/conf/settings.xml 文件中配置本地仓库位置。
> 
> 远程仓库：如果本地需要插件或者 jar 包，本地仓库没有，默认去远程仓库下载。  
> 远程仓库可以在互联网内也可以在局域网内。
> 
> 中央仓库 ：在 maven 软件中内置一个远程仓库地址 http://repo1.maven.org/maven2 ，它是中央仓库，服务于整个互联网，它是由 Maven 团队自己维护，里面存储了非常全的 jar 包，它包含了世界上大部分流行的开源项目构件。

|仓库分类|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6457420f9b70e922cf49fca56450b940.jpeg#pic_center)|

> 当需要依赖时，会从仓库中取查找，优先顺序为：
> 
> [本地仓库 > 私服(如果配置了的话) > 公共仓库(如果配置了的话) > 中央仓库](https://blog.csdn.net/qq_43410878/article/details/123812267)

##### 5.3 本地仓库

> 即在[settings.xml](https://blog.csdn.net/qq_43410878/article/details/123812267) 中配置的目录。
> 
> 使用过了的依赖都会自动存储在本地仓库中，后续可以复用。

##### 5.4 远程仓库

###### 5.4.1 中央仓库

> - Maven 中央仓库是由 Maven 社区提供的仓库，不用任何配置，maven中内置了中央仓库的地址。
>     
>     其中包含了绝大多数流行的开源Java构件。
>     
> - https://mvnrepository.com/ 可以搜索需要的依赖的相关信息（仓库搜索服务）
>     
>     http://repo.maven.apache.org/maven2/ 中央仓库地址
>     

###### 5.4.2 公共仓库【`重点`】

> - 除中央仓库之外，还有其他远程仓库。  
>     比如aliyun仓库（http://maven.aliyun.com/nexus/content/groups/public/）
>     
> - 中央仓库在国外，下载依赖速度过慢，所以都会配置一个国内的公共仓库替代中央仓库。
>     

```xml
<!--setting.xml中添加如下配置-->
<mirrors>
	<mirror>
        <id>aliyun</id>  
        <!-- 中心仓库的 mirror(镜像) -->
        <mirrorOf>central</mirrorOf>    
        <name>Nexus aliyun</name>
        <!-- aliyun仓库地址 以后所有要指向中心仓库的请求，都会指向aliyun仓库-->
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>  
    </mirror>
</mirrors>
```

###### 5.4.3 私服【了解】

> 公司范围内共享的仓库，不对外开放。
> 
> 可以通过 Nexus来创建、管理一个私服。

#### 六、Idea-Maven

---

##### 6.1 在Idea中关联Maven

> 在idea中关联本地安装的maven，后续就可以通过idea使用maven来管理项目
> 
> Maven 工程的目录结构
> 
> 作为一个 maven 工程，它的 src目录和 pom.xml 是必备的。  
> 进入 src目录后，我们发现它里面的目录结构如下：
> 
> src/main/java —— 存放项目的.java 文件  
> src/main/resources —— 存放项目资源文件，如 spring, hibernate 配置文件  
> src/test/java —— 存放所有单元测试.java 文件，如 JUnit 测试类  
> src/test/resources —— 测试资源文件  
> target —— 项目输出位置，编译后的class 文件会输出到此目录  
> pom.xml——maven 项目核心配置文件
> 
> 注意：如果是普通的 java 项目，那么就没有webapp 目录。

|在全局设置中，关联Maven|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/448cf27a8e7b2995e54c97384cb6eb09.jpeg#pic_center)|
||

##### 6.2 创建Maven项目

###### 6.2.1 新建项目

> 新建项目，要选择 [Maven](https://blog.csdn.net/qq_43410878/article/details/123812267) 选项

|如下选项|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c3c94f45bd546c6e7b16c3cde286ad2b.jpeg#pic_center)|
||

###### 6.2.2 指定项目名

|设置项目名|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/14005aa75e6659610243e00e3765b1e7.jpeg#pic_center)|
||

###### 6.2.3 项目位置

|项目位置如下|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/23dee5b8b61ae5f327bc4b7cee2ebbfd.jpeg#pic_center)|
||

###### 6.2.4 项目结构

> - src/main/java 存放源代码，建包，放项目中代码(service,dao,User,…)
>     
> - src/main/resources 书写配置文件，项目中的配置文件(jdbc.properties)
>     
> - src/test/java 书写测试代码，项目中测试案例代码
>     
> - src/test/resources 书写测试案例相关配置文件
>     
> - 目根/pom.xml (project object model) maven项目核心文件，其中定义项目构建方式，声明依赖等
>     
> - [注意：](https://blog.csdn.net/qq_43410878/article/details/123812267)项目中的建包，建类，执行，都和普通项目无差异
>     

|项目结构如下：|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b73d8c09a973c842cd90753c4e1ee085.jpeg#pic_center)|
||

###### 6.2.5 pom.xml文件

> pom 基本配置  
> pom.xml 是 Maven 项目的核心配置文件，位于每个工程的根目录，基本配置如下

```xml
<project > ：文件的根节点 .
<modelversion > ： pom.xml 使用的对象模型版本
<groupId > ：项目名称，一般写项目的域名
<artifactId > ：模块名称，子项目名或模块名称
<version > ：产品的版本号 .
<packaging > ：打包类型，一般有 jar、war、pom 等
<name > ：项目的显示名，常用于 Maven 生成的文档。
<description > ：项目描述，常用于 Maven 生成的文档
<dependencies> ：项目依赖构件配置，配置项目依赖构件的坐标
<build> ：项目构建配置，配置编译、运行插件等。
```

```xml
例如：配置tomcat7插件和jdk1.8
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <port>8888</port>
        </configuration>
      </plugin>
      <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-compiler-plugin</artifactId>
          <configuration>
            <target>1.8</target>
            <source>1.8</source>
            <encoding>UTF-8</encoding>
          </configuration>
        </plugin>
    </plugins>
  </build>
```

```xml
在 pom.xml 文件中锁定 jar 包版本配置

<!-- 统一管理jar包版本 -->
<properties>
    <mybatis.version>3.4.5</mybatis.version>
</properties>

<!-- 锁定jar包版本（可省略） -->
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>${mybatis.version}</version>
        </dependency>
    </dependencies>
</dependencyManagement>

<!-- 项目依赖jar包 -->
<dependencies>
	<dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis</artifactId>
        <version>${mybatis.version}</version>
	</dependency>
</dependencies>
```

###### 6.2.6 项目类型

> 根据项目类型，在[pom.xml](https://blog.csdn.net/qq_43410878/article/details/123812267)中做出对应配置，添加配置：[war/jar](https://blog.csdn.net/qq_43410878/article/details/123812267)

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.qf</groupId>
    <artifactId>test01</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!-- 打包方式，如果是java项目则用 jar，
         如果是web项目则用war -->
    <!--<packaging>war</packaging>-->
    <packaging>jar</packaging>
</project>
```

##### 6.3 导入依赖jar

> 建好项目后，需要导入需要的jar，要通过[坐标](https://blog.csdn.net/qq_43410878/article/details/123812267)
> 
> - 每个构件都有自己的坐标 = groupId + artifactId + version = 项目标识 + 项目名 + 版本号
>     
> - 在maven项目中只需要配置坐标，maven便会自动加载对应依赖。删除坐标则会移除依赖
>     

###### 6.3.1 查找依赖

> 依赖查找服务：https://mvnrepository.com/ ，获得依赖的坐标，在maven项目中导入。

|查找依赖坐标|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/308b98f84a1a88526042d539c55e99ec.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1bcf8ee58fdad634cd1c8441c3d6c072.jpeg#pic_center)|
||

###### 6.3.2 导入依赖

> 在项目的pom文件中，增加依赖

|在项目的pom.xml文件添加依赖|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/346781eb28ba6db152faa99a75eda846.jpeg#pic_center)|
||

###### 6.3.3 同步依赖

> 引入坐标后，同步依赖，确认导入。

|窗口右下角弹窗，刷新依赖，使新加的配置被maven加载|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/638f33d913198a4fae5a2df0aba69236.jpeg#pic_center)|
||

####6.4 创建web项目

###### 6.4.1 打包方式

> pom.xml中设置 [war](https://blog.csdn.net/qq_43410878/article/details/123812267)

|web项目打包方式为：[war](https://blog.csdn.net/qq_43410878/article/details/123812267)|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/55af8310bbf715956275ab490d06a169.jpeg#pic_center)|
||

###### 6.4.2 web依赖

> 导入 [JSP](https://blog.csdn.net/qq_43410878/article/details/123812267) 和 [Servlet](https://blog.csdn.net/qq_43410878/article/details/123812267) 和 [JSTL](https://blog.csdn.net/qq_43410878/article/details/123812267)依赖，使项目具有web编译环境

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project ...>
    ...
    <packaging>war</packaging>

	<!-- 导入JSP 和 Servlet 和 JSTL 依赖 -->
    <dependencies>
        <dependency>
            <!-- jstl 支持 -->
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <dependency>
            <!-- servlet编译环境 -->
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <!-- jsp编译环境 -->
            <groupId>javax.servlet</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.0</version>
            <scope>provided</scope>
        </dependency>
    </dependencies>
</project>
```

###### 6.4.3 webapp目录

> 按照maven规范，新建web项目特有目录

|新建如下目录和文件|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2924d7d43ed1d80def76080275a7ddcd.jpeg#pic_center)|
||

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
	<!-- 这是一个空白的web.xml文件模板 -->
</web-app>
```

###### 6.4.4 定义Servlet和Jsp

|照常定义即可|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0f22da8fb25218602f382174fd4a705d.jpeg#pic_center)|
||

##### 6.5 部署web项目

###### 6.5.1 新增Tomcat

|新增Tomcat|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c7da8a518874a3a5d8f718d7311b0f15.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/75e63be4cef51496388eb458c7453bdc.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1fd25702fb7cf256957d253fb1496b37.jpeg#pic_center)|
||

###### 6.5.2 部署web项目

|部署web项目|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/48568765754247c4777c25fdbeed7e0f.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f94514eb93d6a1b69172acdb08e4ee53.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/dcabacd37594a1f1a1eeb015c7f515fb.jpeg#pic_center)|
||

###### 6.5.3 启动Tomcat

|启动Tomcat|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/400de4215b6acfaf0ae310baf28a4095.jpeg#pic_center)|
||
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c566df61d237d980c040d0565b799569.jpeg#pic_center)|
||

##### 6.6 依赖生命周期

###### 6.6.1 概念

> Jar包生效的时间段，即Jar的生命周期
> 
> 依赖范围  
> 在 pom.xml 文件中添加坐标时需要指定依赖范围（scope标签），依赖范围包括：
> 
> compile：编译范围，指 A在编译时依赖 B，此范围为默认依赖范围。编译范围的依赖会用在  
> 编译、测试、运行，由于运行时需要所以编译范围的依赖会被打包。
> 
> provided：provided 依赖只有在当 JDK 或者一个容器已提供该依赖之后才使用， provided 依  
> 赖在编译和测试时需要，在运行时不需要，比如：servlet api 被 tomcat 容器提供。
> 
> runtime：runtime 依赖在运行和测试系统的时候需要，但在编译的时候不需要。比如：jdbc  
> 的驱动包。由于运行时需要所以 runtime 范围的依赖会被打包。
> 
> test：test 范围依赖 在编译和运行时都不需要，它们只有在测试编译和测试运行阶段可用，  
> 比如：junit。由于运行时不需要所以test范围依赖不会被打包。
> 
> system：system 范围依赖与 provided 类似，但是你必须显式的提供一个对于本地系统中 JAR  
> 文件的路径，需要指定 systemPath 磁盘路径，system依赖不推荐使用。

###### 6.6.2 使用方式

> 项目中导入的依赖可以做生命周期的管理

```xml
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.6</version>
    <!-- 生命周期 -->
    <scope>compile</scope>
</dependency>
<dependency>
    <!-- servlet编译环境 -->
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <!-- 生命周期 -->
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <!-- 生命周期 -->
    <scope>test</scope>
</dependency>
```

###### 6.6.3 生命周期详解

|标识|周期|
|---|---|
|compile|缺省值，适用于所有阶段（测试运行，编译，运行，打包）|
|provided|类似compile，期望JDK、容器或使用者会提供这个依赖。如servlet-api.jar；适用于（测试运行，编译）阶段|
|runtime|只在运行时使用，如 mysql的驱动jar，适用于（运行，测试运行）阶段|
|test|只在测试时使用，适用于（编译，测试运行）阶段，如 junit.jar|
|system|Maven不会在仓库中查找对应依赖，在本地磁盘目录中查找；适用于（编译，测试运行，运行）阶段|

#### 七、Maven指令

---

##### 7.1 命令行

> 通过Idea打开 [cmd](https://blog.csdn.net/qq_43410878/article/details/123812267)，然后执行Maven指令
> 
> Maven的常用命令
> 
> clean 清理编译的文件（清理target文件夹）
> 
> compile 编译了主目录的文件（只编译项目中src\main目录下的代码）
> 
> test 编译并运行了测试目录的文件（编译运行src\test目录下的代码）
> 
> package 打包（将war包，该war的命名规范取决于pom.xml文件中的命名）
> 
> install 就是把项目发布到本地仓库
> 
> deploy 上传到私服
> 
> tomcat：run 一键启动

|打开 cmd，并定位到项目目录|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f13859485f5ae2bbc18108f35275c35f.jpeg#pic_center)|
||

|执行maven指令|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a6de14fac865fe3b1b664741d2466940.jpeg#pic_center)|
||

##### 7.2 Maven面板

> Idea中有Maven面板，其中可以快速执行Maven指令

|maven面板|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b2e8920c3869ea13d28d74783e4c30ae.jpeg#pic_center)|
||

#### 八、私服

---

##### 8.1 概念

> - 私服是架设在局域网的一种特殊的远程仓库，目的是代理远程仓库及部署第三方构件。
>     
> - 有了私服之后，当 Maven 需要下载依赖时，直接请求私服，私服上存在则下载到本地仓库；否则，私服请求外部的远程仓库，将构件下载到私服，再提供给本地仓库下载。
>     
> - 私服可以解决在企业做开发时每次需要的jar包都要在中心仓库下载,且每次下载完只能被自己使用,不能被其他开发人员使用
>     
> - 所谓私服就是一个服务器,但是不是本地层面的,是公司层面的,公司中所有的开发人员都在使用同一个私服
>     

##### 8.2 架构

|无私服|有私服|
|:-:|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e181055104c872b2663e1d247690bcfd.png#pic_center)|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cf7024a32c290339faebac37675da704.png#pic_center)|
|||

> 我们可以使用专门的 Maven 仓库管理软件来搭建私服，比如：[Apache Archiva](http://archiva.apache.org/index.cgi)，[Artifactory](http://www.jfrog.com/home/v_artifactory_opensource_overview/)，[Sonatype Nexus](http://www.sonatype.org/nexus/)。这里我们使用 [Sonatype Nexus](https://blog.csdn.net/qq_43410878/article/details/123812267)

##### 8.3 Nexus安装【了解】

###### 8.3.1 下载

> - 官网：https://blog.sonatype.com/
> - 下载地址：[https://help.sonatype.com/repomanager2/download/download-archives---repository-manager-oss](https://help.sonatype.com/repomanager2/download/download-archives---repository-manager-oss)

###### 8.3.2 安装

> 下载nexus-2.x-bundle.zip,解压即可

|nexus安装目录|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/45eb32c753f1bff152b3af952cec96d5.jpeg#pic_center)|
||

##### 8.4 启动【了解】

> - 解压后在bin目录中执行：
>     - nexus install 在系统中安装nexus服务
>     - nexus uninstall 卸载nexus服务
>     - nexus start 启动服务
>     - nexus stop 停止服务

##### 8.5 Nexus登录【了解】

> 访问私服：http://localhost:8081/nexus/

|登录Nexus才可以使用Nexus管理功能|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/16e545e92ffbb0c4b69aa4ed914a73f4.jpeg#pic_center)|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/631217a2474b3d5ef7499b3d1e387d45.jpeg#pic_center)|

##### 8.6 仓库列表【了解】

|仓库类型|描述|
|---|---|
|group|包含多个仓库，通过group库的地址可以从包含的多个仓库中查找构件|
|hosted|私服 服务器本地的仓库，其中存储诸多构件|
|proxy|代理仓库，其会关联一个远程仓库, 比如中央仓库，aliyun仓库，向该仓库查找构件时，如果没有会从其关联的仓库中下载|

|仓库名|描述|
|---|---|
|Releases|存放项目的稳定发布版本，一个模块做完后如果需要共享给他人，可以上传到私服的该库|
|Snapshots|对应不稳定的发布版本|
|3rd party|存放中央仓库没有的 ，如ojdbc.jar，可以上传到私服的该库中|

|仓库列表|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/be8a641ecab6c3e79353f8150356a2d6.jpeg#pic_center)|
||

##### 8.7 Maven配置私服 【`重点`】

> 在maven中配置私服，使得maven可以从私服上获取构件

###### 8.7.1 仓库组

> 而此时就有问题，私服中有很多仓库，每个仓库都有自己的url，则项目中配置哪个仓库呢 ?
> 
> 私服中有一个仓库组，组中包含多个仓库，可以指定仓库组的url，即可从多个仓库中获取构件

|仓库组 注意：proxy的仓库排序在最后|
|:-:|
|![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/297c5f5bf6ee44455f785181d12f68b8.jpeg#pic_center)|
||

###### 8.7.2 Maven关联私服

> 配置[settings.xml](https://blog.csdn.net/qq_43410878/article/details/123812267)，设置私服地址、认证等信息

```xml
<servers>
	<server> 
		<id>nexus-public</id> <!-- nexus的认证id -->
		<username>admin</username> <!--nexus中的用户名密码-->
		<password>admin123</password> 
	</server>
</servers>
<profiles>
	<profile> 
        <id>nexus</id> 
        <repositories> 
            <repository> 
                <id>nexus-public</id> <!--nexus认证id 【此处的repository的id要和 <server>的id保持一致】-->
                <!--name随便-->
                <name>Nexus Release Snapshot Repository</name> 
                <!--地址是nexus中仓库组对应的地址-->
                <url>http://localhost:8081/nexus/content/groups/public/</url>
                <releases><enabled>true</enabled></releases> 
                <snapshots><enabled>true</enabled></snapshots> 
            </repository>
        </repositories> 
        <pluginRepositories> <!--插件仓库地址，各节点的含义和上面是一样的-->
            <pluginRepository> 
                <id>nexus-public</id> <!--nexus认证id 【此处的repository的id要和 <server>的id保持一致】-->
                <!--地址是nexus中仓库组对应的地址-->
                <url>http://localhost:8081/nexus/content/groups/public/</url>
                <releases><enabled>true</enabled></releases> 
                <snapshots><enabled>true</enabled></snapshots> 
            </pluginRepository> 
        </pluginRepositories> 
    </profile>
</profiles>
<activeProfiles>
    <activeProfile>yourjdk</activeProfile>
    <!-- 使私服配置生效 -->
    <activeProfile>nexus</activeProfile>
</activeProfiles>
```

> 至此，Maven项目中需要依赖时，Maven会从私服中下载

##### 8.8 Maven项目部署到私服

> - 执行 ：[mvn deploy](https://blog.csdn.net/qq_43410878/article/details/123812267) 即可将项目部署到私服对应的仓库中，此时项目中的打包方式多为jar
>     
> - 但需要提前在项目的[pom.xml](https://blog.csdn.net/qq_43410878/article/details/123812267)中配置部署私服仓库位置，如下：
>     

```xml
    ...
	<dependencies>
		.....
	</dependencies>
	
	<!-- 在项目的pom.xml中 配置私服的仓库地址，可以将项目打jar包部署到私服 -->
	<distributionManagement>
        <repository>
            <id>nexus-public</id> <!-- nexus认证id -->
            <url>http://localhost:8081/nexus/content/repositories/releases</url>
        </repository>
        <snapshotRepository>
            <id>nexus-public</id> <!-- nexus认证id -->
            <url>http://localhost:8081/nexus/content/repositories/snapshots</url>
        </snapshotRepository>
	</distributionManagement>
</project>
```

> 注意：如上的 repository的 id 依然是要和settings.xml中配置的server中的id 一致，才能通过私服的认证

#### 九、Maven分模块开发

---

> Maven 分模块开发
> 
> 1.先创建父工程，pom.xml文件中，打包方式为pom  
> 2.右键父工程创建子工程，dao工程和service工程打包方式为jar，web工程打包方式为war  
> 3.每完成一个模块后需要install，如果在IDEA中install时报错（JDK版本过低），需要在父工程的pom.xml文件中配置如下代码：

```xml
<build>
    <plugins>
        <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <groupId>org.apache.maven.plugins</groupId>
            <configuration>
                <!--<encoding-->
                <source>1.8</source>
                <target>1.8</target>
                <encoding>UTF-8</encoding>
            </configuration>
        </plugin>
    </plugins>
</build>
```