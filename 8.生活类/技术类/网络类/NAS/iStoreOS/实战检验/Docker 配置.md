
本教程介绍如何在 iStoreOS 上将 Dockge 安装到 NVMe 硬盘，以解决内置存储空间不足的问题。

>**注意**：Docker 所被部署到的文件系统必须是 exFat4 等支持 overlay 特性的文件系统

### 1. 准备工作

#### (1) 确认挂载点

确保 NVMe 硬盘已挂载到 `/mnt/nvme0n1-4`。

```bash
df -h | grep nvme0n1-4
```

示例输出：

```
/dev/nvme0n1p4 /mnt/nvme0n1-4 ext4 1.8T 100G 1.7T 6% /mnt/nvme0n1-4
```

#### (2) 创建 Docker 数据目录

在 NVMe 硬盘上创建目录，用于存放 Docker 数据和 Dockge 配置：

```bash
mkdir -p /mnt/nvme0n1-4/docker/dockge
mkdir -p /mnt/nvme0n1-4/docker/stacks
```

### 2. 安装 Docker Compose (如果未安装)

```bash
opkg update
opkg install docker-compose
```

### 3. 创建 Dockge docker-compose.yml

进入 Dockge 配置目录并创建配置文件：

```bash
cd /mnt/nvme0n1-4/docker/dockge
nano docker-compose.yml
```

添加以下内容：

```yaml
version: '3'
services:
  dockge:
    image: louislam/dockge:latest
    container_name: dockge
    restart: unless-stopped
    ports:
      - "5001:5001"  # Web 访问端口，可修改
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock  # Docker Socket
      - ./data:/app/data  # Dockge 配置
      - /mnt/nvme0n1-4/docker/stacks:/opt/stacks  # Compose 项目目录
    environment:
      - DOCKGE_STACKS_DIR=/opt/stacks  # Compose 项目路径
```

### 4. 启动 Dockge 服务

```bash
docker-compose up -d
```

验证容器状态：

```bash
docker ps | grep dockge
```

### 5. 访问 Dockge 管理界面

浏览器访问：`http://<iStoreOS_IP>:5001`

*   **首次访问**：界面显示 `/opt/stacks` 目录下的 Compose 项目（初始为空）。
*   **操作入口**：点击右上角 **“Create Stack”** 创建新项目，或上传现有 `docker-compose.yml`。

### 6. 添加 Compose 项目示例

#### (1) 创建 Nginx 项目

```bash
mkdir -p /mnt/nvme0n1-4/docker/stacks/nginx
nano /mnt/nvme0n1-4/docker/stacks/nginx/docker-compose.yml
```

添加以下内容（避免端口冲突）：

```yaml
version: '3'
services:
  nginx:
    image: nginx:latest
    ports:
      - "8080:80"  # 映射到 8080 端口
    volumes:
      - ./html:/usr/share/nginx/html  # 挂载静态页面目录
```

#### (2) 在 Dockge 中部署

1.  刷新 Dockge 界面，点击 **“Nginx”** 项目。
2.  点击 **“Start”** 启动容器。
3.  访问 `http://<iStoreOS_IP>:8080` 验证 Nginx 是否运行。

### 7. 关键注意事项

#### (1) 权限问题

如果容器启动失败并提示 **Permission Denied**：

```bash
chmod -R 777 /mnt/nvme0n1-4/docker
cd /mnt/nvme0n1-4/docker/dockge
docker-compose restart
```

#### (2) 备份与恢复

*   **备份 Dockge 配置**:

    ```bash
    tar -czvf dockge-backup.tar.gz /mnt/nvme0n1-4/docker/dockge/data
    ```
*   **恢复备份**:

    ```bash
    tar -xzvf dockge-backup.tar.gz -C /
    ```

#### (3) 更新 Dockge

```bash
cd /mnt/nvme0n1-4/docker/dockge
docker-compose pull
docker-compose up -d
```

### 8. 卸载 Dockge

```bash
cd /mnt/nvme0n1-4/docker/dockge
docker-compose down
rm -rf /mnt/nvme0n1-4/docker/dockge  # 可选
```

通过以上步骤，你可以将 Dockge 及其管理的所有 Compose 项目数据存储在 NVMe 硬盘上，充分利用大容量存储的优势，同时避免 iStoreOS 内置存储空间不足的问题。
