# Hackintosh-EFI

## 本机信息
1. 当前引导是基于OpenCore 0.9.2配置， 平稳运行与Ventrua13.3.1
2. Cpu为 intel i5 10500 comet lake 架构
3. Gpu为 AMD rx580
4. 主板为 微星 B460M 迫击炮
5. 博通BCM94360CD WiFi 蓝牙 模块。

## 2023年5月21日更新
1. 删除启动跑码模式，使用GUI界面
2. 使用USBToolBox 手动mapping usb端口。

## 2023年5月20日更新
1. 修复WiFi失效问题，主要参考open core文档，下载博通网卡内核，并按照顺序排列config文件，并且更换pcie 插槽，怀疑是layout中布局问题，导致无法找到之前的pcie插槽，需要继续调研一下
~~2. 修复蓝牙失效问题，下载博通相应内核后，删除USBPorts内核，更换回USBinjectAll内核。主要原因就是USBPort内核影响了蓝牙。后期需要更新为USBTool并手动匹配所有USB接口。~~
~~3. 删除Boot-arg中的 跑码模式，后期需要更换为界面选择系统~~

## 参考文档和视频
### OpenCore
https://dortania.github.io/OpenCore-Install-Guide/
### 视频-零度解说
https://www.youtube.com/watch?v=e-J3yM7tfos

## 大致步骤
1. 准备一个U盘作为引导盘，使用rufus等工具制作，https://rufus.ie/
2. 下载最新的opencore 的资源
3. 使用opencore的模版准备EFI文件，并根据情况手动配置config.plist文件
4. 将准备好EFI文件导入到U盘中，同时可以将下载好的苹果系统镜像导入
5. 修改BIOS一些设置，适配黑苹果系统，并设置为U盘启动
6. 选择EFI引导启动，可以选择直接安装系统，或者清理后安装，等待安装，大约会重启几次耗时半个小时
7. 最后系统打开后，使用OpenCore Configrator等工具，将制作好的EFI文件挂载到系统中
8. Enjoy your macOS！

## 当前存在问题 TODO
~~1. Wifi蓝牙未适配当前系统~~
~~采用 https://www.youtube.com/watch?v=8ztViUoN8h8 可修复~~

~~2. 前面板USB2.0 未适配~~
~~暂无方案， 可能是需要处理 Kexts中的 USBPorts 更换成 USBinjectAll，后期可以尝试一下~~

3. 无法睡眠
暂无方案

4. 是否可以删除博通的kexts
