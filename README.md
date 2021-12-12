# MSI Prestige 15 Hackintosh

该项目为使用OpenCore引导MSI Prestige 15 32G 1TB 4K版笔记本黑苹果的EFI实例，OpenCore版本为0.7.6，适配Big Sur(11.0.x-11.6.x)、Monterey(12.0.1)。

## 硬件驱动说明

| 类型               | 型号                              | 备注                     |
| ------------------ | --------------------------------- | ------------------------ |
| Model              | MSI Prestige 15 A10SC             |                          |
| CPU                | Intel i7-10710U                   |                          |
| IGPU               | Intel Graphics UHD 620            |                          |
| DGPU               | Nvidia GTX1650 Max-Q              | **无法驱动，已SSDT禁用** |
| Display            | Sharp SHP14A1 15.6' 3840x2160(4K) |                          |
| RAM                | Samsung DDR4 2666MHz 16GB x2      |                          |
| SSD1               | Western Digital SN730 1TB         |                          |
| SSD2               | Western Digital SN750 1TB         | 增配                     |
| Audio              | Reltek ALC298                     |                          |
| Wireless           | Intel AX201 WIFI 6                |                          |
| Bluetooth          | Intel AX201 0x80870026 BT5.1      |                          |
| Card Reader        | Realtek RTS5250 PCI-E             | **无法驱动**             |
| Fingerprint Reader | Synaptics WBDI                    | **无法驱动**             |

- BIOS版本：E16S3IMS.108

## 提示

- 在BIOS中关闭安全引导。
- 在BIOS中关闭 CFG Lock（需要进入隐藏菜单，在BIOS中，先按住ALT + 右CTRL + 右SHIFT，然后按下(FN)F2可以打开隐藏菜单），该项目在隐藏菜单的Advanced->power & Performance ->CPU - Power Management Control ->CPU lock Configuration ->CFG lock部分。
- 在BIOS中关闭 VT-d 选项。
- 请自行重新生成config.plist中的序列号、主板序列号、SmUUID等信息，如果Clover和OC需要一起用，那么保证两者的信息一致，**升级config的时候切记不要覆盖这些信息**。

## 附加修复

- 耳机有杂音问题，使用ComboJack进行可选择切换，终端进入Attach/ComboJack/，执行 `./install.sh` 安装。

## 未测试组件

- Thunderbolt 3，**Type-C口以及视频输出正常(HDMI)**，手头没有TB3设备，无法测试

## 已知问题

- Type-C 1口无法识别USB2.0设备 (2口正常)，造成的后果是部分Type-C 扩展坞的USB口无法识别2.0设备
- 蓝牙丢失问题，丢失后在Windows中也不可见，需要关机拔电源后静置几秒再开机可解决（硬件问题，正常开关机不会出现）
- 从Windows重启进入macOS后外放无声，完全关机后重新按电源键启动后恢复

## 参考
- https://github.com/hla63/Msi-modern-15-Hackintosh
- https://github.com/KerKerOgh/MSI-Prestige-15-Hackintosh
- https://github.com/daliansky/XiaoXinPro-13-hackintosh
- https://github.com/daliansky/OC-little
- https://dortania.github.io/OpenCore-Install-Guide/

## 驱动

- https://github.com/acidanthera/OpenCorePkg
- https://github.com/acidanthera/OcBinaryData
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