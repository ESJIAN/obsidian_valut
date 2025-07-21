
### **简介**

Let's Markdown 是一个开源项目，旨在简化 Markdown 文档的创建、编辑和共享。快速、最小的网络编辑器，使标记编辑协作，每个人都可以访问。它提供了一套工具和功能，使 Markdown 文档的处理变得更加轻松和高效。使用[Rust](https://zhida.zhihu.com/search?content_id=233729915&content_type=Article&match_order=1&q=Rust&zhida_source=entity)和[React.js](https://zhida.zhihu.com/search?content_id=233729915&content_type=Article&match_order=1&q=React.js&zhida_source=entity)构建。有关详细信息，请参阅[GitHub仓库](https://github.com/Cveinnt/LetsMarkdown.com)[^1]。

主要特点：

- 在线编辑器：Let's Markdown 提供了一个易于使用的在线编辑器，您可以在其中创建和编辑 Markdown 文档。这个编辑器具有实时预览功能，使您可以立即查看文档的外观。

- 团队协作：Let's Markdown 允许多人同时协作编辑 Markdown 文档。您可以与团队成员一起工作，实时同步所有更改。

- 其它特性  
    
	- 类似[VSCode](https://zhida.zhihu.com/search?content_id=233729915&content_type=Article&match_order=1&q=VSCode&zhida_source=entity)的编辑器，支持命令调色板（语法高亮显示、自动完成、编辑器主题…）  
	    
	- 最少的设置，无需登录-告别恶意跟踪器和隐私侵犯  
	    
	- 使用Rust和WebAssembly构建高效后端  
	    
	- 黑暗模式（duh）  
	    
	- 表情符号支持并启用快捷方式  
	    
	- （即将推出）光标跟踪、同步滚动、下标/脚注/插入支持等  
	    

### **部署**

GitHub仓库提供了本地启动及部署的文档，大家可自行阅读下，我们此处提供docker和docker-compose 部署的方式。

- **[Docker](https://zhida.zhihu.com/search?content_id=233729915&content_type=Article&match_order=1&q=Docker&zhida_source=entity) 部署**

**拉取镜像**

```text
docker pull cveinnt/letsmarkdown
```

**启动**

```text
docker run --rm -dp 3030:3030 cveinnt/letsmarkdown
```

- **docker-compose 部署**

**编写docker-compose.yml文件**

docker-compose.yml

```text
version: "3.3"
services:
  phpmyadmin:
    image: cveinnt/letsmarkdown:latest
    ports:
        - 3030:3030
    restart: always
```

**启动**

```text
docker-compose up -d 
```

### **使用**

启动之后访问我们部署的ip和端口 http://localhost:3030

<center><b>首页</b></center>

![](https://pic3.zhimg.com/v2-dd61ab3daa33266a7d64c06f412475be_1440w.jpg)

<center><b>编辑页面</b></center>

![](https://pica.zhimg.com/v2-620440b29ffac43a95ee58b205ce4316_1440w.jpg)

- Dark Mode：主题,这儿提供了亮色和暗色两种主题

- Share Link：分享地址，可供多人同时在线编辑

- Active Users：在线编辑的用户

### **总结**

Let's Markdown 不仅为 Markdown 用户提供了一个强大的编辑平台，还通过其卓越的文档协作能力，使团队更容易地共同创造、编辑和管理 Markdown 文档。无论是您是个人作者还是团队中的一员，都值得一试 Let's Markdown，以提高文档协作的效率和质量。

[^1]: [(20 封私信 / 5 条消息) 提升 Markdown 文档协作：Let's Markdown介绍与部署 - 知乎](https://zhuanlan.zhihu.com/p/655206254)
