## **基本概念**

旁路由是一种网络配置方式，它在主路由器旁边接入一台额外的路由设备，专门负责特定的网络任务，如代理、广告过滤等。这台设备不直接连接互联网，而是通过主路由器访问网络。旁路由的工作原理是在主旁路由构成的网络架构中，分担一部分路由器的功能，从而实现网络带宽的合理分配利用，并提供更强的扩展性。

## **应用场景**

旁路由的应用场景,，以下是问GPT，回答的：

- **网络覆盖扩展**：在大面积房屋或多层建筑中，旁路由可以通过设置在家中的不同位置，形成一个覆盖更广的Wi-Fi网络，消除信号盲区。
- **提升网络性能**：通过设置旁路由，用户可以对各类设备的带宽进行详细管理，优先保障重要设备的网络速度，减少视频缓冲、游戏延迟等问题。[**网络安全**](https://cloud.tencent.com/product/ddos?from_column=20065&from=20065)**防护**：旁路由可以单独配置VPN、[入侵检测](https://cloud.tencent.com/product/cwp?from_column=20065&from=20065)系统等增强安全功能，为家庭网络提供额外的防护层。
- **访问控制与内容过滤**：旁路由可以方便地设置访问控制，限制特定设备在特定时间段内上网，或是对特定网站进行访问限制，防止家庭成员接触到不良网站。
- **游戏与流媒体优化**：旁路由可以为游戏主机、流媒体设备分配更高的优先级，确保在网络高负荷时，依然能够流畅地进行游戏或者观看高清视频。
- **实验与学习平台**：对于网络爱好者以及技术人员，旁路由提供了一个极好的实验与学习平台，用户可以在旁路由上尝试不同的操作系统、配置高级的网络功能。

不过我想说，以上功能，其实在主路由上一样可以做，比如安全防护，访问控制之类的。我很赞同Eason Yang的观点，**只有你不好动主路由，或者主路由不支持改动的情况下，才考虑使用旁路由**。否则其实旁路由我感觉没多大意义。

## **配置组网**

旁路由的组网图对应如下

![](https://developer.qcloudimg.com/http-save/yehe-1160092/629697a94227479b2c3a94157e8e8746.png)

主路由的lan口连上旁路由的lan口，将旁路由的lan地址改成和主路由一个网段，地址不一样即可。终端不管是通过有线，还是无线连接，不管是连主路由，还是旁路由，都可以。根据终端网关和dns的不一样，走的流量不一样。这里我用红色的数字圈标记了1，2，3，其中1表示主路由，2表示旁路由，3表示终端设备。根据终端设备在哪儿指定网关和dns，有如下的三种配置场景，具体怎么配置就不细说了。

**方案一：主路由开启****DHCP****，旁路由关闭DHCP（非全局）**

> 这里非全局的意思是不是所有设备都过旁路由

1. 修改旁路由的管理地址网段：确保旁路由的管理地址与主路由处于同一网段，便于管理。例如，如果主路由的IP是192.168.1.1，那么旁路由可以设置为192.168.1.x，其中x是2到254之间的一个未使用的地址。
2. 关闭IPV6和DHCP服务：在旁路由的设置中，DHCP服务应该设置为忽略此接口。
3. 防火墙设置：在防火墙设置中，确保打开了IP动态伪装功能，这可以解决一些路由器会校验数据包的IP和MAC地址的对应关系的问题。
4. 终端设置：需要使用旁路由的设备，需要手动设置设备的网关和DNS指向旁路由的IP地址。

**方案二：主路由开启DHCP，旁路由关闭DHCP（全局）**

> 全局是只所有设备都过旁路由

1. 主路由设置：将主路由的DHCP的默认网关修改为旁路由的IP，DNS[服务器](https://cloud.tencent.com/product/cvm/?from_column=20065&from=20065)也修改为旁路由的IP。
2. 旁路由设置：与方案一相同，但所有设备的网络流量都将通过旁路由。

**方案三：主路由关闭DHCP，旁路由开启DHCP（全局）**

1. 主路由设置：关闭主路由的DHCP服务，设置网关和DNS为旁路由的IP。
2. 旁路由设置：开启DHCP服务，并设置网关为主路由的IP。

注意，很多网上的指导，有这样另外在配置旁路由时，可能需要在旁路由的防火墙自定义规则中添加以下规则来解决IP地址和MAC地址对应关系的问题：

javascript

```javascript
iptables -t nat -I POSTROUTING -o 网卡名 -j MASQUERADE
```

这条规则的意思是执行SNAT功能，把数据包的源IP改成旁路由的IP，无论该数据包是否会经过插件处理。这个参考实际情况来看

## **典型案例配置说明：通过旁路由管理上网策略**

我这里用ikuai做主路由，OpenWrt做旁路由，并在OpenWrt上配置了OC猫进行策略管控。ikuai的lan口连接OpenWrt的Lan口，具体连线如下，

![](https://developer.qcloudimg.com/http-save/yehe-1160092/e43193fd8ccf77d6f2497caf004b64dd.png)

ikuai主路由，管理地址10.20.30.1

OpenWrt作为旁路由，10.20.30.2

针对以上的几种方案，分别进行说明验证：

### **默认情况下**

主路由正常下发dhpc

![](https://developer.qcloudimg.com/http-save/yehe-1160092/cf426fb731145c91bb88075cda03a1ca.png)

旁路由关闭dhcp，默认走主路由出去。终端的配置和具体表现如下：

![](https://developer.qcloudimg.com/http-save/yehe-1160092/6835ef2d1eaac714b7cf2daee12fbaf5.png)

### **方案1**

手动指定网关 Windows终端侧配置

![](https://developer.qcloudimg.com/http-save/yehe-1160092/bdcde1842aa84691d09ed7da8140419d.png)

实际上网的表现：

![](https://developer.qcloudimg.com/http-save/yehe-1160092/a810330bdf0ef5ae0f7dbf33202e6aff.png)

### **方案2**

主路由下发dhcp和dns，旁路由不参与。主路由ikuai配置：

![](https://developer.qcloudimg.com/http-save/yehe-1160092/b0fc0dd7ea1978aca48d176577118b5c.png)

旁路由OpenWrt Lan口配置

![](https://developer.qcloudimg.com/http-save/yehe-1160092/fba4b81aade88ce9a4aab5946c1d8ea3.png)

终端windows上，可以看到下发的网关和dns，以及上网情况。

![](https://developer.qcloudimg.com/http-save/yehe-1160092/7610b3eed9551314f4b6f36e17704a3f.png)

### **方案3**

主路由不参与，旁路由下发网关和dns。ikuai 上dhcp配置

![](https://developer.qcloudimg.com/http-save/yehe-1160092/543df3d3cf0025d8e3f12a4ed5addf5c.png)

旁路由OpenWrt上的配置

![](https://developer.qcloudimg.com/http-save/yehe-1160092/ee9f884419d37ec53b8bf57d484028db.png)

windows终端配置以及上网情况。

![](https://developer.qcloudimg.com/http-save/yehe-1160092/b655da5074916859e631f379488837f3.png)

## **总结**

使用旁路由，就是局域网内一个代理的作用。通过旁路由可以实现一些额外的功能，不过这个前面也说了，这些都可以在主路由去做，只有在不想改变现有网络形态的情况下，才适合用旁路由。但是实际的过程中，对网络需要有些基本的了解，什么二层、三层，网关，dns，arp等，否则可能得不偿失。 - END -