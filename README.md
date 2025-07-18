# Solana RPC 节点一键安装与管理脚本

## 简介

本脚本旨在为 Solana 节点运维者提供一套**一键自动化安装、优化、管理**的解决方案。通过系统参数优化和自动化流程，极大降低部署门槛，让 Solana 节点可以在更经济的服务器上高效运行并保持良好的区块同步速度。

- 支持主网、测试网、开发网
- 适合普通 RPC 节点和中小型服务商
- 集成交互式管理菜单和常用快捷命令
- 本脚本是由https://github.com/0xfnzero/solana-rpc-install/tree/main自动化。有任何疑问请移步查看
---

## 推荐硬件配置

- **CPU**：AMD Ryzen 9 9950X 或同级别 x86_64 处理器
- **内存**：≥ 192GB（官方推荐 1TB，脚本优化后 192GB 也可流畅运行）
- **磁盘**：至少 3 块 NVMe SSD
  - 系统盘：1TB
  - 账本盘（ledger）：≥ 2TB
  - 账户盘（accounts）：≥ 2TB
- **操作系统**：Ubuntu 20.04/22.04（建议裸机或高性能云主机）

---

## 功能特性

- 一键自动化安装 Solana 节点及依赖
- 自动检测并挂载 NVMe 磁盘，安全格式化（带二次确认）
- 系统参数极致优化（sysctl、ulimit、内核、网络等）
- 自动安装 openssl1.1 兼容包
- 自动生成并管理验证者密钥
- 自动配置防火墙
- 自动生成 systemd 服务和启动脚本
- 自动下载并集成健康检查、同步监控等运维脚本
- 交互式中文管理菜单，支持常用节点运维操作
- 支持自我更新

---

## 快速开始

### 1. 上传脚本到服务器

```bash
scp solana-rpc.sh root@your_server:/root/
chmod +x /root/solana-rpc.sh
```

### 2. 一键安装节点（首次运行）

```bash
./solana-rpc.sh --install
```

> **注意：**  
> - 安装过程中会自动检测并格式化账本盘和账户盘，请务必确认磁盘选择无误，避免数据丢失。
> - 安装完成后，脚本会输出硬件信息和常用管理命令。

### 3. 日常管理（推荐菜单模式）

```bash
solana-rpc --menu
```

进入交互式菜单，支持启动/停止/重启节点、查看状态、日志、健康、监控等操作。

### 4. 常用命令

```bash
solana-rpc --status       # 查看节点状态
solana-rpc --logs         # 查看实时日志
solana-rpc --catchup      # 检查区块同步
solana-rpc --health       # 检查节点健康
solana-rpc --monitor      # 硬件监控
solana-rpc --start        # 启动节点
solana-rpc --stop         # 停止节点
solana-rpc --restart      # 重启节点
solana-rpc --update       # 更新脚本
```

---

## FAQ

### Q: 192GB 内存真的够用吗？
A: 通过系统参数优化和合理配置，192GB 内存可满足普通 RPC 节点需求。极端高负载或全历史节点建议 512GB~1TB。

### Q: 脚本会自动格式化磁盘吗？
A: 是的，但会有二次确认提示，只有输入 `yes` 才会执行格式化操作。

### Q: 支持哪些系统？
A: 推荐 Ubuntu 20.04/22.04，需 x86_64 架构，root 权限。

### Q: 如何更新脚本？
A: 运行 `solana-rpc --update`，脚本会自动自我更新。

### Q: 节点安装后如何日常管理？
A: 推荐使用 `solana-rpc --menu` 进入交互式菜单，或用快捷命令。

---

## 交流与支持

- Telegram 群组：[https://t.me/fnzero_group](https://t.me/fnzero_group)
- Issues/PR 欢迎提交改进建议

---

## 免责声明

本脚本为开源工具，请在测试环境充分验证后再用于生产环境。格式化磁盘等高风险操作请务必谨慎，数据丢失风险自负。

---

**让 Solana 节点部署和运维变得更简单！**
