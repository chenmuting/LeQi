# 乐栖 LeQi

乐栖 LeQi 是一个面向 Windows 桌面的音乐播放器。本仓库是公开发布仓库，用于提供 Windows 安装包、绿色版压缩包和应用更新检查文件。源码仓库为私有仓库。

## 当前版本

```text
version: 1.0.21
build: 52
channel: stable
```

## 下载

Release 页面：

```text
https://github.com/chenmuting/LeQi/releases
```

当前版本直链：

```text
https://github.com/chenmuting/LeQi/releases/download/v1.0.21/LeQiSetup-1.0.21.exe
https://github.com/chenmuting/LeQi/releases/download/v1.0.21/LeQi-windows.zip
https://github.com/chenmuting/LeQi/releases/download/v1.0.21/version.json
```

文件说明：

```text
LeQiSetup-1.0.21.exe   Windows 安装包
LeQi-windows.zip       Windows 绿色版
version.json           应用更新检查文件
```

## v1.0.21 build 52 更新重点

- 新增统一表格列宽记忆，核心表格列宽使用 QSettings 持久化保存。
- 核心表格新增右键复制能力：复制单元格、复制整行、复制选中区域。
- 歌单分类页新增“搜索当前已加载歌单”输入框。
- 歌单分类页新增快捷分类按钮：全部、华语、流行、摇滚、民谣、电子、轻音乐、学习、工作、睡前。
- 专辑页新增专辑封面显示，加载专辑详情时异步下载封面。
- 歌手页新增歌手专辑列表，双击专辑可打开专辑页。
- 播放队列新增撤销排序，保留最近 10 次排序快照。
- 播放队列新增随机打乱。
- 启动自检报告新增“一键复制精简报告”。
- 数据管理页新增“修复本地数据”，可修复本地歌单 JSON、常用目录和 SQLite 基础状态。

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

### 数据管理

- 导出 / 导入用户数据。
- 导入前自动备份当前数据。
- 清空缓存、日志、下载目录、收藏、本地歌单、用户歌单缓存、播放历史和播放次数。
- 修复本地数据：创建缺失目录、检查/修复本地歌单 JSON、隔离损坏 JSON、执行 SQLite integrity_check 和 VACUUM。

### UI、性能与稳定性

- 页面切换延迟刷新，降低切换卡顿。
- 多个页面采用后台加载。
- 搜索页、歌手页、专辑页、歌单分类页歌曲表使用或试点 `QTableView + QAbstractTableModel`。
- 核心表格支持列宽记忆。
- 核心表格支持右键复制单元格、复制整行、复制选中区域。
- v1.0.16 起修复启动阶段高概率闪退问题。

### 启动自检中心

系统诊断页支持启动自检，可检查配置文件、版本文件、数据目录、日志目录、应用图标、QSS 样式、SQLite 数据库、本地歌单 JSON、API 地址配置、关键 Python 模块导入、播放后端模块、打包资源和 Release version.json。

支持导出报告，也支持一键复制精简报告。

## 基础使用说明

### 浏览歌单分类

1. 进入「歌单分类」页面。
2. 页面会自动获取 `/playlist/catlist` 分类。
3. 分类加载完成后会自动加载当前分类歌单。
4. 可使用快捷分类按钮快速切换。
5. 可在搜索框中筛选当前已加载歌单。
6. 双击歌单加载歌曲。

### 查看歌手专辑

1. 进入「歌手」页面。
2. 搜索歌手。
3. 点击“歌手专辑”。
4. 双击专辑打开专辑页。

### 修复本地数据

进入：

```text
数据管理 -> 修复本地数据
```

## 发布与校验脚本

```bash
python scripts/check_public_release_assets.py --repo chenmuting/LeQi --tag v1.0.21 --build 52
python scripts/check_build_integrity.py --version 1.0.21
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
