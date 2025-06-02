# HrnrKitOS 服务器/Linux运维工具盘 v3.1.0 发布说明


## 产品概述

HrnrKitOS 是一款面向一线运维工程师的**免费全能运维工具盘**。它集成了主流品牌服务器的维护工具，包括 RAID/HBA 卡管理、网卡固件管理、PXE 网络启动及网络配置等实用功能，致力于显著提升服务器运维效率。

![HrnrKitOS iPXE 主界面](https://github.com/hrnr27/HrnrKitOS/blob/main/HrnrKitOSpxe%E7%BB%B4%E6%8A%A4%E7%B3%BB%E7%BB%9F.png)

## v3.1.0 主要更新

*   **新增 PXE 远程维护系统：** 支持服务器通过网络启动工具盘，无需再为每台服务器插拔 U 盘。
*   **新增硬件信息采集功能：** 支持批量收集服务器硬件配置信息，并可导出为 CSV 文件。
*   **新增 BMC/iLO 密码重置工具：** 支持远程或本地恢复默认密码（默认密码：`Aa?123456`）。
*   **新增 Supermicro BIOS 激活码计算工具：** 直接在超微主板上运行即可生成 BIOS 激活码。
*   **新增工具：** MegaCli64, storcli64（至此，工具总数已达 **32 个**）。
*   **修复：** Mellanox 网卡工具 `mst` 加载问题（感谢用户 @幸福人生 反馈）。
*   **优化：** 系统性能与数据迁移工具。
*   **调整：** 移除了旧版 PXE 系统安装服务工具（如有需要请单独下载HrnrPxe_server_install到HrnrKitOS下使用）。

## 技术参数

*   **镜像文件：** `HrnrKit-System-3.1.0-x86_64.iso` (237MB)
*   **SHA-256 校验值：**
    ```
    fd641b02fc2e76c7d3287bda5898fd65a294af6792e1e0e55ec3651f6faab8de
    ```
*   **启动支持：** Legacy BIOS / UEFI 双模式
*   **自动挂载：** 工具盘载体 U 盘将自动挂载至 `/mnt`
*   **系统登录密码：** `000000` *(请注意安全)*

## PXE 远程维护功能详解 (v3.1.0 核心特性)

*   **无物理介质：** 服务器通过 PXE 网络启动加载 HrnrKitOS 工具盘。
*   **批量硬件采集：** 支持远程收集多台服务器的硬件配置信息。
*   **远程 SSH 管理：** PXE 服务端可直接 SSH 连接到启动后的客户端服务器进行操作。
*   **支持离线安装的操作系统：**
    *   Debian: 10.13 / 11.11 / 12.7
    *   Ubuntu: 20.04 - 24.04 (桌面版/服务器版)
    *   Deepin: 20.9 / 23
    *   RHEL 系: CentOS / Rocky Linux / RHEL 7 - 9
    *   Fedora: 39 / 40
    *   openEuler

## 内置硬件工具列表 (精选)

涵盖主流服务器厂商的关键维护工具：

*   **存储管理：** storcli64, perccli64, MegaCli64, smartctl, sas3flash, sas2flash, sas3ircu, arcconf
*   **网络配置：** Mellanox (mlxconfig, mstflint/flint, mlxfwmanager), Broadcom (bnxtnvm), Intel (bootutil64e, Yafuflash)
*   **带外管理 (BMC/iLO/iDRAC)：** ipmitool, HPE (hponcfg, ssacli), Supermicro (afulnx, smcipmitool), Dell (racadm)
*   **诊断与信息：** dmidecode, turbostat, lshw, nvme-cli
*   **BIOS/固件：** fwupd, afu (AMI), afudos (AMI), afuefi (AMI)
*   **其他实用工具：** memtester, stress-ng, gdisk, partclone, ddrescue

*(工具总数：32 个)*

## 使用说明

1.  **工具入口：** 所有功能集成于 `/toolkit/HrkitStresk` 目录。启动系统后，运行 `HrkitStresk` 脚本即可调用工具菜单界面。
2.  **U 盘可移除：** 系统完全启动至内存后，即可拔出 U 盘，工具运行不受影响。
3.  **PXE 配置：** 在选择PXE 功能后，根据提示设置服务端的网络参数（IP、DHCP范围等），然后启动 PXE 服务。

## 问题反馈与下载

*   **反馈与建议：**
    *   邮箱：hrnr27@outlook.com
    *   *(请注意：作者通常每 1-3 周查看一次邮件，回复可能略有延迟，但所有邮件都会被处理)*
*   **下载地址：**
    *   百度网盘： [https://pan.baidu.com/s/1KbVnL3QcYzq6I7MMeqwNjw](https://pan.baidu.com/s/1KbVnL3QcYzq6I7MMeqwNjw) 提取码：`3bqf`
    *   github: https://github.com/hrnr27/HrnrKitOS/tags

---

**HrnrKitOS - 让服务器运维更简单高效！**
