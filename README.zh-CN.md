# H618 Armbian（Debian 12）USB 线刷镜像

[English](README.md) | [简体中文](README.zh-CN.md)

**基于 Debian 12.15 Bookworm 的 Armbian，运行 Linux 6.12.114 内核。** 已为该 H618 主板移植并优化全志 BSP 的 eMMC HS400 相关驱动逻辑，**200MHz HS400** 模式通过读写完整性和重启测试。使用 **PhoenixUSBPro_V4.1.0** 直接线刷进入 eMMC。

## 设备与系统参数

| 项目 | 参数 |
|---|---|
| 芯片 | Allwinner H618，ARM64 |
| 内存／存储 | **4GB DDR3＋256GB eMMC** |
| 主板型号 | B00-HX3-REV1.6-F |
| 网卡 | **Realtek RTL8211F 千兆网口** |
| 系统 | **Armbian，基于 Debian 12.15 Bookworm** |
| 内核 | **6.12.114-h618-hs400-r11i** |
| 存储驱动 | 在 Linux 6.12.114 上移植并优化全志 BSP HS400 相关逻辑 |
| eMMC | **200MHz HS400、8bit、1.8V**，启动自动调参 |
| 空间 | 首次自动扩容，系统与数据共用根分区 |
| TF 卡座 | 未焊接 |
| 网络 | DHCP 自动获取地址 |
| 镜像初始登录 | 用户 `root`，密码 `123456`，登录后请修改 |
| Docker | 未预装 |

256GB 已实机验证；128GB 待实机验证。其他主板、批次及锁定版本需分别确认适配。

![H618 主板](assets/board-h618.jpg)

## 镜像下载

[下载镜像及 SHA256 校验文件](https://github.com/niko188899/h618-armbian-phoenix-usb-flash/releases/tag/r11i-debian12)。

文件：**`H618-Armbian-USB-Flash.img.xz`**，约603MB。下载后解压为 `.img` 再刷写。

## 刷写步骤

**前提：机顶盒是前期可解锁的公开版，能够长按重置键进入 USB 烧录模式。**

1. 备份需要保留的数据，完整线刷会覆盖原系统和数据。
2. 打开 **PhoenixUSBPro_V4.1.0**，载入解压后的 `.img`，启动烧录检测。
3. 盒子**不接 DC 电源**，**长按重置键**，用 **USB-A 对 USB-A 双头 USB 数据线**连接电脑和盒子的烧录 USB 口。
4. 软件识别设备并开始烧录后松开重置键，等待写入成功。
5. 拔掉双头 USB 线，接网线，再接 DC 电源正常启动。
6. 等待首次自动扩容完成，到路由器 DHCP 列表查找地址，再通过 SSH 登录。

烧录 USB 口和重置键位置按对应主板确认。
