# ASUS-TUF-GAMING-B560M-PLUS-WIFI-i5-11400-RX6600XT-HACKINTOSH-OPENCORE

## 硬件列表

|项目|名称
|-|-
|CPU|Intel 11th CORE 11400
|主板|ASUS TUF GAMING B560M PLUS WIFI
|内存|corsair DDR4 2666MHz 8Gx2
|显卡|AMD RX6600XT
|硬盘|SAMSUNG 980PRO 512GB
|无线网卡|AX201

### 功能测试

- [x] 板载声卡
- [x] 板载网卡
- [x] 睡眠唤醒
- [x] CPU 变频
- [x] 所有USB端口
- [x] 接力和隔空投送
- [x] 板载蓝牙

[❌] 核显硬件加速

### BIOS设置

- USB设备从S3/S4/S5唤醒：允许
- PS/2鼠标从S3/S4/S5唤醒：允许
- USB键盘从S3/S4/S5唤醒：任意

### 安装过程
- 准备安装U盘：参考OC官方配置，十分好用：[USB Creation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#setting-up-opencore-s-efi-environment)，包含macOS、Windows、Linux的U盘制作。
- (重要)使用OpenCoreConfigurator打开我提供的EFI的OC/config.plist 重新生成SystemSerialNumber/SystemUUID/MLB
- 将当前提供的EFI放入U盘EFI磁盘目录下，表示使用当前EFI进行引导
- 开机配置主板各项配置，以及设置U盘UEFI启动顺序第一
- 插入U盘，选择U盘UEFI启动，进行安装系统
- 安装完成进入系统，成功!

### 系统时差

- Windows下管理员身份运行

```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项

- `config.plist`勾上仿冒苹果快捷键`PollAppleHotKey`，在启动选择界面，先选中要启动的项，然后按键盘的 `Ctrl` + `Enter` 进入系统即可

- 也有看到说在 `设置`-`启动磁盘` 可选择默认启动项,修改后重启

### 鸣谢
- https://github.com/OrangJuc/
- 橙汁大佬提供ssdt的修改
- 最好的入门教程：[OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- 中文教程：[Xjn的博客](https://blog.xjn819.com/post/opencore-guide.html)
- 中文文档 & kexts集合下载：[OpenCore中文文档](https://oc.skk.moe/)
- 镜像下载 & 中文教程：[黑果小兵](http://blog.daliansky.net)
