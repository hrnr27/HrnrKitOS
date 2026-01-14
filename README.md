<!-- GitHub README.md for hrnr27/hrnrOS -->
<p align="center">
  <img src="docs/hrnrOS_logo.svg" alt="hrnrOS Logo" width="200"/>
</p>

<h1 align="center">hrnrOSv1.2.1</h1>

<p align="center">
  <strong>新一代数据中心裸金属自动化运维平台</strong><br/>
  资产全生命周期 · 裸金属自动驾驶 · 全栈硬件感知 · 故障自愈闭环
</p>

<p align="center">
  <a href="https://github.com/hrnr27/hrnrOS/releases">
    <img src="https://img.shields.io/github/v/release/hrnr27/hrnrOS?style=flat-square&label=Latest%20Release&color=238636"/>
  </a>
  <a href="https://github.com/hrnr27/hrnrOS/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/hrnr27/hrnrOS?style=flat-square&label=License&color=0969da"/>
  </a>
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-lightgrey?style=flat-square&logo=linux"/>
  <img src="https://img.shields.io/badge/Agentless-Ready-orange?style=flat-square"/>
</p>

---

<details open>
<summary><b>📑 目录 (Table of Contents)</b></summary>

- [项目简介](#-项目简介)
- [核心特性](#-核心特性)
- [支持列表](#-支持列表)
- [快速开始](#-快速开始)
- [功能概览](#-功能概览)
- [下载与更新](#-下载与更新)
- [社区与支持](#-社区与支持)

</details>

---

## 📖 项目简介

**hrnrOS** 是一套专为大规模数据中心设计的全生命周期运维平台。它无需依赖复杂的带外网络，通过 **PXE 自动化技术** + **Agentless (无代理) 模式**，实现了从**设备自动发现、系统无人值守安装、全栈硬件监控**到**故障自愈**的完整闭环。

无论是数百台服务器的新局点交付，还是日常的硬件故障排查，hrnrOS 都能让繁杂的运维工作变得像驾驶自动挡汽车一样简单。

---

## ✨ 核心特性

| 模块 | 亮点功能 |
| :--- | :--- |
| **📦 资产 CMDB** | **自动发现/Excel导入**，深度采集 CPU/内存/硬盘/网卡/GPU 形成 BOM 清单，记录全链路操作审计。 |
| **🚀 PXE 自动化** | 支持 **RHEL/Windows/国产信创** 全系系统。独创 **可视化 RAID/Bond 配置**，Windows 自动分区与驱动注入。 |
| **🩺 Nexus 监控** | **全栈感知 + 故障自愈**。实时透视 ECC/SMART/GPU 状态；Agent 失联自动触发 SSH/IPMI 重启修复；支持基准变更审计。 |
| **🛠️ 系统运维** | **浏览器即控制台**。集成 WebSSH (含 SFTP)、**一键唤起本地 RDP**、批量密码初始化与脚本并发执行。 |
| **💡 现场神器** | **物理磁盘定位 (无 Agent)**。通过 SSH 直接控制背板，点亮 NVMe/RAID/HBA 硬盘定位灯，拒绝拔错盘。 |
| **🎮 IPMI 管理** | 批量电源控制，提供 **Web 控制台临时凭据** (30分钟轮换)，支持 BMC 密码修复与恢复出厂设置。 |
| **🌐 网络架构** | **多网段并行服务**。单机同时支撑多个 VLAN/物理网段的 PXE 服务，物理隔离，互不干扰。 |

---

## ✅ 支持列表

hrnrOS 内置了丰富的自动化安装模板，覆盖主流及信创操作系统：

| 家族 | 支持版本 |
| :--- | :--- |
| **<img src="https://simpleicons.org/icons/redhat.svg" width="12"/> RHEL 系** | RedHat 7/8/9, CentOS 7/8/9, AlmaLinux, Rocky Linux, Oracle Linux |
| **<img src="https://simpleicons.org/icons/windows.svg" width="12"/> Windows** | Server 2008/2012/2016/2019/2022/2025, Windows 10/11 |
| **🇨🇳 国产信创** | openEuler (欧拉) 23/24/25, Anolis (龙蜥) 7/8/23, Kylin (麒麟) V10+, UOS |
| **<img src="https://simpleicons.org/icons/ubuntu.svg" width="12"/> Debian 系** | Ubuntu 20.04/22.04/24.04 LTS, Debian 11/12/13 |
| **<img src="https://simpleicons.org/icons/suse.svg" width="12"/> 虚拟化** | VMware ESXi 8, Proxmox VE, SUSE SLE 12/15 |

---

## 🚀 快速开始

hrnrOS 支持部署在 **Rocky Linux 8+ / Ubuntu 20.04+** 等主流 Linux 发行版上。

### 1. 获取安装包
```bash
wget https://github.com/hrnr27/hrnrOS/releases/download/v1.2.1/hrnrOS-nexus-v1.2.1-full.tar.gz
tar -zxvf hrnrOS-nexus-v1.2.1-full.tar.gz
cd hrnrOS-nexus-v1.2.1
```

### 2. 一键安装
脚本会自动检测环境、格式化数据盘并配置服务。
```bash
sudo ./install
```

### 3. 访问控制台
安装完成后，通过浏览器访问：`http://<服务器IP>:8080`
- 默认账号：`admin`
- 默认密码：`hrnrkit`

---

## 🧩 功能概览

### 1. 全栈硬件监控 (Nexus Monitor)

具备自我感知能力的监控大屏。不仅展示状态，更支持 **Agent 无感热升级** 与 **智能修复**。

### 2. 自动化 OS 安装 (Visual Config)

告别盲装。在安装前，系统会自动扫描物理磁盘，支持 **可视化配置 RAID 级别** (0/1/5/10) 及网络 Bond 模式。

### 3. 高效系统运维 (System Ops)

集成 WebSSH 终端与批量脚本控制台。针对 Windows 服务器，提供 **一键唤起 RDP** 功能，自动填充凭据，点击即连。

### 4. 物理磁盘定位 (Disk Locator)

专为现场运维设计。无需安装 Agent，直接通过底层指令点亮硬盘 LED 灯，支持 **NVMe、RAID 及 HBA 直通盘**。

### 5. 一键日志采集

自动化收集 RAID 卡日志 (MegaCli/StorCli)、GPU 调试信息及系统日志，内置 **在线高亮搜索器**，快速定位故障。

---

## 📥 下载与更新

| 版本类型 | 说明 | 下载链接 |
| :--- | :--- | :--- |
| **📦 Full (全量包)** | 包含完整依赖与基础镜像，适用于**全新离线安装**。 | [GitHub Release](https://github.com/hrnr27/hrnrOS/releases) |
| **⚡ Update (更新包)** | 仅包含核心程序与 Web 资源，适用于 v1.x **平滑升级**。 | [GitHub Release](https://github.com/hrnr27/hrnrOS/releases) |

---

## 💬 社区与支持

- **官方 QQ**: `759419595` ([点击唤起](http://wpa.qq.com/msgrd?v=3&uin=12345678&site=qq&menu=yes))
- **微信公众号**: `Linux客栈` (获取技术干货与更新推送)
- **Bug 反馈**: [GitHub Issues](https://github.com/hrnr27/hrnrOS/issues)
- **邮件支持**: <support@hrnrkit.cn>

---

<p align="center">
  <sub>Made with ❤️ by HrnrKit Team. 赋能数据中心智能运维。</sub>
</p>
