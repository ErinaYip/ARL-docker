# ARL-docker (fork)

Fork 自 [honmashironeko/ARL-docker](https://github.com/honmashironeko/ARL-docker)，ARL（灯塔）v2.6.2 Docker 部署。

本 fork 的修改：

- `docker-compose.yml` 适配 NixOS + rootless Podman：去掉 external 卷，日志/截图/poc 改用命名卷，配置只读挂载，mongodb/rabbitmq 加 healthcheck，补 `exec` 修信号传递，移除废弃的 `version` 字段。
- 删除原仓库的 yum/apt 安装脚本、换源脚本、外部 docker-compose 二进制和占位日志文件。

部署：

```bash
export DOCKER_HOST=unix:///run/user/$(id -u)/podman/podman.sock   # 仅 rootless Podman 需要
docker-compose up -d
```

访问 `https://IP:5003/`，默认账号 `admin` / `honmashironeko`。配置见 `config-docker.yaml`。
