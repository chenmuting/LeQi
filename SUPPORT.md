# 支持与问题排查

本仓库是乐栖 LeQi 的公开发布仓库，仅用于发布安装包、绿色版压缩包和更新检查文件。

## 下载失败

请先确认 Release 中是否存在以下文件：

```text
LeQi-windows.zip
LeQiSetup-<version>.exe
version.json
```

如果应用内下载提示 404，通常表示对应版本的 Release 资产尚未上传完成。

## 无法检查更新

应用内更新检查读取：

```text
https://github.com/chenmuting/LeQi/releases/latest/download/version.json
```

请确认最新 Release 中包含 `version.json`。

## 安装包无法运行

建议：

1. 重新下载安装包。
2. 确认文件名类似 `LeQiSetup-1.0.13.exe`。
3. 右键安装包，选择“以管理员身份运行”。
4. 如果被安全软件拦截，请检查安全软件日志。

## 绿色版无法启动

建议：

1. 完整解压 `LeQi-windows.zip`。
2. 不要直接在压缩包内运行。
3. 确认目录中存在 `LeQi.exe` 和 `_internal` 目录。
4. 如果缺少 `_internal`，请重新下载压缩包。

## 无法播放歌曲

应用内可查看播放事件日志：

```text
数据管理 -> 播放事件日志
```

可以查看、筛选、复制、导出或清空日志。

## 数据备份

应用内可进入：

```text
数据管理 -> 导出用户数据
```

导入用户数据前建议保持“导入前自动备份当前数据”开启。

## 反馈问题时建议提供

```text
应用版本
Build 号
Windows 版本
安装方式：安装包 / 绿色版
问题截图
播放事件日志，若与播放有关
诊断信息，关于页可复制
```
