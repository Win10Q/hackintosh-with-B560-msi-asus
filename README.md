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
- USB键盘从S3/S4/S5唤醒：任意键

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
- 提供ssdt的修改
