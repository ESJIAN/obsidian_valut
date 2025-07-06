## 1：先创建一个挂载emqx的目录

## 2：docker拉去emqx

```bash
docker pull emqx/emqx:latest
```

### 2-1：先启动一次eqmx，然后停止，删除容器

```bash
docker run -d --name emqx --privileged=true -p 1883:1883 -p 8883:8883 -p 8083:8083 -p 8084:8084 -p 8081:8081 -p 18083:18083  emqx/emqx:latest
```

### 以下是每一个端口对应的作用和协议，需要用上那个，就可以开启那个

```bash
2025-01-01 09:32:24 WARNING: NOTE: Use the same cookie for all nodes in the cluster.
2025-01-01 09:32:25 EMQX_RPC__PORT_DISCOVERY [rpc.port_discovery]: manual
2025-01-01 09:32:25 EMQX_NODE__NAME [node.name]: emqx@172.17.0.2
2025-01-01 09:32:27 Listener ssl:default on 0.0.0.0:8883 started.
2025-01-01 09:32:27 Listener tcp:default on 0.0.0.0:1883 started.
2025-01-01 09:32:27 Listener ws:default on 0.0.0.0:8083 started.
2025-01-01 09:32:27 Listener wss:default on 0.0.0.0:8084 started.
2025-01-01 09:32:27 Listener http:dashboard on :18083 started.
2025-01-01 09:32:27 EMQX 5.2.0-build.1 is running now!
```

### 2-2：然后复制eqmx目录

```bash
docker cp emqx:/opt/emqx .
```

> - 这个命令是使用 Docker 的 docker cp 命令来从一个正在运行的容器中将文件或目录复制到主机上
> - 这里是引用
> - 具体解释如下：
> - docker cp：Docker 命令，用于在容器和主机之间复制文件或目录。
> - emqx：容器名称或容器 ID，指定要复制文件或目录的容器。
> - /opt/emqx：容器内的路径，指定要复制的文件或目录在容器内的位置。
> - . 主机内的路径，指定要将文件或目录复制到主机上的位置。. 表示当前用户的主目录。
> - 综合起来，命令 docker cp emqx:/opt/emqx ~ 表示将容器 emqx 中位于 /opt/emqx 路径下的文件或目录复制到当前用户的主目录下。这可以将容器内的文件或目录复制到主机上进行查看、编辑或处理。

### 2-3：然后停止，删除容器

```bash
docker stop emqx
docker rm emqx
```

### 2-4：再重新启动容器与挂载

```bash
docker run -d --name emqx --privileged=true -p 1883:1883 -p 8883:8883 -p 8083:8083 -p 8084:8084 -p 8081:8081 -p 18083:18083 -v /root/emqx:/opt/emqx emqx/emqx:latest
```

### 3：登录EMQX的dashboard界面：输入http://127.0.0.1:18083，默认账号:admin，密码:public

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f5da3382dbf4c5ae71e932973331494e.png)

### 3-1：EMQX的网页客户端工具http://www.emqx.io/online-mqtt-client

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ce21f96da07dded3c60a6ca63d9008a3.png)

### 3-2：添加客户端连接EMQX的认证方式（账号或者客户id，默认是随意账号或者客户id都可以连接）

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3874d5cd6a3eff09f3c57b60c7a6be69.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/84dbf83875eaf776f13bf85698372f62.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/169e1e111f992e9721dd75d9753dff39.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ea144dd1333b2cbca090303e373d82ec.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c6ad583e9b845e89f019b08fe8291b94.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6d4b2f9fd3aa996a811b606b6e2ebe73.png)

### 3-3：输入账号密码保存后，客户端连接就需要使用存在的账号和密码才能连接

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/36f23371fed3f01bf96956f21273611a.png)

### 3-4：客户端连接就需要使用存在的账号和密码才能连接

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a59092d0a10eabe331adaa833bd9151a.png)

## 4：桥接模式，可以转发主题的内容到http或者mqtt，如下转发http配置

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d780547e7e69265b41b078448fc118ed.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3b9ac4ef76a0b6c6321e7e7b0a8e1241.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/780499eb0bcdea0b07c1e88c9ae5c860.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/541edd82c16bd5eda8ab50f68177bcfd.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/125d5e485be825928fb09022b5b1f128.png)

### 4-1：使用客户发送消息

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2f78a78ebd0c84faa93cfe4c618d4512.png)

### 4-2：http服务的服务端与接收到的数据

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5d777fb99a085887b26bed884dbc3ce6.png)

### 4-2：http服务的只接受mqtt内容发的信息，不需要额外信息，设置payload，修改如下

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0c28e5236207d1b2a3fb07f4b52b7e71.png)

## 5：EMQX问题分析
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2bab91a38419345c0eb79d9d1a9f8a15.png)

## 6：Java代码的引入使用,pom导入依赖

```xml
<dependencies>
   <dependency>
       <groupId>org.eclipse.paho</groupId>
       <artifactId>org.eclipse.paho.client.mqttv3</artifactId>
       <version>1.2.5</version>
   </dependency>
</dependencies>

```

### 6-1：然后创建 MQTT 客户端并连接

```java
MqttClient client = new MqttClient(broker, clientid, new MemoryPersistence());
MqttConnectOptions options = new MqttConnectOptions();
options.setUserName(username);
options.setPassword(password.toCharArray());
client.connect(options);
```

> - **MqttClient: 同步调用客户端，使用阻塞方法通信**
> - **MqttClientPersistence: 代表一个持久的数据存储，用于在传输过程中存储出站和入站的信息，使其能够传递到指定的 QoS**
> - **MqttConnectOptions: 连接选项，用于指定连接的参数，下面列举一些常见的方法**
> - **setUserName: 设置用户名**
> - **setPassword: 设置密码**
> - **setCleanSession: 设置是否清除会话**
> - **setKeepAliveInterval: 设置心跳间隔**
> - **setConnectionTimeout: 设置连接超时时间**
> - **setAutomaticReconnect: 设置是否自动重连**

### 6-2：发布 MQTT 消息（tcp://协议前缀即使工具的mqtt://协议）

```java
package io.emqx.mqtt;

import org.eclipse.paho.client.mqttv3.MqttClient;
import org.eclipse.paho.client.mqttv3.MqttConnectOptions;
import org.eclipse.paho.client.mqttv3.MqttException;
import org.eclipse.paho.client.mqttv3.MqttMessage;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;

public class PublishSample {

   public static void main(String[] args) {

       String broker = "tcp://192.168.11.50:1883";
       //String broker = "ws://192.168.11.50:8083/mqtt";//看emqt开启了什么服务
       String topic = "mqtt/test";
       String username = "emqx";
       String password = "public";
       String clientid = "publish_client";
       String content = "Hello MQTT";
       int qos = 0;

       try {
           MqttClient client = new MqttClient(broker, clientid, new MemoryPersistence());
           // 连接参数
           MqttConnectOptions options = new MqttConnectOptions();
           // 设置用户名和密码
           options.setUserName(username);
           options.setPassword(password.toCharArray());
           options.setConnectionTimeout(60);
      options.setKeepAliveInterval(60);
           // 连接
           client.connect(options);
           // 创建消息并设置 QoS
           MqttMessage message = new MqttMessage(content.getBytes());
           message.setQos(qos);
           // 发布消息
           client.publish(topic, message);
           System.out.println("Message published");
           System.out.println("topic: " + topic);
           System.out.println("message content: " + content);
           // 关闭连接
           client.disconnect();
           // 关闭客户端
           client.close();
      } catch (MqttException e) {
           throw new RuntimeException(e);
      }
  }
}

```

### 6-3：订阅 MQTT 主题

```java
package io.emqx.mqtt;

import org.eclipse.paho.client.mqttv3.*;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;

public class SubscribeSample {
   public static void main(String[] args) {
       String broker = "tcp://broker.emqx.io:1883";
       String topic = "mqtt/test";
       String username = "emqx";
       String password = "public";
       String clientid = "subscribe_client";
       int qos = 0;

       try {
           MqttClient client = new MqttClient(broker, clientid, new MemoryPersistence());
           // 连接参数
           MqttConnectOptions options = new MqttConnectOptions();
           options.setUserName(username);
           options.setPassword(password.toCharArray());
           options.setConnectionTimeout(60);
      options.setKeepAliveInterval(60);
           // 设置回调
           client.setCallback(new MqttCallback() {

               public void connectionLost(Throwable cause) {
                   System.out.println("connectionLost: " + cause.getMessage());
              }

               public void messageArrived(String topic, MqttMessage message) {
                   System.out.println("topic: " + topic);
                   System.out.println("Qos: " + message.getQos());
                   System.out.println("message content: " + new String(message.getPayload()));

              }

               public void deliveryComplete(IMqttDeliveryToken token) {
                   System.out.println("deliveryComplete---------" + token.isComplete());
              }

          });
           client.connect(options);
           client.subscribe(topic, qos);
      } catch (Exception e) {
           e.printStackTrace();
      }
  }
}

```

> - **MqttCallback 说明：**
> - **connectionLost(Throwable cause): 连接丢失时被调用**
> - **messageArrived(String topic, MqttMessage message): 接收到消息时被调用**
> - **deliveryComplete(IMqttDeliveryToken token): 消息发送完成时被调用**

### 6-4：MqttCallback单独做一个接口修改如下

```java
package com.example.poi.utils;

import org.eclipse.paho.client.mqttv3.IMqttDeliveryToken;
import org.eclipse.paho.client.mqttv3.MqttCallback;
import org.eclipse.paho.client.mqttv3.MqttMessage;

/**
 * @Author xu
 * @create 2023/9/14 11
 */
public class SampleCallback implements MqttCallback {
    public void connectionLost(Throwable cause) {
        System.out.println("connection lost：" + cause.getMessage());
    }

    public void messageArrived(String topic, MqttMessage message) {
        System.out.println("Received message: \n  topic：" + topic + "\n  Qos：" + message.getQos() + "\n  payload：" + new String(message.getPayload()));
    }

    public void deliveryComplete(IMqttDeliveryToken token) {
        System.out.println("deliveryComplete");
    }
}
```

## 6-5：mqtt回调就可以是使用如下方式

```java
client.setCallback(new SampleCallback());
```

## 7：emqx通讯，如果消费端断开了一天，但是发送端一直发送消息到emqx，怎么保证当消费端正常后，可以消费断开期间的全部消息

- **EMQ X 是支持 MQTT 消息队列功能的消息中间件，因此可以通过 EMQ X 实现在消费端断开期间保留消息，并在消费端重新连接后将离线期间的消息推送给消费端。  
    具体实现方法如下：**

### 7-1：在消费端连接 EMQ X 时，设置 clean_session 参数为 false，这样消费端和 EMQ X 之间的连接不会在消费端断开时自动清除

```java
MqttClient client = new MqttClient(broker, clientId, new MemoryPersistence());
// 连接参数
MqttConnectOptions options = new MqttConnectOptions();
options.setUserName(username);
options.setPassword(password.toCharArray());
options.setConnectionTimeout(60);
options.setKeepAliveInterval(60);
/**消费端和 EMQ X 之间的连接不会在消费端断开时自动清除,当断开后，只要会话过期时间到了，才会消失，可以保证只要有会话在，连上后就可以消费断开之间的消息，如果不想消费断开之间的消息就重新生成一个客户端id,即可解决问题*/
options.setCleanSession(false);
```

- ## **注意EQMX的开启cleanSession会话为false的时候，默认的会话过期时间为2小时，可以通过修改EMQX配置目录opt/emqx/emqx.conf里添加会话过期时间，单位为毫秒，如下设置为1个小时**
    

```bash
mqtt.session_expiry_interval =3600000
```

### 7-2：订阅主题时，使用 QoS 级别为 1 或 2，这样如果发送端在消费端断开期间发布消息，它们将被存储在 EMQ X 中

### 7-3：在 EMQ X 中，开启 Retained Message 功能，可以确保消费端在订阅时能够接收到最新的消息，而不是在消费端重新连接后接收到旧的消息

```java
String content="阳光明媚";
MqttMessage message = new MqttMessage(content.getBytes());
message. setQos(qos);
/**保留消息，最新一条记录一定可以被消费，只要有客户端连接都可以消费到最新的消息*/
message.setRetained(true);
client.publish(topic, message);
```

- **如果发送方发送了很多消息，但消费端断开时间很长，可能会导致 EMQ X 中消息数量过多，建议在 EMQ X 中设置合适的消息过期时间或清理策略，以确保系统性能**

## 8：客户端断开怎么设置自动重连, options.setAutomaticReconnect(true)

- **在设置 options.setAutomaticReconnect(true) 之前，已经调用了 options.setCleanSession(true) 方法，并且客户端与代理断开连接时，代理会清除客户端的会话信息。在这种情况下，自动重新连接可能无法生效**
- **要解决这个问题，可以尝试将 options.setCleanSession(true) 改为 options.setCleanSession(false)，以保留客户端的会话信息，从而使得自动重新连接有效**

```java
options.setCleanSession(false);
options.setAutomaticReconnect(true);
```

- **回调类修改，可以观察重连状态**

```java
package com.example.poi.utils;

import org.eclipse.paho.client.mqttv3.IMqttDeliveryToken;
import org.eclipse.paho.client.mqttv3.MqttCallback;
import org.eclipse.paho.client.mqttv3.MqttCallbackExtended;
import org.eclipse.paho.client.mqttv3.MqttMessage;

/**
 * @Author xu
 * @create 2023/9/14 11
 */
public class SampleCallback implements MqttCallbackExtended {

    public void connectionLost(Throwable cause) {
        System.out.println("connection lost：" + cause.getMessage());
    }

    public void messageArrived(String topic, MqttMessage message) {
        System.out.println("Received message: \n  topic：" + topic + "\n  Qos：" + message.getQos() + "\n  payload：" + new String(message.getPayload()));
    }

    public void deliveryComplete(IMqttDeliveryToken token) {
        System.out.println("deliveryComplete");
    }


    @Override
    public void connectComplete(boolean reconnect, String serverURI) {
        System.out.println(serverURI);
        System.out.println(reconnect);
    }
}

```

## 9：使用ws(默认端口8083)协议发布消息到MQTT，使用ws协议的好处就是后缀有必须的路径/mqtt，方便好处就是可以在nginx代理的时候进行路径转发，这是订阅端代码，发布端代码，使用mqtt(tcp)协议，ws协议都是一样，其实只要修改发布端的url为ws的路径即可以，其他代码都不需要修改

```java
import org.eclipse.paho.client.mqttv3.MqttAsyncClient;
import org.eclipse.paho.client.mqttv3.MqttConnectOptions;
import org.eclipse.paho.client.mqttv3.IMqttToken;
import org.eclipse.paho.client.mqttv3.MqttException;
import org.eclipse.paho.client.mqttv3.MqttMessage;

public class MqttSubscriber {

    public static void main(String[] args) {
        // 替换为你的 MQTT 代理的 WebSocket 端点 URL
        String brokerUrl = "ws://192.168.11.50:8083/mqtt";
        String clientId = "JavaClient";
        String topic = "realtime";

        try {
            // 创建一个 MQTT 客户端
            MqttAsyncClient client = new MqttAsyncClient(brokerUrl, clientId);
            MqttConnectOptions options = new MqttConnectOptions();
            options.setAutomaticReconnect(true);
            options.setCleanSession(true);
            options.setConnectionTimeout(10);

            // 连接到 MQTT 代理
            System.out.println("Connecting to broker: " + brokerUrl);
            client.connect(options).waitForCompletion();
          
            // 订阅主题
            System.out.println("Subscribing to topic: " + topic);
            client.subscribe(topic, 1);

            // 为订阅设置回调，以便在收到消息时执行操作
            client.setCallback(new org.eclipse.paho.client.mqttv3.MqttCallback() {
                @Override
                public void connectionLost(Throwable cause) {
                    System.out.println("Connection to MQTT broker lost!");
                }

                @Override
                public void messageArrived(String topic, MqttMessage message) throws Exception {
                    System.out.println("Message arrived. Topic: " + topic + " Message: " + new String(message.getPayload()));
                }

                @Override
                public void deliveryComplete(IMqttToken token) {
                    System.out.println("Delivery is complete!");
                }
            });

            // 保持程序运行，以便接收消息
            Thread.sleep(Long.MAX_VALUE);

        } catch (MqttException | InterruptedException e) {
            e.printStackTrace();
        }
    }
```