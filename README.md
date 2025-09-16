<!-- GitHub README.md for hrnr27/HrnrKitOS -->
<p align="center">
  <img src="docs/hrnrkitos_logo.svg" alt="HrnrKitOS Logo" width="180"/>
</p>

<h1 align="center">HrnrKitOS PXE Nexus v3.3.1</h1>

<p align="center">
  <strong>面向一线运维工程师的企业级裸金属自动化运维平台</strong><br/>
  一键 PXE 启动 · 自动化 OS 安装 · 物理磁盘定位 · 深度硬件诊断
</p>

<p align="center">
  <a href="https://github.com/hrnr27/HrnrKitOS/releases">
    <img src="https://img.shields.io/github/v/release/hrnr27/HrnrKitOS?style=flat-square&label=Release&logo=github"/>
  </a>
  <a href="https://github.com/hrnr27/HrnrKitOS/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/hrnr27/HrnrKitOS?style=flat-square&label=License"/>
  </a>
  <img src="https://img.shields.io/badge/ISO-935MB-blue?style=flat-square"/>
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
| --- | --- |
| ⚙️ **自动化 OS 安装** | **(全新)** 支持 Kickstart/Preseed, 模板化部署 RHEL/Ubuntu/SUSE |
| 💡 **物理磁盘定位** | **(全新)** 远程 Web 点灯，精准定位 SAS/SATA/NVMe 硬盘，告别拔错盘 |
| 🖥️ **Web UI 管理平台** | 集中化图形界面，实时监控与批量管理所有 PXE 客户端 |
| 🔬 **深度诊断与压测** | 一键硬件健康检查、日志采集、压力测试 (CPU/内存/硬盘/GPU) |
| 🔌 **带外管理 (IPMI)** | 远程开/关机、重启、设置引导项 (PXE/BIOS)，实现零接触运维 |
| 🔧 **38+ 专业工具集** | 全面覆盖存储、网络、GPU、BMC、BIOS 等主流品牌控制器 |

---

## 🚀 快速开始
![hrnrkit-home](docs/home.png)

### 1) 笔记本/虚拟机中部署 (推荐)
1.  **启动 ISO**: 在 VirtualBox/VMware 中启动 `HrnrKit-System-v3.3.1-x86_64.iso`
    -   网卡1: NAT (用于访问互联网)
    -   网卡2: 桥接 (用于 PXE 客户端网络)
2.  **访问 Web UI**: 浏览器打开 `http://<服务器IP>:8080`
3.  **客户端上线**: 将目标服务器网卡设为 PXE 启动，即可自动加载 HrnrKitOS 并出现在 Web 界面
4.  **(可选) 命令行**: 终端执行 `/toolkit/HrnrkitStresk` 进入传统工具菜单

### 2) U盘/物理服务器部署
-   系统启动后完全加载至内存，U 盘可安全拔除
-   配置好网络后，即可作为 PXE 服务端使用

---

## 🛠️ 功能详解

### 1. ⚙️ 企业级自动化 OS 安装 (全新)
![os-install](docs/ipxe_tutorial_end.png)
-   **模板化部署**: 支持主流操作系统 (RHEL/CentOS, Ubuntu/Debian, SUSE) 的 Kickstart, Preseed/Autoinstall 模板。
-   **Web 流程驱动**: 从 ISO 上传、模板管理、任务创建到进度监控，全程 Web 化，实现无人值守安装。
-   **IPMI 自动引导**: 深度集成带外管理，可自动远程开机并引导服务器进入 PXE 安装流程。
-   **安装后脚本 (Post-install)**: 自动执行初始化脚本，完成主机名、网络、软件源等配置。
-   **交互式磁盘配置**: 在安装前，通过 Web 界面为服务器直观地选择安装目标盘。

### 2. 💡 物理磁盘定位 (Web 点灯) (全新)
![drive-locate](docs/placeholder_locate_drive.png) <!-- 提示：请替换为真实截图 -->
-   **精准映射**: 自动关联 Linux 块设备 (`/dev/sdX`) 与其物理**插槽号 (Slot)** 和**序列号 (SN)**。
-   **统一操作**: 抽象化硬件厂商底层命令，提供统一的“点亮/熄灭”按钮，屏蔽硬件差异。
-   **支持异构存储**: 无论是 RAID 卡后的 SAS/SATA 盘，HBA 直通卡，还是主板直连的 NVMe 盘，都能被准确识别并点亮。

### 3. 🖥️ 集中化 Web 管理
![webui-dashboard](docs/Client.png)
-   **实时监控**: 客户端 IP / MAC / 在线状态一目了然。
-   **批量操作**: 支持对在线客户端执行统一的重启、关机、信息采集等任务。
-   **带外管理 (OOB)**: 集成强大的 IPMI 功能，实现远程开关机、设置引导项等“零接触”操作。
-   **设备信息管理**: 支持批量导入服务器编号、MAC 及 IPMI 凭证，简化设备初始化流程。

### 4. 🔬 深度硬件诊断与健康分析
![hardware-test](docs/nvidia_test_done.png)
-   **压力测试套件**: 提供 CPU, 内存, 硬盘, 网络, GPU 的专业压力测试，支持实时监控和 PDF 报告导出。
-   **智能健康分析**: 深入解读硬盘 SMART、RAID 卡事件、网卡状态和 BMC 日志，提前预警潜在故障。
-   **一站式日志采集**: 一键打包所有关键组件 (RAID/GPU/HBA/NIC/BMC) 的日志，加速故障排查。

### 5. ⬆️ 固件升级与维护
![firmware-upgrade](docs/raidupdate.png)
-   **存储控制器升级**: 支持 LSI/Broadcom RAID 卡和 HBA 卡固件在线升级，提供实时进度反馈。
-   **BIOS 工具集**: 内置 AMI BIOS 刷写工具 (`afu`, `afudos`, `afuefi`)，满足主板维护需求。

---

## 🧰 内置工具清单
> 共 38+ 个，按场景分类

| 类别 | 工具 |
| --- | --- |
| **存储管理** | `storcli64`, `perccli64`, `MegaCli64`, `smartctl`, `sas3flash`, `sas2flash`, `sas3ircu`, `arcconf` |
| **网络配置** | `mlxconfig`, `mstflint`, `mlxfwmanager`, `bnxtnvm`, `bootutil64e`, `Yafuflash` |
| **GPU 管理** | `nvidia-smi`, `fieldiag` |
| **带外管理** | `ipmitool`, `hponcfg`, `ssacli`, `smcipmitool`, `racadm` |
| **诊断信息** | `dmidecode`, `turbostat`, `lshw`, `nvme-cli` |
| **压力测试** | `stress-ng`, `memtester`, `fio`, `iperf3`, `fieldiag`|
| **BIOS/固件** | `fwupd`, `afu`, `afudos`, `afuefi` |
| **其他** | `gdisk`, `partclone`, `ddrescue` |

---

## 📥 下载与校验

| 渠道 | 链接 | 校验信息 |
| --- | --- | --- |
| **GitHub Releases** | [hrnr27/HrnrKitOS/tags](https://github.com/hrnr27/HrnrKitOS/tags) | SHA-256: `(请在此处更新为 v3.3.1 的真实哈希值)` |
| **百度网盘** | [pan.baidu.com](https://pan.baidu.com/s/1KbVnL3QcYzq6I7MMeqwNjw) 提取码 `3bqf` | HrnrKit-System-v3.3.1-x86_64.iso |

> **校验命令:** `sha256sum HrnrKit-System-v3.3.1-x86_64.iso`

---

## ❓ 常见问题
<details>
<summary>Q: 这个工具是免费的吗？</summary>
A: 是的，HrnrKitOS 对个人和商业用途完全免费。
</details>

<details>
<summary>Q: 如何重置 BMC 密码？</summary>
A: 在 Web UI 选中目标主机 → 更多操作 → BMC 密码重置。目前支持 Dell, HPE, Supermicro, Lenovo 等主流品牌。
</details>

<details>
<summary>Q: 是否支持 UEFI 启动？</summary>
A: 支持 Legacy BIOS 与 UEFI 双模式启动。
</details>

---

## 🤝 贡献与反馈
- 📧 **邮件**: <support@hrnrkit.cn> (1-3 周内回复)
- 🐛 **Issue**: 发现 Bug 或有功能建议？请到 [GitHub Issues](https://github.com/hrnr27/HrnrKitOS/issues) 提交。
- 💡 **PR**: 欢迎提交代码补丁、文档改进或新工具集成！

---

<p align="center">
  <sub>HrnrKitOS PXE Nexus — 让裸金属服务器运维更简单、更智能、更高效！</sub>
</p>
