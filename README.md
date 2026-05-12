# 乐栖 LeQi

乐栖 LeQi 是一个面向 Windows 桌面的音乐播放器。本仓库是公开发布仓库，用于提供 Windows 安装包、绿色版压缩包和应用更新检查文件。源码仓库为私有仓库。

## 当前版本

```text
version: 1.0.25
build: 56
channel: stable
```

## 下载

Release 页面：

```text
https://github.com/chenmuting/LeQi/releases
```

当前版本直链：

```text
https://github.com/chenmuting/LeQi/releases/download/v1.0.25/LeQiSetup-1.0.25.exe
https://github.com/chenmuting/LeQi/releases/download/v1.0.25/LeQi-windows.zip
https://github.com/chenmuting/LeQi/releases/download/v1.0.25/version.json
```

文件说明：

```text
LeQiSetup-1.0.25.exe   Windows 安装包
LeQi-windows.zip       Windows 绿色版
version.json           应用更新检查文件
```

## v1.0.25 build 56 更新重点

- 新增首次启动欢迎页，提供搜索、歌单分类、设置等快速入口。
- 新增全局快捷键说明，支持 F1 查看快捷键。
- 新增全局快捷键：空格播放 / 暂停、Ctrl+F 搜索、Ctrl+L 歌单、Ctrl+H 历史、Ctrl+, 设置、Ctrl+Q 队列、F5 刷新。
- 首页优化为快捷仪表盘，增加发现、歌单分类、歌手、专辑、数据管理、检查更新等入口。
- 设置页新增“启动时显示欢迎页”开关。
- 新增空状态组件，用于统一空列表说明样式。
- Toast 状态提示支持 info / success / warning / error 类型样式。
- 修复安装包启动闪退风险：main.py 在导入应用模块前先归一化工作目录。
- 修复安装包启动闪退风险：配置读取兼容安装目录与 `_internal/config`。
- 修复安装包快捷方式工作目录：开始菜单、桌面图标和安装后启动均使用 `{app}` 作为 WorkingDir。
- 安装包脚本仓库链接更新为公开仓库 `chenmuting/LeQi`。

## 主要功能

### 在线音乐播放

- 关键词搜索歌曲、歌手、专辑。
- 搜索结果分页加载更多。
- 双击搜索结果直接播放。
- 播放失败提示与连续失败治理。
- 播放失败原因分类与事件日志记录。
- 当前歌曲播放后后台预取下一首在线歌曲 URL。

### 新手引导与快捷键

- 首次启动显示欢迎页。
- 欢迎页支持快速进入搜索、歌单分类和设置。
- 设置页可控制是否启动时显示欢迎页。
- F1 可打开快捷键说明。
- 支持空格播放 / 暂停、Ctrl+F 搜索、Ctrl+L 歌单、Ctrl+H 历史、Ctrl+, 设置、Ctrl+Q 队列、F5 刷新。

### 首页仪表盘

- 首页展示 API 地址、播放内核、收藏数量、历史数量、总播放次数、缓存歌单数量。
- 首页提供搜索、发现、歌单分类、歌手、专辑、本地音乐、本地歌单、数据管理、系统诊断和检查更新快捷入口。
- 首页展示最近播放和常听歌曲 Top 10。

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
- 显示队列歌曲状态。
- 失败歌曲支持重试播放、移除失败歌曲、复制失败原因。

### 播放事件日志

- 记录播放成功、播放失败、跳过、停止、连续失败、预取等事件。
- 记录失败原因、失败阶段、播放后端、队列位置、歌曲名、歌手和专辑。
- 支持筛选播放事件。
- 支持导出 TXT / JSON。

### 自动更新与关于页

- 启动后延迟自动检查更新。
- 24 小时内只自动检查一次。
- 自动检查失败只写日志，不弹错误。
- 关于页展示应用信息、版本更新、Release 下载、项目链接、运行环境、诊断信息和更新日志。
- 关于页显示 ZIP / EXE 下载状态和下载进度。
- 关于页版本字段使用安全写入，降低字段缺失导致启动崩溃风险。

### 安装包启动稳定性

- 安装包启动前先归一化工作目录，避免从开始菜单或桌面快捷方式启动时找不到配置。
- 配置读取兼容安装目录 `config/app_config.json` 与 `_internal/config/app_config.json`。
- 资源查找兼容安装目录与 `_internal/assets`。
- 安装包快捷方式设置 WorkingDir 为 `{app}`。
- 安装包脚本仓库链接指向公开仓库 `chenmuting/LeQi`。

### 启动稳定性与诊断

- 启动失败弹窗支持复制错误信息。
- 启动失败弹窗支持打开日志目录。
- 启动失败会生成 `logs/last_crash_summary.txt`。
- 系统诊断页支持查看最近崩溃日志。
- 系统诊断页支持复制、打开、清空 `logs/error.log`。
- 系统诊断页支持播放后端健康检查。
- Release 前执行 UI 完整性检查、配置默认值检查、页面导入检查和安装包运行时检查。

### 数据管理

- 导出 / 导入用户数据。
- 导入前自动备份当前数据。
- 清空缓存、日志、下载目录、收藏、本地歌单、用户歌单缓存、播放历史和播放次数。
- 修复本地数据：创建缺失目录、检查 / 修复本地歌单 JSON、隔离损坏 JSON、执行 SQLite integrity_check 和 VACUUM。
- 查看、筛选、清空、导出播放事件日志。

### UI、性能与稳定性

- 页面切换延迟刷新，降低切换卡顿。
- 多个页面采用后台加载。
- 搜索页、歌手页、专辑页、歌单分类页歌曲表使用或试点 `QTableView + QAbstractTableModel`。
- 核心表格支持列宽记忆。
- 核心表格支持右键复制单元格、复制整行、复制选中区域。
- Toast 支持不同状态样式。
- v1.0.16 起修复启动阶段高概率闪退问题。

## 基础使用说明

### 首次启动欢迎页

首次启动会显示欢迎页，可选择：

```text
开始搜索
浏览歌单分类
打开设置
不再显示
```

可在设置页调整：

```text
启动时显示欢迎页
```

### 快捷键

```text
空格：播放 / 暂停
Ctrl + F：搜索
Ctrl + L：本地歌单
Ctrl + H：播放历史
Ctrl + ,：设置
Ctrl + Q：播放队列
F5：刷新当前页
F1：快捷键说明
```

### 安装包启动失败排查

若安装包启动失败，请查看：

```text
logs/error.log
logs/last_crash_summary.txt
```

v1.0.25 已修复以下高风险点：

```text
快捷方式工作目录不正确
启动前未切换到安装目录
配置文件位于 _internal/config 时读取失败
资源文件位于 _internal/assets 时读取失败
```

### 播放失败处理

播放失败时，应用会：

```text
停止并释放当前媒体资源
记录失败原因和失败阶段
将播放队列歌曲标记为已失败 / 已跳过
必要时自动跳过下一首
达到连续失败上限时停止队列
```

在播放队列中可对失败歌曲执行：

```text
重试播放
复制失败原因
移除失败歌曲
```

### 播放事件日志

进入：

```text
数据管理 -> 播放事件日志
```

可按以下类型筛选：

```text
播放成功
播放失败
跳过
停止
连续失败
预取
```

支持导出：

```text
TXT
JSON
```

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

## 发布与校验脚本

```bash
python scripts/check_ui_integrity.py
python scripts/check_config_defaults.py
python scripts/check_page_construction.py
python scripts/check_installer_runtime.py
python scripts/check_public_release_assets.py --repo chenmuting/LeQi --tag v1.0.25 --build 56
python scripts/check_build_integrity.py --version 1.0.25
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
