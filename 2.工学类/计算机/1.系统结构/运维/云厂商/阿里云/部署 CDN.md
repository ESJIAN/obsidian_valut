# 



# 目录









# **1. 开通CDN服务**


1.登录[阿里云CDN平台](https://www.aliyun.com/product/cdn?spm=a2c4g.11186623.0.0.43ed3e06qNaoxe)

2.单击**立即开通**。

3.**计费类型**默认按使用流量计费，并选中**CDN服务协议**。CDN产品定价，请参见[CDN定价](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.10.1b444ee22Dxy8y#/cdn/detail)

![CDN开通图片](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/4968133761/p548797.png)

4.单击**立即开通**。成功开通CDN服务后，您可以在[阿里云CDN平台](https://www.aliyun.com/product/cdn)单击**管理控制台**，进入CDN管理控制台界面。


# 2. 添加加速域名

## 2.1. 准备工作

1. 您已经拥有稳定运行的源站（即业务服务器或OSS）。如果没有源站，请参见[通过控制台使用ECS实例](https://help.aliyun.com/zh/ecs/getting-started/create-and-manage-an-ecs-instance-by-using-the-ecs-console)或[创建存储空间](https://help.aliyun.com/zh/oss/user-guide/create-a-bucket-4)创建。
    
2. 您已经拥有用于加速的域名。
    
    当目标加速区域为**仅中国内地**或**全球**时，域名需要完成备案。如果域名未备案，您可以登录[阿里云ICP代备案管理系统](https://beian.aliyun.com/pcContainer/myorder)完成备案。
    
3. 您已经开通了CDN服务。如果未开通，请参见[开通CDN服务](https://help.aliyun.com/zh/cdn/activate-alibaba-cloud-cdn#task-187531)进行开通。
    

## 2.2. 配置域名信息

1. 登录[CDN控制台](https://cdn.console.aliyun.com/)。
    
2. 在左侧导航栏，单击**域名管理**。
    
3. 单击**添加域名**，在**域名信息**页面，配置**加速区域**、**加速域名**和**业务类型**，其他参数均保持默认。
    
    ![china](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/9581397861/p94748.png)
    


|          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **参数**   | **说明**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **加速区域** | - **仅中国内地**：所有用户访问均会调度至中国内地就近节点提供加速服务（海外地区和中国香港、中国澳门、中国台湾地区的访问流量将会被调度至华东电信的CDN节点）。<br>    <br>- **全球**：所有用户访问将会择优调度至全球就近节点提供服务。<br>    <br>- **全球（不包含中国内地）**：非中国内地用户访问会被调度至就近节点服务；中国内地用户访问会被调度至日本、新加坡和中国香港的CDN加速节点服务。<br>    <br><br>**重要**<br><br>- 加速区域为**仅中国内地**或**全球**时，加速域名要求**必须备案**，您可以登录[阿里云ICP代备案管理系统](https://beian.aliyun.com/pcContainer/myorder)完成备案。由于工信部备案系统存在数据延迟，刚完成备案的域名请在8小时后再配置。<br>    <br>- 加速区域为**全球（不包含中国内地）**时，对加速域名**备案不作要求**。<br>    <br>- 不同的加速区域价格不一样，请根据您的实际需求选择。计费详情，请参见[CDN定价](https://www.aliyun.com/price/product?spm=a2c4g.11186623.2.10.1b444ee22Dxy8y#/cdn/detail)。                                                                                                                                                                             |
| **加速域名** | 填写[加速域名](https://help.aliyun.com/zh/cdn/product-overview/terms#section-obn-stb-p2b)名称，填写要求请参见[使用限制](https://help.aliyun.com/zh/cdn/product-overview/limits)。<br><br>**说明**<br><br>首次在CDN控制台添加一个新域名时，需要完成域名归属权验证。具体操作，请参见[验证域名归属权](https://help.aliyun.com/zh/cdn/verify-domain-name-ownership#task-2511469)。如果之前已经验证通过根域名的归属权，请忽略。                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **业务类型** | - [图片小文件](https://help.aliyun.com/zh/cdn/product-overview/scenarios#section-mnp-tw0-fz3)：适用于电商类、网站类、游戏图片类等小型的静态资源加速场景。<br>    <br>- [大文件下载](https://help.aliyun.com/zh/cdn/product-overview/scenarios#section-9n4-tgj-a76)：适用于大于20 MB的静态文件加速场景。<br>    <br>- [视音频点播](https://help.aliyun.com/zh/cdn/product-overview/scenarios#section-zuc-giw-6og)：适用于音频或视频文件加速场景。<br>    <br>- [全站加速](https://help.aliyun.com/zh/edge-security-acceleration/dcdn/product-overview/what-is-dcdn#concept-hdt-3t2-xdb)：适用于含有大量动态和静态内容混合，且多为动态资源请求的加速场景。<br>    <br>    当业务类型选择**ESA边缘安全加速**时，您需根据界面提示，前往全站加速控制台添加域名并进行相关配置。具体操作，请参见[添加服务域名](https://help.aliyun.com/zh/edge-security-acceleration/dcdn/getting-started/add-a-domain-name#task-alv-1fk-xdb)。<br>    <br><br>**说明**<br><br>配置后业务类型不可修改。 |


## 2.2. 配置源站
>**注意**：这里非常容易犯错，你可能配置为源站点为 stalab.fun，但是在 CNAME 解析中的主机记录前缀中却写了 www ，这样的 CNAME 解析是错误的，会造成 CNAME 验证不生效

1. 完成域名业务信息配置后，在**源站信息**区域单击**新增源站信息**。
    
2. 在**新增源站信息**对话框中，选择源站的类型，并填写源站地址，其他参数均保持默认。
    
    ![配置源站信息](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3869438171/p278368.png)
    
| **参数**   | **说明**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **源站信息** | 选择[源站](https://help.aliyun.com/zh/cdn/product-overview/terms#section-fce-wpt-1bf)的类型，并填写源站地址。源站类型支持**OSS域名**、**IP**、**源站域名**和**函数计算域名**。此处以**OSS域名**举例说明，其他类型的源站配置，详情请参见[配置源站](https://help.aliyun.com/zh/cdn/user-guide/configure-an-origin-server)。<br><br>**源站信息**选择**OSS域名**，并在下方的**域名**列表中选择同账号下的OSS Bucket，或选择输入阿里云OSS Bucket的外网域名作为源站（不支持OSS内网域名作为源站），示例值为`***.oss-cn-hangzhou.aliyuncs.com`。                                                                                                                           |
| **优先级**  | 源站优先级支持设置主备，主优先级大于备优先级。用户请求通过阿里云CDN回源时，会优先回源到优先级为主的源站地址。主源站出现故障的情况下，将会回源到备源站。源站优先级的取值范围为0~127，数值越小，优先级越高。主源站的优先级默认值为20，备源站的优先级默认值为30。如需配置其他值，请[填写信息](https://page.aliyun.com/form/act2017566026/index.htm)申请。<br><br>例如，有A、B两个源站，A源站的优先级为主，B源站的优先级为备，则用户请求通过阿里云CDN回源时会优先回源到A源站，如果A源站出现故障，将会回源到B源站，当A源站恢复正常后会从B源站切换回A源站。                                                                                                                                                                                                        |
| **权重**   | 当多个源站的优先级相同时，阿里云CDN会按照源站的权重分配用户请求回源到不同源站的比例，实现按权重的负载均衡。您可以根据业务需求，自行设置权重值。<br><br>- 取值范围：1~100，数值越大，源站分配到的用户请求比例越高。<br>    <br>- 默认值：10。<br>    <br><br>例如：有A、B两个源站，两个源站的优先级都是主，A源站的权重为80，B源站的权重为20，则用户请求将会按照8:2的比例在A、B两个源站之间分配。                                                                                                                                                                                                                                                                                                |
| **端口**   | 表示CDN节点回到源站哪个端口请求资源。默认为80，根据您源站的支持情况，可自定义设置回源端口，允许设置的端口范围为1~65535。<br><br>- 默认值：80。<br>    <br>- 端口值为443时，以HTTPS协议回源；80或其他自定义端口，以HTTP协议回源。<br>    <br><br>**说明**<br><br>- 如果需要以HTTPS协议回源到其他自定义端口，请参见[配置回源协议](https://help.aliyun.com/zh/cdn/user-guide/configure-the-origin-protocol-policy#task-261642)。<br>    <br>- 如果配置了**回源协议**功能（默认为关闭状态），这里配置的端口会失效。关闭回源协议的方法，请参见[配置回源协议](https://help.aliyun.com/zh/cdn/user-guide/configure-the-origin-protocol-policy#task-261642)。<br>    <br>- 当源站选择OSS域名时，回源端口是否支持自定义端口，取决于OSS产品。 |


3. 配置完成后，单击**确定**。




![1743180335338.png](https://www.helloimg.com/i/2025/03/29/67e6d1c75f954.png)
<center>图：楼主本人的设置(已打码服务器真实IPV4地址)</center>





## 2.4. 完成域名审核

1. 完成源站配置后，阅读并勾选合规承诺，单击**下一步**。
    
2. 页面跳转至**推荐配置**页面，请根据实际需要配置缓存过期时间、忽略参数、页面优化、Range回源、Gzip压缩等基础配置，有效提升CDN的缓存命中率和访问性能，请参见[推荐配置（可选）](https://help.aliyun.com/zh/cdn/configure-system-recommended-features)。
    
    您可以单击页面下方的**一键配置**按钮，CDN会快速帮您完成相关配置；您也可以单击**返回域名管理**在域名列表页的操作栏单击**推荐配置**再次进入。
    
3. 等待人工审核。
    
    审核通过后，域名状态显示为**正常运行**，表示添加成功。
    
    ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3869438171/p810612.png)
    
    
    - 如果您的加速域名无需人工审核，将直接进入下一个配置环节，您可根据实际业务需求，完成推荐配置。
        
    - 新增域名的生效时长通常在10分钟以内，偶尔会因为系统波动延长到30分钟，如果超过30分钟仍未完成域名新增，那么将会有阿里云的工程师介入处理。
        
    

# 3. 配置CNAME

[配置CNAME](https://help.aliyun.com/zh/cdn/add-a-cname-record-for-a-domain-name?spm=a2c4g.11186623.0.0.7d35171aWqIkYs#task-187531)：添加域名后，阿里云CDN会为您分配对应的CNAME域名，您需要完成CNAME配置，CDN服务才能生效。


同时，建议您在[配置CNAME](https://help.aliyun.com/zh/cdn/add-a-cname-record-for-a-domain-name#task-187531)前，完成以下操作：

- [推荐配置（可选）](https://help.aliyun.com/zh/cdn/configure-system-recommended-features#task-187634)：为域名配置缓存过期时间、带宽封顶等功能，提升CDN的缓存命中率、安全性和访问性能。
    
- [模拟访问测试（可选）](https://help.aliyun.com/zh/cdn/test-whether-a-domain-name-is-accessible#task-2520721)：保证DNS解析顺利切换而不影响现有业务。

## 3.1. **准备工作**

1. 您已开通了CDN服务。如果未开通，请参见[开通CDN服务](https://help.aliyun.com/zh/cdn/activate-alibaba-cloud-cdn#task-187531)进行开通。
    
2. 您已成功添加了加速域名。如果没有添加，请参见[添加加速域名](https://help.aliyun.com/zh/cdn/add-a-domain-name)进行添加。
    


    

## **3.2. 获取加速域名的CNAME域名**

前往阿里云CDN控制台的[域名管理列表](https://cdn.console.aliyun.com/domain/list)，复制加速域名对应的CNAME记录值，用于填写到配置CNAME域名解析条目中的记录值当中。

![域名管理](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/0740719261/p66555.png)




## **3.3. 配置CNAME域名解析**

不同DNS服务商配置CNAME域名解析的方法不同，请以实际情况为准。本文以阿里云和腾讯云两大DNS服务商为例。



- 配置泛域名（如*.aliyundoc.com）解析为CNAME域名时，此泛域名的次级域名（如example.aliyundoc.com）都将支持加速功能，但不支持加速泛域名的三级域名，更多信息请参考：[泛域名加速](https://help.aliyun.com/zh/cdn/does-alibaba-cloud-cdn-support-wildcard-domain-names)。
    
- 同一个域名解析服务商下，域名解析存在冲突规则。具体冲突和解决方法，请参见[解析记录冲突规则](https://help.aliyun.com/zh/dns/dns-record-conflict-rules)和[常见问题](https://help.aliyun.com/zh/cdn/add-a-cname-record-for-a-domain-name?spm=a2c4g.11186623.0.0.7d35171aWqIkYs#section-u25-nhf-h9n)。
    
- 由于阿里云CDN校验域名的DNS解析记录的服务器部署在中国内地。如果您对域名做了分区域DNS解析配置，例如仅对域名的中国内地以外区域（中国香港、中国澳门、中国台湾、其他国家和地区）配置了阿里云CDN的CNAME地址，校验服务器将无法解析到该CNAME地址，且在CDN控制台该域名的CNAME状态会显示为**待配置**，这种情况不影响CDN的加速服务。
    
- 阿里云CDN、全站加速DCDN、直播以及点播产品的CNAME域名仅可以作为阿里云CDN的调度解析使用，对于恶意使用CNAME域名的行为，阿里云有权清退对应的域名和账号。
    




如果您的DNS服务商是阿里云，您可以根据以下步骤完成CNAME配置。

1. 使用**加速域名所在的阿里云账号**，登录[云解析DNS控制台](https://dns.console.aliyun.com/)。
    
2. **可选：**（非阿里云注册的域名）在云解析控制台添加域名。
    
    **说明**
    
    非阿里云注册的域名，需要先在云解析控制台完成域名添加，才能进行域名解析设置。具体操作，请参见[添加域名](https://help.aliyun.com/zh/dns/domain-management)。如果您的域名是在阿里云注册的，请跳过该步骤。
    
3. 在**域名解析**页面，找到您的域名，在域名右侧单击**解析设置**。
    
4. 单击**添加记录**，添加CNAME记录。
    
    **说明**：精准域名的CNAME解析优先级大于泛域名的CNAME解析。如果您的加速域名为泛域名，且主机记录设置为星号（*）时，需删除泛域名下所有已生效的二级域名的解析记录。
    
| **参数**     | **填写样例**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | **说明**                                                                                                                                                                                                                                                                           |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **记录类型**   | CNAME                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 选择CNAME。                                                                                                                                                                                                                                                                         |
| **主机记录**   | - **子域名示例：**<br>    <br>    - 加速域名为`example.aliyundoc.com`，主机记录为`example`。<br>        <br>    - 加速域名为`www.example.aliyundoc.com`，主机记录为`www.example`。<br>        <br>- **泛域名示例：**<br>    <br>    - 加速域名为`.aliyundoc.com`，主机记录为`*`。<br>        <br>    - 加速域名为`*.example.aliyundoc.com`，主机记录为`*.example`。<br>        <br>- **根域名示例**：根域名为`aliyundoc.com`且配置加速域名为`aliyundoc.com`时，主机记录填写`@`。<br>    <br><br>**说明**<br><br>域名解析设置是针对您注册的域名（如aliyundoc.com）或域名的左侧部分进行解析设置。配置主机记录时，您仅需要填写要解析的部分（如解析**example**.aliyundoc.com时填写example）。 | - 加速域名为子域名的情况下，主机记录为子域名的前缀。<br>    <br>- 加速域名为泛域名的情况下，主机记录为`*`。<br>    <br>- 加速域名为根域名自身时，主机记录为`@`。<br>    <br><br>**说明**<br><br>关于子域名的解释，您可以参考[域名基本概念](https://help.aliyun.com/zh/dns/basic-concepts)。                                                                           |
| **解析请求来源** | 推荐保持默认                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 默认线路。                                                                                                                                                                                                                                                                            |
| **记录值**    | `www.example.com.w.kunlunsl.com`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 输入加速域名对应的CNAME记录值。<br><br>**说明**<br><br>一级域名（如example.aliyundoc.com）和二级域名（如www.example.aliyundoc.com）对应的CNAME值不同。如果您要加速二级域名，需要将二级域名也添加到CDN上并解析到对应的CNAME记录值，或者在CDN上添加泛域名，泛域名的CNAME可以被二级域名使用。添加泛域名或二级域名，请参见[添加加速域名](https://help.aliyun.com/zh/cdn/add-a-domain-name#task-678836)。 |
| **TTL**    | 推荐保持默认                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | TTL为缓存时间，数值越小，修改记录后各地生效时间越快，默认为10分钟。                                                                                                                                                                                                                                             |
	
    
5. 单击**确认**，完成添加。







![1743181375972.png](https://www.helloimg.com/i/2025/03/29/67e6d5e69e988.png)
<center>图：楼主的CNAME配置</center>





![1743181126914.png](https://www.helloimg.com/i/2025/03/29/67e6d4df66691.png)

<center>图：必须要注意的CNAME配置原则</center>




此处我是填写的源站信息类型是 IPV4，因为我想要用户输入 www.stalab.fun 时候先访问的是 CDN 缓存服务器， 等缓存未命中在访问真实的源服务器 IPV4地址，此页面设置可以用下图解释

![1743180439364.png](https://www.helloimg.com/i/2025/03/29/67e6d2306207b.png)


所以在 `全站加速CDN/域名管理/配置` 这个页面中我们把加速域名 `stalab.fun.w.kunlunpi.com` 与服务器实际IPV4地址关联了起来，而在云解析DNS添加的CNAME记录这么一个行为则是将客户端访问的`www.stalab.fun`与CDN转发入口域名`www.stalab.fun.w.kunlunpi.com`关联了起来。

用户访问`www.stalab.fun`首先访问的是`www.stalab.fun.w.kunlunpi.c`CDN服务器上对真实服务器网页的缓存，如果该如果该CDN服务器有真实服务器网页的缓存的话，会直接将页面返回给客户端。如果没有目标真实服务器的缓存，则流量会被`www.stalab.fun.w.kunlunpi.c`的CDN服务器转发给真实服务器，由真实服务器发送给客户端。



| CNAME配置错误案例1 | ![1743181270381.png](https://www.helloimg.com/i/2025/03/29/67e6d57060cb3.png) |
| -----------: | ----------------------------------------------------------------------------- |
|              |                                                                               |

## **3.4. 验证CNAME配置是否生效**

- **方法一：一键验证**
    
    1. 前往阿里云CDN控制台的[域名管理列表](https://cdn.console.aliyun.com/domain/list)。
        
    2. 选择目标域名，将鼠标指向加速域名的**CNAME状态**处，状态为**已配置**时，则表示CNAME配置已生效。![image.png](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/0106463071/p751435.png)
        
        **说明**
        
        云解析DNS上新增CNAME记录实时生效，修改CNAME记录在10分钟后生效（具体生效时间长短取决于域名DNS解析配置的TTL时长，10分钟为TTL的默认时长），在此期间控制台中状态可能仍显示**待配置**，请忽略。
        
- **方法二：通过nslookup命令验证**
    
    1. 打开cmd程序（Windows）、终端（macOS/Linux）。
        
    2. 输入nslookup -type=CNAME **加速域名**，如果返回的解析结果和CDN控制台上该加速域名的CNAME值一致，则表示CDN加速已经生效。例如：
        
        ```plaintext
        nslookup -type=CNAME www.example.com
        ```
        
        ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/9493449371/p795364.png)
        

## 3.5. 注意事项

- 如果加速域名已经配置了A记录，您可以先通过[模拟访问测试](https://help.aliyun.com/zh/cdn/test-whether-a-domain-name-is-accessible)来验证CNAME记录是否能正常的映射，然后直接将当前A记录修改为对应的CNAME记录。注意需要在业务流量低谷时进行操作。
    
- 如果您已经完成CNAME配置，但是在访问的时候页面出现页面重定向次数太多的问题，建议您参考这篇文档介绍的方法进行解决：[CDN加速后提示重定向的次数过多](https://help.aliyun.com/zh/cdn/too-many-redirects-occur-after-my-domain-name-is-accelerated-by-alibaba-cloud-cdn)。
    
- 如果您已经完成CNAME配置，但是访问时页面提示使用了不受支持的协议，建议您参考这篇文档进行HTTPS证书的配置然后再去访问：[配置HTTPS证书](https://help.aliyun.com/zh/cdn/user-guide/configure-an-ssl-certificate)。



## 3.6. 常见问题

- [如何获取CNAME域名？](https://help.aliyun.com/zh/cdn/how-to-obtain-a-cname-domain-name)
    
- [CNAME记录和A记录冲突怎么办？](https://help.aliyun.com/zh/cdn/dns-records-conflict-with-each-other#concept-2093797)
    
- [CNAME解析未生效怎么办？](https://help.aliyun.com/zh/cdn/cname-record-does-not-take-effect#concept-2093802)
    
- [如何查看CDN节点是否生效？](https://help.aliyun.com/zh/cdn/ee86e4)
    
- [如何使用CDN加速OSS资源？](https://help.aliyun.com/zh/cdn/use-cases/accelerate-the-retrieval-of-resources-from-an-oss-bucket-in-the-alibaba-cloud-cdn-console)
    
- [CDN加速后提示重定向的次数过多解决方案](https://help.aliyun.com/zh/cdn/too-many-redirects-occur-after-my-domain-name-is-accelerated-by-alibaba-cloud-cdn)










## 3.7. **拓展阅读**

### 3.7.1. **CNAME记录**

CNAME记录，即Canonical Name Record，直译成中文就是"规范的名称记录"。其作用是将一个域名映射到另一个域名。更多CNAME记录的解释和使用请参见：[CNAME记录简介](https://help.aliyun.com/zh/cdn/what-is-a-dns-cname-record)。

### 3.7.2. **加速原理**

添加加速域名之后，CDN将为您提供一个CNAME域名。通过DNS解析，此CNAME域名将直接指向CDN服务器。为了实现加速效果，您需要将加速域名（例如example.aliyundoc.com）原本的DNS记录更新为指向系统分配的CNAME域名（例如example.aliyundoc.com.w.kunlunle.com）。当用户访问加速域名时，请求将自动被转发至最近的CDN节点，从而提升访问速度，详细加速原理请见：[加速原理](https://help.aliyun.com/zh/cdn/product-overview/what-is-alibaba-cloud-cdn#section-wql-p2l-56f)。

### 3.7.3. **域名解析**

域名解析是用于将域名（如example.aliyundoc.com）解析为客户端实际连接的IP地址的服务，更多域名解析内容请参见：[什么是域名解析？](https://help.aliyun.com/zh/cdn/what-is-dns-resolution#trouble-2323389)
# **4. 配置HTTPS证书**

CDN支持HTTPS加速服务，您可以上传自定义证书或将已经托管在阿里云SSL证书服务的证书部署至CDN平台，启用HTTPS加速服务，实现全网数据加密传输。本文介绍配置和更新HTTPS证书的操作方法。前提条件

**前提条件**

- 已经拥有HTTPS证书。如果需要购买证书，您可以在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)
    
- 自有证书需满足证书格式要求。详细信息，请参见[证书格式说明](https://help.aliyun.com/zh/cdn/user-guide/certificate-formats)
    

**背景信息**

根据认证级别不同，可分为多种类型的证书，不同类型证书的安全性和适用的网站类型不同。详细信息，请参见[支持选购的证书类型](https://help.aliyun.com/zh/ssl-certificate/product-overview/what-is-certificate-management-service)。

证书的格式可以进行转换。详细信息，请参见[证书格式转换方式](https://help.aliyun.com/zh/cdn/user-guide/certificate-formats)。

**说明**

- CRT后缀文件是Certificate的简称，可能是PEM编码格式，也可能是DER编码格式。进行证书格式转换前请仔细确认您的证书格式是否需要转换。
    
- PEM（Privacy Enhanced Mail）一般为文本格式，以 “-----BEGIN ***-----”开头，以 “-----END ***-----结尾”，中间的内容是Base64编码。这种格式可以保存证书和私钥，为了区分证书与私钥，一般会将PEM格式的私钥后缀改为.key。
    






## 4.1. **配置或更新HTTPS证书**

HTTPS功能为增值服务，开启HTTPS将产生HTTPS请求数计费，该费用单独按量计费，不包含在CDN流量包内。HTTPS计费介绍，请参见[静态HTTPS请求数](https://help.aliyun.com/zh/cdn/billing-of-value-added-services-1)

1.登录[CDN控制台](https://cdn.console.aliyun.com/)

2.在左侧导航栏，单击**域名管理**。

3.在**域名管理**页面，单击目标域名对应的**管理**。

4.在指定域名的左侧导航栏，单击**HTTPS配置**。

5.在**HTTPS证书**区域，单击**修改配置**。

6.在**HTTPS设置**界面，打开**HTTPS安全加速**开关。

当您打开**HTTPS安全加速**开关时，系统弹出确认开启HTTPS界面，该操作单独计费，您可以根据所需选择是否开启。HTTPS计费标准，请参见[静态HTTPS请求数](https://help.aliyun.com/zh/cdn/billing-of-value-added-services-1)

7.配置证书相关参数。

**说明**

- 阿里云CDN默认支持的TLS加密算法，请参见[CDN默认支持的TLS加密算法](https://help.aliyun.com/zh/cdn/user-guide/default-tls-encryption-algorithms)
    
- 有关HTTPS证书的常见问题，请参见[HTTPS相关常见问题](https://help.aliyun.com/zh/cdn/user-guide/faq-about-https)
    




|   |   |
|---|---|
|**参数**|**说明**|
|证书来源|**证书来源**包含以下四种，四种证书之间可以相互切换。<br><br>**云盾（SSL）证书中心**<br><br>您可以在[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas)<br><br>**自定义上传（证书+私钥）**<br><br>如果证书列表中无当前适配的证书，您可以上传自定义证书。您需要在设置证书名称后，上传证书内容和私钥，该证书将在阿里云SSL证书服务中保存。您可以在[我的证书](https://yundun.console.aliyun.com/?spm=5176.2020520110.all.12.16df56a1u1IhI6&p=cas#/cas/home)<br><br>**说明**<br><br>上传该类型的证书时如果提示证书重复，您可以修改证书名称后再上传。<br><br>**自定义上传（证书）**[CSR生成工具](https://help.aliyun.com/document_detail/149568.html)<br><br>**免费证书**<br><br>免费证书只适用于HTTPS安全加速业务，因此您无法在阿里云SSL证书控制台管理该证书，也无法查看到公钥和私钥。免费证书的申请和续签规则请参见控制台界面提示。<br><br>- 免费证书签发：1~2个工作日，期间您可以重新选择上传自定义证书或云盾证书。<br>    <br><br>**说明**<br><br>免费证书签发：1~2个工作日，期间您可以重新选择上传自定义证书或云盾证书。<br><br>- 免费证书签发：1~2个工作日，期间您可以重新选择上传自定义证书或云盾证书。|
|证书名称|当**证书来源**为以下两种时，需要配置证书名称。<br><br>- **云盾（SSL）证书中心**<br>    <br>- **自定义上传（证书+私钥）**|
|证书（公钥）|当**证书来源**为以下两种时，需要配置**证书（公钥）**。配置方法参见**证书（公钥）**输入框下方的**pem编码参考样例。**<br><br>- **自定义上传（证书+私钥）**<br>    <br>- 自定义上传（证书）|
|私钥|当**证书来源**选择**自定义上传（证书+私钥）**时，需要配置**私钥**。配置方法参见私钥输入框下方的**pem编码参考样例**。|

8.单击**确定**，完成配置。







## **4.2. 验证HTTPS配置是否生效**

更新HTTPS证书1分钟后将全网生效。您可以使用HTTPS方式访问资源，如果浏览器中出现锁的HTTPS标识，表示HTTPS安全加速已生效。

![|737](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/7152490461/p378882.png)

## **4.3. 关闭HTTPS安全加速**

如果您不再使用HTTPS安全加速功能，可随时在CDN控制台关闭HTTPS安全加速。关闭HTTPS安全加速实时生效，关闭后您将无法继续使用HTTPS安全加速功能。




# 5. 参考链接
- [如何开通和配置CDN服务_云·原生建站-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/cnw/user-guide/activate-and-configure-cdn)
- [快速配置加速域名，方便接入CDN加速服务-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/cdn/add-a-domain-name?spm=a2c4g.11186623.0.0.4c512c179CE2Aj)
- [通过配置CNAME域名实现网站加速-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/cdn/add-a-cname-record-for-a-domain-name?spm=a2c4g.11186623.0.0.7d35171aWqIkYs#task-187531)
- [cdn配置（超详细+图解+原理）-CSDN博客](https://blog.csdn.net/ziqibit/article/details/130825005)
- [【CDN】快速了解CDN是什么？以及工作原理和应用场景-CSDN博客](https://blog.csdn.net/weixin_43431218/article/details/144678242?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-144678242-blog-130825005.235^v43^pc_blog_bottom_relevance_base6&spm=1001.2101.3001.4242.2&utm_relevant_index=4)
