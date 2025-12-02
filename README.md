<!-- GitHub README.md for hrnr27/HrnrKitOS -->
<p align="center">
  <img src="docs/hrnrkitos_logo.svg" alt="HrnrKitOS Logo" width="180"/>
</p>

<h1 align="center">HrnrKitOS PXE Nexus v1.2.0</h1>

<p align="center">
  <strong>面向一线运维工程师的企业级裸金属自动化运维平台</strong><br/>
  一键 PXE 启动 · 自动化 OS 安装 · 物理磁盘定位 · 深度硬件诊断 · 跨机房网段启动
</p>

<p align="center">
  <a href="https://github.com/hrnr27/HrnrKitOS/releases">
    <img src="https://img.shields.io/github/v/release/hrnr27/HrnrKitOS?style=flat-square&label=Release&logo=github"/>
  </a>
  <a href="https://github.com/hrnr27/HrnrKitOS/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/hrnr27/HrnrKitOS?style=flat-square&label=License"/>
  </a>
  <img src="https://img.shields.io/badge/Platform-x86__64-lightgrey?style=flat-square"/>
</p>

---

<details open>
<summary>📑 目录</summary>

- [核心亮点](#-核心亮点)
- [快速开始](#-快速开始)
- [功能详解](#-功能详解)
- [内置工具清单](#-内置工具清单)
- [下载与校验](#-下载与校验)
- [常见问题](#-常见问题)
- [贡献与反馈](#-贡献与反馈)

</details>

---

## ✨ 核心亮点

| 特性 | 简介 |
|------|------|
| **🚀 部署** | <br>**原生Linux系统部署 (新)**：支持直接安装在 **Rocky/AlmaLinux/RHEL 8+、Fedora、Ubuntu/Debian** 等主流系统上，灵活融入现有运维环境。 |
| 🌐 **多网段并行完整服务** | 接口独立设计，可在同一主机上让多个物理网口/VLAN同时成为全功能PXE服务器，服务栈物理隔离，满足多机房、多VLAN、高规隔离场景的并行交付需求。 |
| ⚙️ **自动化 OS 安装** | 支持 Kickstart/Preseed，模板化部署 RHEL/Ubuntu/SUSE 等主流系统，集成IPMI自动引导与Web流程驱动。 |
| 🔬 **深度硬件诊断** | **新增CPU深度诊断与专业烤机功能**，提供处理器全方位健康洞察与极限稳定性测试。 |
| 💾 **全系存储配置** | **增强RAID卡支持**，现可便捷配置管理 RAID 0, 1, 5, 10, 50, 60 等全系列别。 |
| 🛠️ **智能带外管理** | **新增恢复出厂设置、修改BMC密码功能**，并与系统安装流程智能关联，实现零接触运维。 |
| 💡 **物理磁盘定位** | 远程Web点灯，精准定位SAS/SATA/NVMe硬盘，**新增对直通(Pass-Through)硬盘的支持**。 |
| 📊 **资产信息管理** | **完善硬件信息采集，并支持一键导出为Excel报告**，便于存档与分析。 |

---

## 🚀 快速开始
![hrnrkit-home](docs/home.png)

### 1) 原生Linux系统部署
您可以将HrnrKitOS服务端直接安装到您现有的Linux服务器环境中。

1.  **环境要求**：
    *   **支持的系统**：Rocky Linux 8+, AlmaLinux 8+, RHEL 8+, Fedora, Ubuntu/Debian等。
    *   **网络**：建议配置两个网络接口，一个用于管理，一个专用于PXE服务。
    *   **存储**：需要准备一个独立分区或硬盘（≥100GB）用于存储数据。

2.  **安装与启动**：
    ```bash
    # 请在此处替换为实际的安装包名和安装命令
    # 例如：tar -zxvf hrnrkitos-nexus-v3.4.0.tar.gz && cd hrnrkitos-nexus-v3.4.0 && ./install.sh
    ```
    安装程序将引导您完成配置并自动设置服务。完成后，通过浏览器访问 `http://<服务器IP>:8080` 即可进入Web管理界面。
---

## 🛠️ 功能详解

### 1. 🌐 多网段并行完整服务
![multi-segment](docs/nc_multi_subnet.png)
- **接口独立设计**：同一主机上任意物理网口/VLAN均可同时成为「全功能PXE服务器」，各自独享DHCP/TFTP/HTTP/DNS服务栈，零交叉、零中继。
- **标签驱动配置**：支持 **PXE网络**（完整引导）、**业务网络**（仅分配IP）、**通用网络**（仅本机静态IP）三种模式。
- **典型场景**：适用于多机房并行装机、异构VLAN批量交付、生产/管理/实验网物理隔离等高规需求。

### 2. ⚙️ 企业级自动化OS安装
![os-install](docs/ipxe_tutorial_end.png)
- **模板化部署**：支持主流操作系统的Kickstart, Preseed/Autoinstall模板。
- **Web全流程**：从ISO上传、模板管理到安装进度监控，全程Web化。
- **带外集成**：可结合IPMI自动远程开机并引导至PXE安装流程。
- **交互式磁盘配置**：在安装前，通过Web界面为服务器直观选择安装目标盘。

### 3. 🔬 深度硬件诊断与压测
![hardware-test](docs/nvidia_test_done.png)
- **专业压测套件**：提供CPU、内存、硬盘、网络、GPU的专业压力测试。
- **CPU深度诊断 (新)**：新增处理器深度诊断功能，提供健康状态与性能洞察。
- **专业CPU烤机 (升级)**：升级极限稳定性测试，检验系统在高负载下的可靠性。
- **智能健康分析**：深入解读硬盘SMART、RAID卡事件、BMC日志，预警潜在故障。
- **一站式日志采集**：一键打包所有关键硬件组件的日志，加速故障排查。

### 4. 💾 全系存储配置与管理
- **增强RAID配置支持 (新)**：全面支持RAID 0, 1, 5, 10, 50, 60等级的便捷配置与管理。
- **物理磁盘定位**：自动映射Linux块设备到物理插槽，提供统一的“点亮/熄灭”操作，**新增对直通硬盘的点灯支持**。
- **固件升级**：支持LSI/Broadcom RAID/HBA卡固件在线升级。

### 5. 🛠️ 智能带外(BMC/IPMI)管理
- **新增功能**：
    - **恢复出厂设置**：一键复位BMC/iBMC配置。
    - **修改BMC密码**：直接在平台内安全更新带外管理密码。
- **核心功能**：远程开/关机、重启、设置引导项，实现零接触运维。
- **流程关联**：增强与系统安装流程的智能关联。

### 6. 📊 资产管理与报告
- **完善硬件采集 (新)**：采集更全面、准确的硬件资产信息。
- **导出Excel报告 (新)**：支持将硬件信息一键导出为Excel文件，便于数据分析与存档。
- **优化压测报告样式 (新)**：硬件压力测试报告视觉升级，数据呈现更直观。

### 7. 🔌 兼容性增强
- **支持更多Linux系统部署 (新)**：可原生安装于主流Linux发行版。
- **优化IPXE兼容性 (新)**：增强对各类网卡的兼容性，提升网络引导成功率。

---

## 🧰 内置工具清单
> 共 38+ 个，按场景分类

| 类别 | 工具 |
| --- | --- |
| **存储管理** | `storcli64`, `perccli64`, `MegaCli64`, `smartctl`, `sas3flash`, `sas2flash`, `sas3ircu`, `arcconf` |
| **网络配置** | `mlxconfig`, `mstflint`, `mlxfwmanager`, `bnxtnvm`, `bootutil64e`, `Yafuflash` |
| **GPU 管理** | `nvidia-smi`, `fieldiag` |
| **带外管理** | `ipmitool`, `hponcfg`, `ssacli`, `smcipmitool`, `racadm` |
| **诊断与压测** | `dmidecode`, `turbostat`, `lshw`, `nvme-cli`, `stress-ng`, `memtester`, `fio`, `iperf3` |
| **BIOS/固件** | `fwupd`, `afu`, `afudos`, `afuefi` |
| **其他** | `gdisk`, `partclone`, `ddrescue` |

---

## 📥 下载与校验

| 渠道 | 链接 | 说明 |
| --- | --- | --- |
| **GitHub Releases** | [hrnr27/HrnrKitOS/tags](https://github.com/hrnr27/HrnrKitOS/tags) | 获取最新版本的 **Live ISO** 及 **原生部署安装包**。 |
| **百度网盘** | [pan.baidu.com](https://pan.baidu.com/s/1KbVnL3QcYzq6I7MMeqwNjw) 提取码 `3bqf` | 备用下载渠道。 |

> **请注意**：从 v3.4.0 开始，我们提供 **Live ISO** 和 **Linux原生安装包** 两种格式，请根据您的部署需求选择下载。

---

## ❓ 常见问题
<details>
<summary>Q: 现在支持哪些部署方式？</summary>
A: 目前支持两种部署方式：1) **传统 Live ISO 模式**，解压即用；2) **原生Linux系统部署**，可直接安装在 Rocky/AlmaLinux/RHEL 8+、Fedora、Ubuntu/Debian 等系统上，更灵活地融入现有环境。
</details>

<details>
<summary>Q: 如何重置 BMC 密码？</summary>
A: 在 Web UI 选中目标主机 → 更多操作 → BMC 密码重置。该功能已在新版本中增强，支持更多品牌。
</details>

<details>
<summary>Q: 是否支持 UEFI 启动？</summary>
A: 支持 Legacy BIOS 与 UEFI 双模式启动。
</details>

<details>
<summary>Q: 如何导出硬件信息报告？</summary>
A: 在硬件信息采集页面，点击“导出”按钮即可生成 Excel 格式的详细报告。
</details>

---

## 🤝 贡献与反馈
- 📧 **邮件**: <support@hrnrkit.cn>
- 🐛 **Issue**: [GitHub Issues](https://github.com/hrnr27/HrnrKitOS/issues)
- 💡 **PR**: 欢迎提交代码补丁、文档改进或新工具集成！

---

<p align="center">
  <sub>HrnrKitOS PXE Nexus — 让裸金属服务器运维更简单、更智能、更高效！</sub>
</p>
