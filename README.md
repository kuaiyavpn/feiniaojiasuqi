# 飞鸟加速器(又名飞鸟VPN,飞鸟加速)

[简体中文](#简体中文) | [English](#english)

</div>

---

## 简体中文

### 🚀 简介

飞鸟加速器是一款专业的网络加速服务，致力于为用户提供稳定、高速、安全的网络连接体验。通过智能路由技术和全球节点部署，帮助用户优化网络访问速度，降低延迟，提升整体网络体验。

### ✨ 核心特性

- **🌍 全球节点覆盖** - 在亚洲、北美、欧洲等地区部署高速节点
- **⚡ 智能加速** - 自动选择最优线路，支持BBR加速技术
- **🔒 安全加密** - 采用行业标准加密协议，保护数据传输安全
- **📱 多平台支持** - 支持Windows、macOS、Linux、iOS、Android等主流平台
- **🎯 智能分流** - 支持规则分流和智能路由，优化访问体验
- **💡 简单易用** - 一键连接，无需复杂配置
- **🔧 灵活配置** - 支持自定义代理规则和高级设置
- **📊 实时监控** - 提供流量统计和连接状态实时监控

### 🛠️ 技术架构

```
┌─────────────────────────────────────────┐
│            客户端应用层                   │
├─────────────────────────────────────────┤
│          协议层 (GOST/SS/V2Ray)          │
├─────────────────────────────────────────┤
│           智能路由层 (BBR/策略路由)        │
├─────────────────────────────────────────┤
│          节点管理层 (负载均衡/故障转移)     │
├─────────────────────────────────────────┤
│           基础设施层 (全球节点网络)         │
└─────────────────────────────────────────┘
```

### 📦 安装指南

#### Windows
```bash
# 下载安装程序
https://feiniao-vpn.com/download/windows

# 或使用 PowerShell 安装
iwr -useb https://feiniao-vpn.com/install.ps1 | iex
```

#### macOS
```bash
# 使用 Homebrew 安装
brew tap feiniao/vpn
brew install feiniao-accelerator

# 或下载 DMG 安装包
https://feiniao-vpn.com/download/macos
```

#### Linux
```bash
# Ubuntu/Debian
curl -fsSL https://feiniao-vpn.com/install.sh | sudo bash

# CentOS/RHEL/Rocky Linux
sudo yum install -y https://feiniao-vpn.com/feiniao-release.rpm
sudo yum install feiniao-accelerator
```

#### Android / iOS
- Android: [Google Play](https://play.google.com/store/apps/feiniao) | [APK下载](https://feiniao-vpn.com/download/android)
- iOS: [App Store](https://apps.apple.com/app/feiniao)

### ⚙️ 配置说明

#### 基础配置
```json
{
  "server": "auto",
  "mode": "smart",
  "protocol": "auto",
  "dns": {
    "enable": true,
    "server": "8.8.8.8"
  },
  "routing": {
    "domainStrategy": "IPIfNonMatch",
    "rules": []
  }
}
```

#### 高级配置示例
```json
{
  "server": "hk01.feiniao.com",
  "port": 8443,
  "protocol": "vmess",
  "settings": {
    "vnext": [{
      "address": "hk01.feiniao.com",
      "port": 8443,
      "users": [{
        "id": "your-uuid-here",
        "alterId": 64,
        "security": "auto"
      }]
    }]
  },
  "streamSettings": {
    "network": "tcp",
    "security": "tls",
    "tlsSettings": {
      "serverName": "hk01.feiniao.com"
    }
  },
  "mux": {
    "enabled": true,
    "concurrency": 8
  }
}
```

### 🚄 性能优化

#### 启用 BBR 加速
```bash
# Linux 系统启用 BBR
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
```

#### 优化网络参数
```bash
# 优化 TCP 参数
cat >> /etc/sysctl.conf << EOF
net.ipv4.tcp_fastopen = 3
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.ip_local_port_range = 10000 65000
net.ipv4.tcp_max_syn_backlog = 8192
net.ipv4.tcp_max_tw_buckets = 5000
EOF

sysctl -p
```

### 📊 使用统计

| 指标 | 数值 |
|------|------|
| 全球节点数量 | 200+ |
| 覆盖国家/地区 | 50+ |
| 月活跃用户 | 100,000+ |
| 平均延迟降低 | 60% |
| 连接成功率 | 99.9% |

### 🔧 故障排除

#### 连接问题
```bash
# 检查网络连接
ping feiniao-vpn.com

# 查看日志
tail -f /var/log/feiniao/access.log

# 重启服务
systemctl restart feiniao-accelerator
```

#### 常见问题解决方案

1. **无法连接到服务器**
   - 检查网络连接状态
   - 验证账户是否有效
   - 尝试切换节点

2. **速度较慢**
   - 选择地理位置更近的节点
   - 启用智能加速模式
   - 检查本地网络带宽

3. **频繁断线**
   - 更新到最新版本客户端
   - 调整超时设置
   - 联系技术支持

### 🤝 贡献指南

欢迎贡献代码、报告问题或提出建议！

1. Fork 本仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

### 📞 联系我们

- 官网: [https://feiniao-vpn.com](https://feiniao-vpn.com)
- 邮箱: support@feiniao-vpn.com
- Telegram: [@feiniao_support](https://t.me/feiniao_support)
- 文档: [https://docs.feiniao-vpn.com](https://docs.feiniao-vpn.com)

---

## English

### 🚀 Introduction

FeiNiao Accelerator is a professional network acceleration service dedicated to providing users with stable, high-speed, and secure network connection experience. Through intelligent routing technology and global node deployment, it helps users optimize network access speed, reduce latency, and enhance overall network experience.

### ✨ Core Features

- **🌍 Global Node Coverage** - High-speed nodes deployed in Asia, North America, Europe, and more
- **⚡ Intelligent Acceleration** - Auto-select optimal routes with BBR acceleration support
- **🔒 Secure Encryption** - Industry-standard encryption protocols to protect data transmission
- **📱 Multi-Platform Support** - Support for Windows, macOS, Linux, iOS, Android, and more
- **🎯 Smart Routing** - Support for rule-based routing and intelligent traffic splitting
- **💡 Easy to Use** - One-click connection, no complex configuration needed
- **🔧 Flexible Configuration** - Support for custom proxy rules and advanced settings
- **📊 Real-time Monitoring** - Traffic statistics and connection status monitoring

### 🛠️ Technical Architecture

```
┌─────────────────────────────────────────┐
│          Client Application Layer        │
├─────────────────────────────────────────┤
│      Protocol Layer (GOST/SS/V2Ray)     │
├─────────────────────────────────────────┤
│   Smart Routing Layer (BBR/Policy)      │
├─────────────────────────────────────────┤
│  Node Management (LB/Failover)           │
├─────────────────────────────────────────┤
│   Infrastructure (Global Network)        │
└─────────────────────────────────────────┘
```

### 📦 Installation Guide

#### Windows
```bash
# Download installer
https://feiniao-vpn.com/download/windows

# Or install via PowerShell
iwr -useb https://feiniao-vpn.com/install.ps1 | iex
```

#### macOS
```bash
# Install via Homebrew
brew tap feiniao/vpn
brew install feiniao-accelerator

# Or download DMG package
https://feiniao-vpn.com/download/macos
```

#### Linux
```bash
# Ubuntu/Debian
curl -fsSL https://feiniao-vpn.com/install.sh | sudo bash

# CentOS/RHEL/Rocky Linux
sudo yum install -y https://feiniao-vpn.com/feiniao-release.rpm
sudo yum install feiniao-accelerator
```

#### Android / iOS
- Android: [Google Play](https://play.google.com/store/apps/feiniao) | [APK Download](https://feiniao-vpn.com/download/android)
- iOS: [App Store](https://apps.apple.com/app/feiniao)

### ⚙️ Configuration

#### Basic Configuration
```json
{
  "server": "auto",
  "mode": "smart",
  "protocol": "auto",
  "dns": {
    "enable": true,
    "server": "8.8.8.8"
  },
  "routing": {
    "domainStrategy": "IPIfNonMatch",
    "rules": []
  }
}
```

#### Advanced Configuration Example
```json
{
  "server": "hk01.feiniao.com",
  "port": 8443,
  "protocol": "vmess",
  "settings": {
    "vnext": [{
      "address": "hk01.feiniao.com",
      "port": 8443,
      "users": [{
        "id": "your-uuid-here",
        "alterId": 64,
        "security": "auto"
      }]
    }]
  },
  "streamSettings": {
    "network": "tcp",
    "security": "tls",
    "tlsSettings": {
      "serverName": "hk01.feiniao.com"
    }
  },
  "mux": {
    "enabled": true,
    "concurrency": 8
  }
}
```

### 🚄 Performance Optimization

#### Enable BBR Acceleration
```bash
# Enable BBR on Linux
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
```

#### Optimize Network Parameters
```bash
# Optimize TCP parameters
cat >> /etc/sysctl.conf << EOF
net.ipv4.tcp_fastopen = 3
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.ip_local_port_range = 10000 65000
net.ipv4.tcp_max_syn_backlog = 8192
net.ipv4.tcp_max_tw_buckets = 5000
EOF

sysctl -p
```

### 📊 Usage Statistics

| Metric | Value |
|--------|-------|
| Global Nodes | 200+ |
| Countries/Regions | 50+ |
| Monthly Active Users | 100,000+ |
| Average Latency Reduction | 60% |
| Connection Success Rate | 99.9% |

### 🔧 Troubleshooting

#### Connection Issues
```bash
# Check network connection
ping feiniao-vpn.com

# View logs
tail -f /var/log/feiniao/access.log

# Restart service
systemctl restart feiniao-accelerator
```

#### Common Solutions

1. **Cannot connect to server**
   - Check network connection status
   - Verify account validity
   - Try switching nodes

2. **Slow speed**
   - Select geographically closer nodes
   - Enable smart acceleration mode
   - Check local network bandwidth

3. **Frequent disconnections**
   - Update to latest client version
   - Adjust timeout settings
   - Contact technical support

### 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

### 📞 Contact Us

- Website: [https://feiniao-vpn.com](https://feiniao-vpn.com)
- Email: support@feiniao-vpn.com
- Telegram: [@feiniao_support](https://t.me/feiniao_support)
- Documentation: [https://docs.feiniao-vpn.com](https://docs.feiniao-vpn.com)

---

<div align="center">
  
**🌟 Star this repository if you find it helpful!**

Made with ❤️ by FeiNiao Team

</div>
