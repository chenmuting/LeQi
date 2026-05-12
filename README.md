# 乐栖 LeQi

乐栖 LeQi 是一个面向 Windows 桌面的音乐播放器。本仓库是公开发布仓库，用于提供 Windows 安装包、绿色版压缩包和应用更新检查文件。源码仓库为私有仓库。

## 当前版本

```text
version: 1.0.23
build: 54
channel: stable
```

## 下载

Release 页面：

```text
https://github.com/chenmuting/LeQi/releases
```

当前版本直链：

```text
https://github.com/chenmuting/LeQi/releases/download/v1.0.23/LeQiSetup-1.0.23.exe
https://github.com/chenmuting/LeQi/releases/download/v1.0.23/LeQi-windows.zip
https://github.com/chenmuting/LeQi/releases/download/v1.0.23/version.json
```

文件说明：

```text
LeQiSetup-1.0.23.exe   Windows 安装包
LeQi-windows.zip       Windows 绿色版
version.json           应用更新检查文件
```

## v1.0.23 build 54 更新重点

- 新增 UI 页面完整性检查脚本，提前发现页面字段未初始化风险。
- 新增配置默认值检查脚本，确保新增配置字段具备默认值。
- 新增关键页面导入检查脚本，降低打包后启动崩溃风险。
- 关于页版本字段写入改为安全方法，修复更新源 / 自动检查字段缺失导致启动崩溃的问题。
- 启动失败弹窗增加复制错误信息、打开日志目录和 `last_crash_summary.txt`。
- 系统诊断页新增最近崩溃日志、复制崩溃日志、打开 / 清空 `error.log`。
- Release 工作流增加 UI integrity、config defaults、page import 三项轻量检查。
- 工作流校验保持容错，避免 PyInstaller 目录结构和 GitHub 下载跳转造成误失败。

## 主要功能

### 在线音乐播放

- 关键词搜索歌曲、歌手、专辑。
- 搜索结果分页加载更多。
- 双击搜索结果直接播放。
- 播放失败提示与连续失败治理。

### 发现页

- 快速搜索。
- 搜索历史。
- 热门歌单分类入口。
- 歌手入口。
- API 能力检测。

### 歌单分类

- 调用 `/playlist/catlist` 获取在线歌单分类。
- 进入页面后自动加载分类。
- 分类加载完成后自动加载当前分类歌单。
- 支持搜索当前已加载歌单。
- 支持快捷分类按钮。
- 当前歌单歌曲可批量加入本地歌单。

### 歌手与专辑

- 搜索歌手。
- 查看歌手详情和歌手简介。
- 分页加载歌手歌曲。
- 查看歌手专辑列表。
- 双击歌手专辑打开专辑页。
- 搜索专辑。
- 查看专辑详情和专辑歌曲。
- 专辑封面显示。
- 专辑歌曲内搜索。
- 单首歌曲或整张专辑加入播放队列 / 本地歌单。

### 播放队列

- 查看、播放、移除、清空播放队列。
- 拖拽排序、上移、下移、置顶、置底。
- 撤销排序。
- 随机打乱。
- 保存为本地歌单时保留当前顺序。

### 自动更新与关于页

- 启动后延迟自动检查更新。
- 24 小时内只自动检查一次。
- 自动检查失败只写日志，不弹错误。
- 关于页展示应用信息、版本更新、Release 下载、项目链接、运行环境、诊断信息和更新日志。
- 关于页显示 ZIP / EXE 下载状态和下载进度。
- 关于页版本字段使用安全写入，降低字段缺失导致启动崩溃风险。

### 启动稳定性与诊断

- 启动失败弹窗支持复制错误信息。
- 启动失败弹窗支持打开日志目录。
- 启动失败会生成 `logs/last_crash_summary.txt`。
- 系统诊断页支持查看最近崩溃日志。
- 系统诊断页支持复制、打开、清空 `logs/error.log`。
- Release 前执行 UI 完整性检查、配置默认值检查和页面导入检查。

### 数据管理

- 导出 / 导入用户数据。
- 导入前自动备份当前数据。
- 清空缓存、日志、下载目录、收藏、本地歌单、用户歌单缓存、播放历史和播放次数。
- 修复本地数据：创建缺失目录、检查 / 修复本地歌单 JSON、隔离损坏 JSON、执行 SQLite integrity_check 和 VACUUM。

### UI、性能与稳定性

- 页面切换延迟刷新，降低切换卡顿。
- 多个页面采用后台加载。
- 搜索页、歌手页、专辑页、歌单分类页歌曲表使用或试点 `QTableView + QAbstractTableModel`。
- 核心表格支持列宽记忆。
- 核心表格支持右键复制单元格、复制整行、复制选中区域。
- v1.0.16 起修复启动阶段高概率闪退问题。

## 基础使用说明

### 自动检查更新

1. 打开应用。
2. 应用启动完成后会按设置延迟自动检查更新。
3. 有新版本时会显示底部通知。
4. 当前已是最新版时默认静默。
5. 检查失败只写入日志，不影响启动。

### 关于页检查更新与下载

1. 进入「关于」页面。
2. 点击「检查更新」。
3. 查看当前版本、远程版本、更新状态和远程更新日志。
4. 点击「下载 ZIP 版」或「下载安装包 EXE」。
5. 下载完成后可打开文件、打开下载目录或复制文件路径。

### 查看最近崩溃日志

进入：

```text
系统诊断 -> 最近崩溃日志
```

可查看、复制、打开或清空：

```text
logs/error.log
```

启动失败时还会生成：

```text
logs/last_crash_summary.txt
```

### 浏览歌单分类

1. 进入「歌单分类」页面。
2. 页面会自动获取 `/playlist/catlist` 分类。
3. 分类加载完成后会自动加载当前分类歌单。
4. 可使用快捷分类按钮快速切换。
5. 可在搜索框中筛选当前已加载歌单。
6. 双击歌单加载歌曲。

### 修复本地数据

进入：

```text
数据管理 -> 修复本地数据
```

## 发布与校验脚本

```bash
python scripts/check_ui_integrity.py
python scripts/check_config_defaults.py
python scripts/check_page_construction.py
python scripts/check_public_release_assets.py --repo chenmuting/LeQi --tag v1.0.23 --build 54
python scripts/check_build_integrity.py --version 1.0.23
```

## 更新检查

应用内更新检查读取：

```text
https://github.com/chenmuting/LeQi/releases/latest/download/version.json
```

每个正式 Release 应包含：

```text
version.json
LeQi-windows.zip
LeQiSetup-<version>.exe
```

## 仓库说明

- 本仓库仅用于公开发布安装包和更新文件。
- 源码仓库为私有仓库。
- 本仓库不公开源码。
