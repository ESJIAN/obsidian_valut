

官网：[calibre - 电子书管理工具 www.calibre-ebook.com/zh_CN](https://www.calibre-ebook.com/zh_CN)

​![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2023/202310101720621.png)​

## NAS 部署 Calibre-Web

```sh
version: '3'
services:
  calibre-web:
    image: linuxserver/calibre-web
    container_name: calibre-web
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Shanghai
    volumes:
      - /volume2/Media/MyBook/CalibreLibrary:/books
      - /volume1/docker/Calibre-Web/config:/config
    ports:
      - "28083:8083"
    restart: unless-stopped
```

## Calibre-Web 设置

1. 设置数据库，需要先在 config 中放好 `metadata.db`​ 文件。 ，记得勾选 `Separat Book Files from Library`​，将书籍文件和数据库文件分离。  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202411062338605.png)​
2. 修改密码和显示语言，记得拉到最后面点击保存。  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202411062323801.png)  
    3.基本设置中，启动上传  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202411062326217.png)​
3. 删除书籍，点击书籍 - 编辑数据 - 删除书籍  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202411062327978.png)  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202411062328134.png)​

​![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2023/202310101729072.png)​

## 参考

1. 通过calibre-web打造个人在线图书馆[1](https://www.sdgarden.top/archives/117/#footnotes-def-1)

---

1. # 通过calibre-web打造个人在线图书馆
    
    # 1 calibre-web简介
    
    Calibre-web 是一个为 Calibre 电子书管理软件设计的开源 Web 界面。Calibre 是一个强大的电子书管理和转换工具，它允许用户管理他们的电子书收藏，转换电子书格式，以及阅读电子书。Calibre-web 提供了一个基于 Web 的界面，使得用户可以通过浏览器访问和管理他们的 Calibre 电子书库。
    
    以下是 Calibre-web 的一些主要特点：
    
    1. **用户界面**：提供直观的 Web 界面，方便用户浏览和管理电子书。
    2. **跨平台**：可以在多种操作系统上运行，包括 Windows、macOS 和 Linux。
    3. **集成 Calibre**：与 Calibre 软件紧密集成，使用 Calibre 的数据库和功能。
    4. **多格式支持**：支持 Calibre 支持的所有电子书格式，包括 EPUB、MOBI、AZW3、PDF 等。
    5. **搜索和过滤**：提供强大的搜索和过滤功能，帮助用户快速找到想要的电子书。
    6. **电子书阅读**：内置电子书阅读器，用户可以直接在 Web 界面中阅读电子书。
    7. **自定义和扩展**：用户可以根据需要自定义界面和功能，并且支持插件扩展。
    8. **同步和备份**：可以与 Calibre 同步数据，也支持备份和恢复电子书库。
    9. **OPDS 支持**：支持 OPDS（开放出版物分发系统），允许用户通过其他 OPDS 客户端访问他们的电子书库。
    
    Calibre-web 是 Calibre 用户的一个有用补充，特别是对于那些希望在不同设备上访问和管理他们的电子书收藏的用户。通过 Calibre-web，用户可以更便捷地享受电子书阅读和管理的乐趣。
    
    # 2 calibre-web服务安装
    
    ## 2.1 直接安装exe版本
    
    - 下载安装calibre-web：[GitHub - janeczku/calibre-web: Web app for browsing, reading and downloading eBooks stored in a Calibre database](https://github.com/janeczku/calibre-web)，下载exe版本，安装后可直接运行。  
        ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202401161407355.png)​
    - 登陆[Calibre-Web | 登录](http://localhost:8083/login?next=%2Fadmin%2Fdbconfig)
    - **Username:** admin
    - **Password:** yourpassword  
        ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202401161405889.png)​
    
    ## 2.2 手动安装python版本
    
    ### 2.2.1 Installation via pip (recommended)
    
    1. Create a virtual environment for Calibre-Web to avoid conflicts with existing Python dependencies
    2. Install Calibre-Web via pip: `pip install calibreweb`​ (or `pip3`​ depending on your OS/distro)
    3. Install optional features via pip as needed, see [this page](https://github.com/janeczku/calibre-web/wiki/Dependencies-in-Calibre-Web-Linux-and-Windows) for details
    4. Start Calibre-Web by typing `cps`​
    
    *Note: Raspberry Pi OS users may encounter issues during installation. If so, please update pip (*​ _​`./venv/bin/python3 -m pip install --upgrade pip`​_​ _) and/or install cargo (_​_​`sudo apt install cargo`​_​ _) before retrying the installation._
    
    首先将pip源设置为国内，安装速度更快。[[【Python】安装及基本设置#Python pip配置国内源]]
    
    ```shell
    python.exe -m pip install --upgrade pip
    pip install virtualenv
    virtualenv calibre-web-venv
    calibre-web-venv\Scripts\activate.bat
    pip install -r requirements.txt
    pip install calibreweb
    ```
    
    ### 2.2.2 安装后启动服务
    
    方法一：进入安装目录---激活虚拟环境---启动calibre-web服务
    
    ```
    C:\Users\yaole>g:
    G:\>cd G:\yaole\Downloads\calibre-web
    G:\yaole\Downloads\calibre-web>calibre-web-venv\Scripts\activate.bat
    (calibre-web-venv) G:\yaole\Downloads\calibre-web>cps 
    ```
    
    方法二：直接进入文件夹，双击cps.exe  
    ![](https://lei-1258171996.cos.ap-guangzhou.myqcloud.com/imgs/2024/202401171613249.png)​
    
    ## 2.3 设置开机启动
    
    复制下文，保存为runCPS.vbs
    
    ```vb
    Set ws = Createobject("wscript.Shell")
    ws.run "G:\yaole\Downloads\calibre-web\calibre-web-venv\Scripts\cps.exe",vbhide
    ```
    
    编写完文件后，把文件放到cps.exe所在的目录下，右击该文件发送到桌面快捷发送：  
    然后把这个快捷方式加入开机自启中，按住win+R，输入命令shell:startup：  
    点击确认后，把桌面快捷方式拖到这个文件加即可。
    
    # 3 相关文章
    
    - [NAS 部署 Calibre-Web，搭建个人数字图书馆](https://www.sdgarden.top/archives/117/#20241209151559-hsghzal)
    - [使用 Calibre-web 在 WINDOWS10 搭建自己的漫画库 - 知乎](https://zhuanlan.zhihu.com/p/94534013)
    - [手把手教你用电脑端Calibre软件管理Calibre-web电子书库 - 极客角落 geekyes Calibre管理Calibre-web](https://www.geekyes.com/414.htm)
    - 命令行方式安装：[Windows环境下搭建网页图书馆(Calibre-Web) – Kamakoto](http://www.kamakoto.fun/calibre-windows/)
    - 视频教程：[Calibre私人书库搭建教学！藏书、漫画、听书，在线阅读+格式转换_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV12v411W7Pw/?vd_source=2acd4867545f3104b2ec4f3b962314d8)
    
    ‍ [↩](https://www.sdgarden.top/archives/117/#footnotes-ref-1)