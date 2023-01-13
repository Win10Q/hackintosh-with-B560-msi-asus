# ASUS-MSI-10-11-HACKINTOSH-OPENCORE
## 同步视频

```
https://www.bilibili.com/video/BV1Jd4y187ZS/
```
## 关于本机
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E5%85%B3%E4%BA%8E%E6%9C%AC%E6%9C%BA.png)
## 硬件列表
|项目|名称
|-|-
|CPU0|Intel 10th CORE all
|CPU1|Intel 11th CORE all
|主板1|ASUS TUF GAMING B560M PLUS WIFI
|主板2|MSI MORTAR B560M
|主板3|ASUS H510-B560 均支持（igpu需遍历
|主板4|MSI H510-B560 均支持（igpu需遍历
|显卡|AMD RX/intel uhd630（自行重命名config
|无线网卡1|AX201/200（请看驱动包）
|无线网卡2|FV-T919(BCM94360CD)
### 功能测试
- [x] 板载声卡
- [x] 板载网卡
- [x] 睡眠唤醒
- [x] CPU 变频
- [x] 所有USB端口
- [x] 接力和隔空投送
- [x] 板载蓝牙

[❌] 核显硬件加速
### 必读项目
- 华硕usb唤醒需要去掉`EFI/OC/ACPI/SSDT-GPRW`,但是本人测试风扇会唤醒不停，微星貌似没问题
- 10代的各位请把`EFI-OC`内的`config10-egpu/igpu`重命名为`config`食用
- 10代+500系要`定制hdmi`才可食用，`tuf`以及`mortar`已遍历完成，提取`edid`注入即可食用（具体请参考b站乌龙蜜桃来一打视频，简介文件也在库里哦~）
- 视频链接：https://www.bilibili.com/video/BV1UW4y1J7J2/
- 遍历后的`con`欢迎大家在`isues`的10代核显分区分享自己的`con`值哦~
### BIOS设置
#### ASUS-11th
- disable igpu（Otherwise, you will not be able to sleep normally）
- disable Intel Rapid Storage Technology
最后需要按键盘上的`F10`键保存退出即可.
#### ASUS-10th
- Disabe
- Fast Boot
- VT-d
- CSM
- Intel SGX
- CFG Lock
- Enable
- VT-x (no option in BIOS, it's enabled by default)
- Above 4G decoding
- Hyper-Threading
- EHCI/XHCI Hand-off
- OS type: Windows UEFI Mode (Clear Secure Boot Keys or choose `Other` type)
- DVMT Pre-Allocated(iGPU Memory): 64MB
最后需要按键盘上的`F10`键保存退出即可.
#### MSI-10th
- Boot -- Fast Boot -> Disabled
- Advanced -- PCH Sorage Configuration -- SATA Mode Selection -> AHCI
- Boot -- CSM(Compatibility Support Module) -> Disabled
- Ai Tweaker -- Ai Overclock Tuner -> XMP
- Advanced -- CPU configuration -- Intel Virtualization Technology -> Disabled
- Advanced -- System Agent (SA) Configuration -- VT-D -> Disabled
- Advanced -- System Agent (SA) Configuration -- Above 4G Decoding -> Disabled
- Advanced -- System Agent (SA) Configuration -- Graphics Configuration -- Primary Display -> CPU Graphics 集成显卡配置1
- Advanced -- System Agent (SA) Configuration -- Graphics Configuration -- iGPU Multi-Monitor -> Disabled 集成显卡配置2
- Advanced -- PCH configruation - IOAPIC 24-119 Entries -> Enabled
- Advanced -- PCH-FW Configuration -- TPM Device Selection -> Discrete TPM
- Advanced -- APM Configuration -- ErP Ready -> Disabled
- Advanced -- Network Stack Configuration -- Network Stack -> Disabled
- Boot -- Secure Boot -- OS Type -- Other OS
最后需要按键盘上的`F10`键保存退出即可.
#### MSI-11th
- Boot -- Fast Boot -> Disabled
- Advanced -- PCH Sorage Configuration -- SATA Mode Selection -> AHCI
- Boot -- CSM(Compatibility Support Module) -> Disabled
- Ai Tweaker -- Ai Overclock Tuner -> XMP
- Advanced -- CPU configuration -- Intel Virtualization Technology -> Disabled
- Advanced -- System Agent (SA) Configuration -- VT-D -> Disabled
- Advanced -- System Agent (SA) Configuration -- Above 4G Decoding -> Disabled
- Advanced -- System Agent (SA) Configuration -- Graphics Configuration -- Primary Display -> PCIE 独立显卡配置 1
- Advanced -- System Agent (SA) Configuration -- Graphics Configuration -- iGPU Multi-Monitor -> Enabled 独立显卡配置 2
- Advanced -- PCH configruation - IOAPIC 24-119 Entries -> Enabled
- Advanced -- PCH-FW Configuration -- TPM Device Selection -> Discrete TPM
- Advanced -- APM Configuration -- ErP Ready -> Disabled
- Advanced -- Network Stack Configuration -- Network Stack -> Disabled
- Boot -- Secure Boot -- OS Type -- Other OS
最后需要按键盘上的`F10`键保存退出即可.
### USB定制
- 从仓库下载 「Windows.exe」到 Windows 平台，双击即可运行
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E5%AE%9A%E5%88%B6-1.png)
- 输入` D `然后回车来探测电脑上的端口
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E5%AE%9A%E5%88%B6-2.png)
- 分别在各个 USB 接口插入` USB2.0 `和` USB 3.X `的设备，每插入一次停留` 5 秒钟`，如果有` Type-C `设备的话，正反都要分别插入记录
- 都挨个插一遍后，输入` B` 回车即可返回主菜单
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E5%AE%9A%E5%88%B6-3.png)
- 回到主菜单，输入` S `来查看端口探测的结果
- 此时结果查看感觉没问题的话，输入` K `回车，即可导出`UTBMap.kext`文件（一般情况下会保存在当前程序的同级目录下）
  ![image](https://user-images.githubusercontent.com/99300084/206326768-84ef300a-e64e-4978-9e30-9c955d537a28.png)
- 除了上述生成的`UTBMap.kext`文件以外，我们还需要配合`USBToolBox.kext`使用（仓库）
- 将上述两个 Kext 放到 OC 的 Kexts 文件夹下面并加载，去除usbport.kext
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E5%AE%9A%E5%88%B6-5.png)
- 重启即可生效，至此你的 USB 基本上定制完了，尽情使用吧
### 安装过程
- 准备安装U盘：参考OC官方配置，十分好用：[USB Creation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#setting-up-opencore-s-efi-environment)，包含macOS、Windows、Linux的U盘制作。
- (重要)使用`OpenCoreConfigurator`打开我提供的EFI的`OC/config.plist` 重新生成`SystemSerialNumber/SystemUUID/MLB`
- 将当前提供的EFI放入U盘EFI磁盘目录下，表示使用当前EFI进行引导
- 开机配置主板各项配置，以及设置U盘UEFI启动顺序第一
- 插入U盘，选择U盘UEFI启动，进行安装系统
- 安装完成进入系统，成功!
### U盘引导修改为硬盘引导
#### 修改准备
- `DiskGenius`（为什么不用EasyUEFI？因为这EasyUEFI会导致BIOS咕咕咕咕咕咕咕咕，所以不用）
- `EFI文件`
#### 修改开始
- 重启到`WIndows`或者`WinPe`都可以
- 打开`DiskGenius`
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/DG-1.png)
- 找到你u盘的`ESP`分区并把`EFI`复制到桌面即可
- 然后找到你的`硬盘` `ESP`分区（注意是这里要是`WINDOWS的ESP`）
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/DG-2.png)
- 点开`EFI`文件夹把刚才拷贝到的桌面的`EFI`里面的`OC`文件夹丢到`EFI`里面
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/DG-3.png)
- 然后点击顶部菜单栏的`工具`-`设置` `UEFIBIOS`启动项
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/DG-4.png)
- 添加一个启动项，把路径指向`ESP-EFI-OC-OpenCore.efi`即可
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/DG-5.png)
- 把这个启动项修改一下名字上移到第一位`保存`即可
### 英特尔wifi
- WIFI请加载驱动包对应版本驱动
### 英特尔蓝牙
- bigsur：`IntelBluetoothFirmware.kext`
- Monterey：`IntelBluetoothFirmware.kext` `BlueToolFixup.kext`
- Ventura：`IntelBluetoothFirmware.kext` `BlueToolFixup.kext` `IntelBTPatcher.kext`
### 开机优化
- 三星硬盘`trim`会导致开机慢
- 解决方法：`SetApfsTrimTimeout`设置为`0`
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E7%A1%AC%E7%9B%98-1.png)
### 系统时差

- Windows下管理员身份运行

```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项
- `config.plist`勾上仿冒苹果快捷键`PollAppleHotKey`，在启动选择界面，先选中要启动的项，然后按键盘的 `Ctrl` + `Enter` 进入系统即可
- 也有看到说在 `设置`-`启动磁盘` 可选择默认启动项,修改后重启
### 更新oc
- 下载最新版本`OCAT`(https://github.com/ic005k/OCAuxiliaryTools/releases)
- 挂载你的`efi`分区（也叫`esp`分区）
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E6%9B%B4%E6%96%B0oc-1.jpg)
- 挂载后先不要着急打开，先把`OCAT`（即`OCAuxiliaryTools`）同步一下再打开
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E6%9B%B4%E6%96%B0oc-2.jpg)
- 然后再打开`Config.plist`。首先点击全选，然后`检查kext`更新，更新`kext`，后点击选择`opencore版本`，选择`最新版`，`获取opencore`，后点击`同步` `保存`即可
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E6%9B%B4%E6%96%B0oc-3.jpg)
- 保存重启即可
  ![Image text](https://github.com/Win10Q/hackintosh-with-B560-msi-asus/blob/main/img-storage/%E6%9B%B4%E6%96%B0oc-4.jpg)
### 鸣谢

- 橙汁大佬提供SSDT的修改[Github-orangjuc](https://github.com/OrangJuc/)
- 定制usb转自国光大佬[国光黑苹果blog](https://apple.sqlsec.com/)
- 拷贝esp与更新oc转自LoonGasCoom[LoonGasCoom](https://www.jzchen.top/)
- 最好的入门教程：[OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- 中文教程：[Xjn的博客](https://blog.xjn819.com/post/opencore-guide.html)
- 中文文档 & kexts集合下载：[OpenCore中文文档](https://oc.skk.moe/)
- 镜像下载 & 中文教程：[黑果小兵](http://blog.daliansky.net)
