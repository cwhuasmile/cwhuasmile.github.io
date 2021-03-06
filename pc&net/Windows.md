## Win10 关闭Windows Defender防病毒程序

1. 点击屏幕左下角`开始`-->`运行`-->输入`gpedit.msc`点确定打开本地组策略编辑器。

2. 以此选择`计算机配置`、`管理模板`、`Windows组件`、`Windows Defender 防病毒程序`。

3. 双击右侧的`关闭Windows Defender 防病毒程序`打开配置对话框。

4. 选择`已启用`，点击下方`确定`既可关闭Windows Defender 防病毒程序。

## UEFI启动修复方法

以下两种方法都是使用bcdboot修复

### 第一种、指定esp分区：

环境为64位8PE，bios/uefi启动进入下都可以。

* 1，启动64位8PE，并用esp分区挂载器或diskgenuis挂载esp分区
* 2，打开cmd命令行，输入以下命令并运行

```cmd
bcdboot c:\windows /s o: /f uefi /l zh-cn
```

其中：c:\windows 硬盘系统目录，根据实际情况修改

/s o: 指定esp分区所在磁盘，根据实际情况修改

/f uefi 指定启动方式为uefi

/l zh-cn 指定uefi启动界面语言为简体中文

> 注：64位7PE不带/s参数，故7PE不支持bios启动下修复

### 第二种、不指定esp分区修复：

环境为64位7或8PE，只有uefi启动进入PE才可以

* 1、不用挂载esp分区，直接在cmd命令行下执行：

```cmd
bcdboot c:\windows /l zh-cn
```

其中 c:\windows 硬盘系统目录，根据实际情况修改

/l zh-cn 指定uefi启动界面语言为简体中文

> 注：在8PE中，我们也可以在uefi启动进入pe后，挂载esp分区用第一种方法修复

## HTTP服务防火墙设置

防火墙添加入站规则，选TCP链接，然后指定端口，例如80，8081等。

## Win10 修改默认图片打开方式为照片查看器

复制以下内容到记事本：

```bash
@echo off&cd\&color 0a&cls
echo 恢复Win10照片查看器
reg add "HKLM\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations" /v ".jpg" /t REG_SZ /d PhotoViewer.FileAssoc.Tiff /f
reg add "HKLM\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations" /v ".jpeg" /t REG_SZ /d PhotoViewer.FileAssoc.Tiff /f
reg add "HKLM\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations" /v ".bmp" /t REG_SZ /d PhotoViewer.FileAssoc.Tiff /f
reg add "HKLM\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations" /v ".png" /t REG_SZ /d PhotoViewer.FileAssoc.Tiff /f
echo 请双击或右击图片，选择“照片查看器”即可
pause
```

然后再保存为.bat的程序，以管理员方式运行之，第一次打开图片时选择windows照片查看器即可。以后重装系统了，或者别人需要设置，直接执行这个批处理程序就好了