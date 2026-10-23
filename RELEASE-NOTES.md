# H618 Armbian (Debian 12) USB Flash Image

Armbian based on **Debian 12.15**, with **Linux 6.12.114** and ported/optimized Allwinner BSP eMMC HS400 logic. **200MHz HS400** operation passed read/write integrity and reboot tests on the supported board.

- H618, 4GB DDR3 + 256GB eMMC, RTL8211F Gigabit Ethernet.
- Automatic first-boot expansion; system and data share the root filesystem.
- Use **PhoenixUSBPro_V4.1.0**. On an early unlockable public-release box, leave DC power disconnected, hold reset, and connect a USB-A to USB-A data cable. Release reset after flashing begins and wait for completion.
- Extract `.img.xz` to `.img` before flashing. Back up data first; flashing overwrites it.
- Initial login: `root` / `123456`; change the password after login.

256GB hardware tested; 128GB hardware validation pending. See the English or Chinese README for the full steps.
