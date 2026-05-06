<p align="center">
  <img src="docs/DeplOS_logo.svg" alt="DeplOS Logo" width="200"/>
</p>

<h1 align="center">DeplOS_v1.3.3</h1>

<p align="center">
  <strong>新一代数据中心裸金属自动化运维平台</strong><br/>
  自动化交付编排 · 黑灯工厂模式 · 全栈硬件感知 · 离线镜像仓库
</p>

> <p align="center"><strong>序阵 · Deploy OS</strong> — 让每一次部署，都井然成阵。</p>

<p align="center">
  <a href="https://github.com/hrnr27/DeplOS/releases">
    <img src="https://img.shields.io/github/v/release/hrnr27/DeplOS?style=flat-square&label=Latest%20Release&color=238636"/>
  </a>
  <a href="https://github.com/hrnr27/DeplOS/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/hrnr27/DeplOS?style=flat-square&label=License&color=0969da"/>
  </a>
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-lightgrey?style=flat-square&logo=linux"/>
  <img src="https://img.shields.io/badge/Arch-x86__64%20%7C%20ARM64-blueviolet?style=flat-square"/>
  <img src="https://img.shields.io/badge/Agentless-Ready-orange?style=flat-square"/>
</p>


<details open>
<summary><b>📑 目录 (Table of Contents)</b></summary>

- [项目简介](#-项目简介)
- [v1.3.3 更新亮点](#-v133-更新亮点-whats-new)
- [v1.3.2 更新亮点](#-v132-更新亮点-whats-new)
- [核心特性](#-核心特性)
- [支持列表](#-支持列表)
- [快速开始](#-快速开始)
- [功能概览](#-功能概览)
- [下载与更新](#-下载与更新)
- [社区与支持](#-社区与支持)

</details>

---

## 📖 项目简介

**DeplOS** 是一套专为大规模数据中心设计的全生命周期运维平台。它无需依赖复杂的带外网络，通过 **PXE 自动化技术**，实现了从设备自动发现、系统无人值守安装、全栈硬件监控到故障自愈的完整闭环。

在 v1.3.3 中，我们完成了**项目重命名与端口变更**，进一步强化了**GPU 硬件适配能力**，并显著提升了系统安全性。

---

## 🎉 v1.3.3 更新亮点 (What's New)

> [!CAUTION]
> **特别提示（升级必读）**
> - **项目更名**：项目从 `hrnros` 正式重命名为 `deplos`，涉及全局配置与脚本路径变更，请务必检查相关依赖。
> - **端口变更**：服务端口由 `8080` 调整为 `9100`，以避免与用户环境中的常见端口冲突，请相应调整防火墙及反向代理配置。
>
> **重要说明**：此次更新涉及项目重命名、端口变更及内核升级，建议在维护窗口期操作，并提前备份配置文件。

### 🛠️ 底层能力与兼容性
- **升级 系统内核**：同步升级 deplOS x86_64 及 ARM64 架构的内核版本，全面提升系统稳定性和硬件兼容性。
- **优化 NVIDIA GPU 驱动**：适配更多 GPU 型号，增强诊断测试模块的准确性。
- **更新 GPU Fieldiag 支持**：新增对 NVIDIA H 系列、B 系列显卡的支持。

### 🏷️ 项目与基础设施
- **项目重命名**：将项目从 `hrnros` 正式重命名为 `deplos`。
- **服务端口变更**：为避免端口冲突，服务端口从 `8080` 修改为 `9100`。

### 🏗️ 交付编排与效率
- **优化 BMC 信息处理**：优化入库编排任务，以用户导入的 BMC 信息为准，若信息正确则直接采用，不再进行修改。

### 🔒 系统安全
- **系统安全加固**：优化并修复了多个系统安全隐患，提升整体安全性。

---

## 🎉 v1.3.2 更新亮点 (What's New)

此次更新聚焦于底层兼容性优化、自动化交付链路增强及易用性提升：

### 🛠️ 底层能力与兼容性
- **新增 BIOS 远程配置**：新增独立 BIOS 配置功能模块，支持通过平台统一管理服务器底层硬件参数。
- **升级 系统内核**：升级 x86_64 架构内核版本，大幅提升系统在高并发部署场景下的稳定性和新型硬件兼容性。
- **优化 GPU 驱动适配**：更新 NVIDIA GPU 驱动架构，适配更多新型号显卡，并同步增强了 GPU 诊断测试模块的准确性。
- **修复 ARM 架构 RAID 配置**：解决了 DeplOS 在 ARM 架构镜像下 RAID 卡无法识别或配置失败的兼容性问题。

### 🏗️ 交付编排与效率
- **新增 场景化新手向导**：在资产管理页面引入快速使用向导，引导用户快速完成从"资产入库"到"自动化交付"的流程闭环。
- **增强 自动化压测流程**：在"新机入库"编排任务中新增**硬盘压测**环节；所有压测模块（CPU/内存/硬盘/GPU）新增"停留在 DeplOS 选择界面"选项，方便现场人工调试。
- **优化 任务调度稳定性**：修复了自动化编排任务因执行时间过长导致异常跳过并误报"安装成功"的逻辑 Bug。
- **优化 PXE 数据加载**：PXE 安装模块任务创建改为直接拉取数据库实时数据，提升高并发任务下的响应速度。

### 🌐 基础设施管理
- **更新 硬件故障库**：扩充硬件健康监控（Nexus Monitor）的故障实例库，提升对亚健康硬件的预警精度。
- **优化 镜像源站管理**：清理并移除失效的公共镜像源，确保内网同步环境的纯净与高效。

> [!WARNING]
> **异常说明**：由于功能架构调整，**GPU 压力测试**模块在 v1.3.2 中暂时关闭，预计将在下个版本修复优化后重新开放。

---

## ✨ 核心特性

| 模块 | 亮点功能 |
| :--- | :--- |
| **📦 资产 CMDB** | **自动发现/BOM比对**。深度采集硬件 BOM 清单，支持 CPU 架构识别与全链路操作审计。 |
| **🏗️ 交付编排** | **自动化流水线**。串联 **BMC 默认强制配置** 与 RAID 组建，实现"点亮即交付"。 |
| **🚀 PXE 自动化** | 支持 RHEL/Windows/信创全系。**优先离线 ISO 安装**，支持可视化 RAID/Bond 配置。 |
| **🩺 Nexus 监控** | **全栈感知**。实时透视 ECC/SMART/GPU 状态，采用最新架构强化故障分析闭环。 |
| **🛠️ 系统运维** | **Web 级控制台**。集成 WebSSH/RDP，**新增对 ESXi 子机管理支持**。 |
| **🧪 算力压测** | **深度质量控制**。涵盖 GPU 显存/核心、CPU、内存满载压测，自动生成 PDF 报告。 |
| **🌐 弹药库** | **私有镜像站**。管理本地 ISO 与软件包同步，支持多网段隔离环境下的快速装机。 |

---

## ✅ 支持列表

DeplOS 支持主流及信创操作系统（x86_64 及 ARM64 架构）：

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
wget https://github.com/hrnr27/DeplOS/releases/download/v1.3.3/deplos_install_v1.3.3.tar.gz
tar -zxvf deplos_install_v1.3.3.tar.gz
cd deplos_install_v1.3.3/
~~~

### 2. 一键安装
~~~bash
sudo ./install
~~~

### 3. 访问控制台
通过浏览器访问：`http://<服务器IP>:9100` (默认账号/密码：`admin`/`hrnrkit`)

---

## 🧩 功能概览

### 1. 全栈硬件监控 (Nexus Monitor)
具备自我感知能力的监控大屏。以真实故障场景经验为指导，强化了 GPU 显存及硬件微损场景的深度分析能力。

### 2. 自动化交付流水线 (Delivery Orchestration)
为大规模裸金属设计的"交付指挥部"。自动串联：**BOM比对 -> BMC强制策略配置 -> RAID组建 -> 硬件72小时压测 -> 自动生成报告 -> 离线OS安装**。

### 3. 自动化 OS 安装 (Visual Config)
告别盲装。安装前自动扫描物理磁盘，支持可视化配置 RAID (0/1/5/10) 及网络 Bond 模式。**针对信创环境优化，移除在线源，默认采用 ISO 离线模式。**

### 4. GPU 深度压力测试 (GPU Stress Test)
针对 HPC 与 AI 算力集群设计。对显卡计算核心及显存颗粒执行高强度验证，支持显存泄漏排查及极限稳定性评估。

### 5. 高效系统运维 (System Ops)
集成 WebSSH 终端与批量脚本控制台。**新增对 ESXi 子机的识别**，支持直接从 DeplOS 运维中心拉起子机控制窗口。

### 6. 物理磁盘定位 (Disk Locator)
无需安装 Agent，直接通过底层指令点亮 LED 灯，支持 **NVMe、RAID 及 HBA 直通盘**，解决现场运维拔错盘的痛点。

---

## 📥 下载与更新

| 版本类型 | 说明 | 下载链接 |
| :--- | :--- | :--- |
| **📦 Full (全量包)** | 包含完整依赖与基础镜像，适用于**全新离线安装**。 | [GitHub Release](https://github.com/hrnr27/DeplOS/releases) |
| **⚡ Update (更新包)** | 仅包含核心程序与 Web 资源，适用于 v1.x **平滑升级**。 | [GitHub Release](https://github.com/hrnr27/DeplOS/releases) |

---

## 💬 社区与支持

- **官方 QQ**: `759419595`
- **微信公众号**: `Linux客栈`
- **邮件支持**: <support@hrnrkit.cn>

<p align="center">
  <sub>Made with ❤️ by DeplOS Team. 赋能数据中心智能运维。</sub>
</p>
