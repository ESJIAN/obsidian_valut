网盘聚合工具 [Alist 被卖](https://xiaoyi.vc/recommend-alternatives-to-alist.html)，后面新团队接手 Alist 改名「[Openlist](https://xiaoyi.vc/openlist.html)」具介绍由这个项目由 Alist 部分原贡献者联合发起，基于原版 Alist 的 Frok 项目[^1]。

现在「Openlist」已经发布测试版，主要更新有去掉原本 API，重新搭建新的开源 API、去掉 pr 新提交的恶意代码、更换新的管理员与作者、更换新的图标，以及上线了官方文档网站。

![20250619-3](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-3.png "20250619-3")

## 安装介绍

安装部署和 Alist 基本上一样，可以通过「Openlist」官方提供的一键脚本、手动安装、Docker 安装方式来部署。如果你没有服务器的话，之前也有给大家分享过：[使用免费 ClawCloud 云服务部署](https://xiaoyi.vc/clawcloud-run.html)。

用 ClawCloud 免费服务器部署「Openlist」进入 ClawCloud 点击 App Launchpad 进入页面后，点击 Create App 新建应用，然后填写下面内容：

- **Application Name：** openlist
- **Image Name：** openlistteam/openlist:beta
- **端口：** 5244
- **Public Address：** 开启

![20250619-4](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-4.png "20250619-4")

填写好后，点击右上角的 Deploy Application 按钮部署应用，等待 Public Address 地址解析，可能要 3 - 10 分钟左右。生效了会显示 Available 状态。然后复制地址就能访问了。

![20250619-5](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-5.png "20250619-5")

解析生效后，还需要查看「Openlist」的默认登录密码，在 Pod List 这里的 Logs 日志里面。

![20250619-6](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-6.png "20250619-6")

打开 Logs 日志，找到 Password is: 后面的就是登录后台的密码了，用户名是 admin。

![20250619-7](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-7.png "20250619-7")



另外如果你正准备把 Alist 转移过来，Alist 的备份是可以导入到「Openlist」里面的，这样就不用再去添加网盘和各种设置了。

![20250619-8](https://xiaoyi.vc/wp-content/uploads/2025/06/20250619-8.png "20250619-8")

## 总结

部署好「Openlist」后可以配合一些支持网盘的播放器来使用，可以看之前分享过的文章：

- [六款网盘播放器横评](https://xiaoyi.vc/comparing-6-top-cloud-media-players.html)
- [夸克 / 百度 / 天翼网盘实现订阅自动转存资源](https://xiaoyi.vc/wp-auto-save.html)
- [使用免费 ClawCloud 云服务部署网盘资源搜索转存工具：CloudSaver](https://xiaoyi.vc/cloudsaver.html)

## 下载地址

- **官方网站：**  
    https://docs.openlist.team/zh/
- **注册 ClawCloud 服务器：**  
    https://console.run.claw.cloud/signin?link=6EC9I3ODK1C3

[^1]: [网盘聚合工具 Openlist 发布，教大家免费部署！Alist 代替品！ - 小羿](https://xiaoyi.vc/openlist-team.html)


# 配置 SMB

OpenWRT路由上使用Alist挂载Win[系统](https://www.ampc8.com/)的局域网SMB共享, 官方也没有说明, 就做个简单的参考/备忘.  
共享[电脑](https://www.ampc8.com/)是局域网的Win10 LTSC2019系统, 怎么设置局域网共享这里就不多说了.  
只把Alist挂載主要设置部分截图.  
  
![Alist挂载局域网Win系统SMB共享的设置方法](https://www.ampc8.com/data/attachment/forum/202503/31/160752acn1or2inxvh18h6.jpg)  



![Alist挂载局域网Win系统SMB共享的设置方法](https://www.ampc8.com/data/attachment/forum/202503/31/160752btpc692bcux6pdpp.jpg)  
  
![Alist挂载局域网Win系统SMB共享的设置方法](https://www.ampc8.com/data/attachment/forum/202503/31/160752xn9djtjdje2xxxr3.jpg)  
  
  
效果如下, 文件夹名是挂载路径自定义显示的名字而非共享设置的名字:  
  
![Alist挂载局域网Win系统SMB共享的设置方法](https://www.ampc8.com/data/attachment/forum/202503/31/162855udpajcjf7kj679kc.jpg)