# 乐栖 LeQi

乐栖 LeQi 是一个 Windows 桌面音乐播放器。

本仓库是 **公开发布仓库**，仅用于提供安装包、绿色版压缩包和更新检查文件。源码仓库为私有仓库，不在此处公开。

## 下载

请到 Releases 下载最新版本：

- `LeQiSetup-1.0.12.exe`：Windows 安装包
- `LeQi-windows.zip`：Windows 绿色版
- `version.json`：应用更新检查文件

Release 页面：

https://github.com/chenmuting/LeQi/releases

当前版本直链：

```text
https://github.com/chenmuting/LeQi/releases/download/v1.0.12/LeQiSetup-1.0.12.exe
https://github.com/chenmuting/LeQi/releases/download/v1.0.12/LeQi-windows.zip
https://github.com/chenmuting/LeQi/releases/download/v1.0.12/version.json
```

## 当前版本

```text
version: 1.0.12
build: 43
channel: stable
```

## 安装方式

### 安装包

下载并运行：

```text
LeQiSetup-1.0.12.exe
```

适合普通用户使用。

### 绿色版

下载并解压：

```text
LeQi-windows.zip
```

然后运行：

```text
LeQi.exe
```

适合不想安装到系统目录的用户。

## 更新检查

应用内更新检查读取 Release 资产中的：

```text
https://github.com/chenmuting/LeQi/releases/latest/download/version.json
```

因此公开仓库 Release 需要始终包含：

```text
version.json
LeQi-windows.zip
LeQiSetup-<version>.exe
```

## 说明

- 本仓库仅用于公开发布安装包和更新文件。
- 源码仓库为私有仓库。
- 如遇下载失败，请确认目标版本的 Release 是否已完成上传。
