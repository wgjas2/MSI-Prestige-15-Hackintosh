# MSI Prestige 15 Hackintosh

该项目为使用OpenCore引导MSI Prestige 15 32G 1TB 4K版笔记本黑苹果的EFI实例，OpenCore版本为0.6.3，适配Catalina(10.15.x)及Big Sur(11.0.x)，因为更换了无线网卡，所以提供原配AX201和替换DW1830两个版本的配置文件，请根据需要自行选择config文件进行引导。

## 硬件驱动说明

| 类型               | 型号                                  | 备注                      |
| ------------------ | ------------------------------------- | ------------------------- |
| Model              | MSI Prestige 15 A10SC                 |                           |
| CPU                | Intel i7-10710U                       |                           |
| IGPU               | Intel Graphics UHD 620                |                           |
| DGPU               | Nvidia GTX1650 Max-Q                  | **无法驱动，已SSDT禁用**  |
| Display            | Sharp SHP14A1 15.6' 3840x2160(4K)     |                           |
| RAM                | Samsung DDR4 2666MHz 16GB x2          |                           |
| SSD1               | Western Digital SN730 1TB             |                           |
| SSD2               | Western Digital SN750 1TB             | 增配                      |
| Audio              | Reltek ALC298                         |                           |
| Wireless           | Boardcom DW1830 (BCM943602BAED) WIFI5 | 原配为 Intel AX201 WIFI 6 |
| Bluetooth          | Boardcom BCM2045A0 BT4.1              | 原配为 Intel AX201 BT5.1  |
| Card Reader        | Realtek RTS5250 PCI-E                 | **无法驱动**              |
| Fingerprint Reader | Synaptics WBDI                        | **无法驱动**              |

- BIOS版本：E16S3IMS.108

## 提示

- 在BIOS中关闭安全引导。
- 在BIOS中关闭CFG Lock（需要进入隐藏菜单，在BIOS中，先按住ALT + 右CTRL + 右SHIFT，然后按下(FN)F2可以打开隐藏菜单），该项目在隐藏菜单的Advanced->power & Performance ->CPU - Power Management Control ->CPU lock Configuration ->CFG lock部分。
- 本例包含Clover和OC两个引导，Boot文件夹中BOOTx64.efi是OC的（因为OC必须要从这里引导）；在将OC和Clover添加到EFI启动项的时候，OC的引导文件选择/EFI/Boot/BOOTx64.efi，而Clover则选择/EFI/Clover/CLOVERX64.efi。
- 请自行重新生成config.plist中的序列号、主板序列号、SmUUID等信息，如果Clover和OC需要一起用，那么保证两者的信息一致，** 升级config的时候切记不要覆盖这些信息 ** 。
- 本例中提供两个网卡版本的EFI（文件名区分），一个是机器原配的AX201无线网卡，另一个是自己更换DW1830无线网卡，如果有条件建议更换，体验更好。
- **AX201 网卡需要使用Apps中的HeliPort进行连接，请自行解压拖入Applications食用！**

## 附加修复

- 耳机有杂音问题，使用ComboJack进行可选择切换，终端进入Attach/ComboJack/，执行 `./install.sh` 安装。
- OC下声卡外放可能有启动无声或者唤醒无声问题，**如果经常无声可以尝试**安装JackFix解决声卡重启问题，终端进入OC-Attach/JackFix/，执行 `sudo ./install.command` 安装（已经修改好声卡节点）。
- 以上两个修复需要 VertStub.kext 驱动，已经加入Clover和OC，安装完后务必重启。

## 未测试组件

- Thunderbolt 3，**Type-C口以及视频输出正常(HDMI)**，手头没有TB3设备，无法测试

## 已知问题

- **BigSur下内置屏幕无法使用4K60Hz完整帧率驱动，固使用修改原始EDID降低刷新率为48Hz后驱动（目前无法解决4K内屏60Hz问题），如果无法接受，请不要升级BigSur！！！**
- 触摸板偶尔可能失灵（键盘驱动防误触造成的，可通过按两次Win+Prtscr恢复）
- 蓝牙丢失问题，丢失后在Windows中也不可见，需要关机拔电源后静置几秒再开机可解决（硬件问题，正常开关机不会出现）

## 参考
- https://github.com/hla63/Msi-modern-15-Hackintosh
- https://github.com/KerKerOgh/MSI-Prestige-15-Hackintosh
- https://github.com/daliansky/XiaoXinPro-13-hackintosh
- https://github.com/daliansky/OC-little
- https://dortania.github.io/OpenCore-Install-Guide/

## 驱动

- https://github.com/acidanthera/OpenCorePkg
- https://github.com/acidanthera/Lilu
- https://github.com/acidanthera/VirtualSMC
- https://github.com/acidanthera/AppleALC
- https://github.com/acidanthera/WhateverGreen
- https://github.com/acidanthera/AirportBrcmFixup
- https://github.com/acidanthera/BrcmPatchRAM
- https://github.com/acidanthera/VoodooPS2
- https://github.com/VoodooI2C/VoodooI2C
- https://github.com/acidanthera/HibernationFixup
- https://github.com/OpenIntelWireless/itlwm
- https://github.com/OpenIntelWireless/IntelBluetoothFirmware
- https://github.com/1hbb/OpenIntelWireless-Factory
- https://github.com/al3xtjames/NoTouchID
- https://github.com/acidanthera/CPUFriend
- https://github.com/acidanthera/NVMeFix
- https://github.com/hackintosh-stuff/ComboJack
- https://github.com/fewtarius/jackfix