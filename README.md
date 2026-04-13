<p align="center">
  <img src="docs/hrnrOS_logo.svg" alt="hrnrOS Logo" width="200"/>
</p>

<h1 align="center">hrnrOS_v1.3.0</h1>

<p align="center">
  <strong>新一代数据中心裸金属自动化运维平台</strong><br/>
  自动化交付编排 · 黑灯工厂模式 · 全栈硬件感知 · 离线镜像仓库
</p>

<p align="center">
  <a href="https://github.com/hrnr27/hrnrOS/releases">
    <img src="https://img.shields.io/github/v/release/hrnr27/hrnrOS?style=flat-square&label=Latest%20Release&color=238636"/>
  </a>
  <a href="https://github.com/hrnr27/hrnrOS/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/hrnr27/hrnrOS?style=flat-square&label=License&color=0969da"/>
  </a>
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-lightgrey?style=flat-square&logo=linux"/>
  <img src="https://img.shields.io/badge/Arch-x86__64%20%7C%20ARM64-blueviolet?style=flat-square"/>
  <img src="https://img.shields.io/badge/Agentless-Ready-orange?style=flat-square"/>
</p>

---

<details open>
<summary><b>📑 目录 (Table of Contents)</b></summary>

- [项目简介](#-项目简介)
- [v1.3.0 更新亮点](#-v130-更新亮点-whats-new)
- [核心特性](#-核心特性)
- [支持列表](#-支持列表)
- [快速开始](#-快速开始)
- [功能概览](#-功能概览)
- [下载与更新](#-下载与更新)
- [社区与支持](#-社区与支持)

</details>

---

## 📖 项目简介

**hrnrOS** 是一套专为大规模数据中心设计的全生命周期运维平台。它无需依赖复杂的带外网络，通过 **PXE 自动化技术** ，实现了从设备自动发现、系统无人值守安装、全栈硬件监控到故障自愈的完整闭环。

在 v1.3.0 中，平台引入了全新的**自动化交付编排**，实现了裸金属服务器从入库到交付的“流水线”自动化作业。

---

## 🎉 v1.3.0 更新亮点 (What's New)

本次更新聚焦于自动化交付效率与国产信创生态的深度融合：

### 🏗️ 交付编排与任务中心
- **新增 自动化交付编排**：完美串联设备发现、BOM 比对、**BMC 强制配置**、硬件压测、RAID 组建及 OS 自动化下发。
- **新增 自动化交付任务中心**：作为“流水线车间”，全局掌控批次任务进度，支持节点级精准排障与强行干预。
- **新增 RAID 配置模块**：提供带外存储管理能力，支持在 OS 安装前通过内存维护系统对阵列卡 VD/PD 进行细粒度配置。

### 🚀 算力压测与质量管控
- **新增 GPU 深度压力测试**：专为 HPC 与 AI 算力集群设计，支持显卡计算核心负载及显存泄漏排查。
- **新增 压测报告查询中心**：自动汇聚 CPU/内存/硬盘/GPU 的 Burn-in Test 数据，支持在线预览并导出 PDF 报告。
- **升级 全栈压测架构**：全面升级 CPU、内存、硬盘压测模块，提升大规模并发下的采集精度。

### 🌐 基础设施与管理
- **新增 镜像源站与同步管理**：构建私有化内网源，解决带宽瓶颈，**默认采用离线 ISO 安装模式**。
- **升级 交换机与 IP 管理**：提供工业级 IP 地址全生命周期管理与跨厂商交换机配置下发能力。
- **升级 硬件监控平台**：采用最新监控架构，强化了 ECC、SMART 等真实故障场景的分析自愈能力。

### 🛠️ 优化与修复
- **优化 IPMI 管理**：修复 Bug，全面升级并优化 WEB 管理页面。
- **新增 ESXi 子机支持**：运维管理新增对 ESXi 子机的识别与直接窗口管理支持。
- **修复 日志采集**：修复了 NVIDIA GPU 环境下部分日志无法采集的已知问题。

---

## ✨ 核心特性

| 模块 | 亮点功能 |
| :--- | :--- |
| **📦 资产 CMDB** | **自动发现/BOM比对**。深度采集硬件 BOM 清单，支持 CPU 架构识别与全链路操作审计。 |
| **🏗️ 交付编排** | **[NEW] 自动化流水线**。串联 **BMC 默认强制配置** 与 RAID 组建，实现“点亮即交付”。 |
| **🚀 PXE 自动化** | 支持 RHEL/Windows/信创全系。**优先离线 ISO 安装**，支持可视化 RAID/Bond 配置。 |
| **🩺 Nexus 监控** | **[UPDATED] 全栈感知**。实时透视 ECC/SMART/GPU 状态，采用最新架构强化故障分析闭环。 |
| **🛠️ 系统运维** | **[UPDATED] Web 级控制台**。集成 WebSSH/RDP，**新增对 ESXi 子机管理支持**。 |
| **🧪 算力压测** | **[NEW] 深度质量控制**。涵盖 GPU 显存/核心、CPU、内存满载压测，自动生成 PDF 报告。 |
| **🌐 弹药库** | **[NEW] 私有镜像站**。管理本地 ISO 与软件包同步，支持多网段隔离环境下的快速装机。 |

---

## ✅ 支持列表

hrnrOS 支持主流及信创操作系统（x86_64 及 ARM64 架构）：

| 家族 | 支持版本 |
| :--- | :--- |
| **<img src="https://simpleicons.org/icons/redhat.svg" width="12"/> RHEL 系** | RedHat 7/8/9, CentOS 7/8/9, AlmaLinux, Rocky Linux, Oracle Linux |
| **<img src="https://simpleicons.org/icons/windows.svg" width="12"/> Windows** | Server 2008/2012/2016/2019/2022/2025, Windows 10/11 |
| **🇨🇳 国产信创** | openEuler 23/24/25, Anolis 7/8/23, Kylin V10+, UOS, BClinux, CtyunOS, TencentOS |
| **<img src="https://simpleicons.org/icons/ubuntu.svg" width="12"/> Debian 系** | Ubuntu 20.04/22.04/24.04 LTS (**离线安装模式**), Debian 11/12/13 |
| **<img src="https://simpleicons.org/icons/suse.svg" width="12"/> 虚拟化** | **VMware ESXi (含子机识别)**, Proxmox VE, SUSE SLE 12/15 |

---

## 🚀 快速开始

### 1. 获取安装包
~~~bash
wget https://github.com/hrnr27/HrnrKitOS/releases/download/hrnr_install_v1.3.0.tar.gz
tar -zxvf hrnr_install_v1.3.0.tar.gz
cd hrnr_install_v1.3.0/
~~~

### 2. 一键安装
~~~bash
sudo ./install
~~~

### 3. 访问控制台
通过浏览器访问：`http://<服务器IP>:8080` (默认账号/密码：`admin`/`hrnrkit`)

---

## 🧩 功能概览

### 1. 全栈硬件监控 (Nexus Monitor) - v2.0
具备自我感知能力的监控大屏。v1.3.0 采用最新架构，以真实故障场景经验为指导，强化了 GPU 显存及硬件微损场景的深度分析能力。

### 2. 自动化交付流水线 (Delivery Orchestration) - 新增
为大规模裸金属设计的“交付指挥部”。自动串联：**BOM比对 -> BMC强制策略配置 -> RAID组建 -> 硬件72小时压测 -> 自动生成报告 -> 离线OS安装**。

### 3. 自动化 OS 安装 (Visual Config)
告别盲装。安装前自动扫描物理磁盘，支持可视化配置 RAID (0/1/5/10) 及网络 Bond 模式。**针对信创环境优化，移除在线源，默认采用 ISO 离线模式。**

### 4. GPU 深度压力测试 (GPU Stress Test) - 新增
针对 HPC 与 AI 算力集群设计。对显卡计算核心及显存颗粒执行高强度验证，支持显存泄漏排查及极限稳定性评估。

### 5. 高效系统运维 (System Ops) - 升级
集成 WebSSH 终端与批量脚本控制台。**新增对 ESXi 子机的识别**，支持直接从 hrnrOS 运维中心拉起子机控制窗口。

### 6. 物理磁盘定位 (Disk Locator)
无需安装 Agent，直接通过底层指令点亮 LED 灯，支持 **NVMe、RAID 及 HBA 直通盘**，解决现场运维拔错盘的痛点。

---

## 📥 下载与更新

| 版本类型 | 说明 | 下载链接 |
| :--- | :--- | :--- |
| **📦 Full (全量包)** | 包含完整依赖与基础镜像，适用于**全新离线安装**。 | [GitHub Release](https://github.com/hrnr27/hrnrOS/releases) |
| **⚡ Update (更新包)** | 仅包含核心程序与 Web 资源，适用于 v1.x **平滑升级**。 | [GitHub Release](https://github.com/hrnr27/hrnrOS/releases) |

---

## 💬 社区与支持

- **官方 QQ**: `759419595`
- **官方 QQ群**: `1065138530`
- **微信公众号**: `Linux客栈`
- **邮件支持**: <support@hrnrkit.cn>

<p align="center">
  <sub>Made with ❤️ by HrnrKit Team. 赋能数据中心智能运维。</sub>
</p>
