# SurfacePro4-Hackintosh
Surface Pro 4 自用黑苹果文件整理，还有很多小问题，不建议日常使用，仅供参考。

## 环境简介
* Surface Pro 4: i5-6300U / 8G / HD520
* macOS 版本: High Sierra (10.13)

## 注意事项
1. 10.13 后不再需要 patch-nvme 补丁。
2. 在安装或更新系统时，需要把 ig-platform-id 改成一个无效 id（0x12345678），否则会卡 AppleIntelSKLGraphicsFramebuffer。成功进入系统后再将修改过的 AppleIntelSKLGraphicsFramebuffer.kext 文件放入S/L/E下，然后修复缓存即可。
3. OTA 升级时会报错（macOS could not be installed on your computer），故暂时只支持全新安装或下载完整系统镜像进行升级。
4. CodecCommander 须安装在 S/L/E 目录下，若放在 EFI/kexts下会导致系统更新时无限重启。
5. 我在 config.plist 的 SMBIOS 中修复了内存频率显示不正确的问题，如果不是 8G 内存，需要手动修改成自己的配置。

## 正常工作
1. 显卡正常驱动，HiDPI 正常开启。目前 IntelGraphicsFixup 项目已经并入 WhateverGreen 中，故添加 WhateverGreen.kext 即可直接驱动显卡，无需再注入 ig-platform-id。
2. 亮度调节正常。
3. 声卡 ALC298 正常使用（使用 AppleALC.kext，并在 config.plist 中注入声卡 id 为 3 即可驱动），使用 CodecCommander.kext 解决唤醒无声问题。
4. TF卡正常识别（使用 GenericUSBXHCI.kext 可直接驱动）。
5. 睡眠唤醒正常。
6. CPU 变频正常。
7. USB 3.0 正常工作。
8. Type Cover 可以使用，音量调节等快捷键均正常工作。

## 有什么问题
1. 触屏、Wi-Fi、蓝牙、摄像头等无解，个人选择使用 USB 网卡上网。
2. Type Cover 的触摸板没有手势操作，不支持热插拔，应该也无解。
3. 机身按钮均不可用（除了长按电源键强制关机外）。
4. 电量无法正常显示（RehabMan 的 Surface Pro 4 DSDT Patch 在 10.13 下无法正常编译通过）。
5. 合盖可睡眠，但唤醒后会进入一个“没睡醒”的状态（保持为最低亮度，且隔一段时间就会自动睡眠），该问题在 10.12 时就已存在，至今没找到解决方法。
6. 偶尔会有一些画面撕裂和花屏的问题（如刚进入系统时），很快能恢复正常，不影响正常使用。
7. 进入系统会出现屏幕泛白问题，个人推测是显卡驱动的问题。

## 更新日志
#### 2018-09-09:
- 支持 10.13.6 系统。
- 更新 Lilu 至 1.2.6 版本。
- 添加 WhateverGreen.kext。

#### 2018-06-06:
- 支持 10.13.5 系统。
- 更新 Lilu 至 1.2.4 版本。
- 删除 IntelGraphicsFixup.kext。

#### 2018-03-31:
- 支持 10.13.4 系统。

## 效果图
<img src="https://github.com/Neil-Steven/SurfacePro4-Hackintosh/blob/master/Screenshots/Screenshot_20180331-173553.jpg" width="684" height="456" />

## 感谢
* [vit9696](https://github.com/vit9696): [AppleALC](https://github.com/vit9696/AppleALC), [Lilu](https://github.com/vit9696/Lilu)
* [RehabMan](https://github.com/RehabMan): [OS-X-Clover-Laptop-Config](https://github.com/RehabMan/OS-X-Clover-Laptop-Config), [EAPD-Codec-Commander](https://github.com/RehabMan/EAPD-Codec-Commander), [OS-X-Generic-USB3](https://github.com/RehabMan/OS-X-Generic-USB3)
* [lvs1974](https://github.com/lvs1974): [IntelGraphicsFixup](https://github.com/lvs1974/IntelGraphicsFixup)
* [BarbaraPalvin](https://github.com/BarbaraPalvin): [IntelGraphicsDVMTFixup](https://github.com/BarbaraPalvin/IntelGraphicsDVMTFixup)
* [Lunaleeguo](https://github.com/Lunaleeguo): [Surface-Pro-4-Sierra](https://github.com/Lunaleeguo/Surface-Pro-4-Sierra)
* [yudongwei](http://i.pcbeta.com/space-uid-918890.html): [new surface pro2017 i5 7300u hd620 款10.13.3的efi分享](http://bbs.pcbeta.com/viewthread-1778486-1-2.html)
