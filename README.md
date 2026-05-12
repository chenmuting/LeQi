# 乐栖 LeQi

乐栖 LeQi 是一个面向 Windows 桌面的音乐播放器，支持在线音乐搜索、发现页、歌单分类、歌手歌曲、专辑页、播放队列、本地歌单、用户歌单、收藏、播放历史统计、主题切换、启动自检、发布校验、数据备份与应用内更新下载。

本仓库是 **乐栖 LeQi 的公开发布仓库**，用于提供安装包、绿色版压缩包和更新检查文件。源码仓库为私有仓库，不在此处公开。

---

## 当前版本

```text
version: 1.0.20
build: 51
channel: stable
```

---

## 下载

请到 Releases 下载最新版本：

```text
https://github.com/chenmuting/LeQi/releases
```

当前版本直链：

```text
https://github.com/chenmuting/LeQi/releases/download/v1.0.20/LeQiSetup-1.0.20.exe
https://github.com/chenmuting/LeQi/releases/download/v1.0.20/LeQi-windows.zip
https://github.com/chenmuting/LeQi/releases/download/v1.0.20/version.json
```

文件说明：

```text
LeQiSetup-1.0.20.exe   Windows 安装包
LeQi-windows.zip       Windows 绿色版
version.json           应用更新检查文件
```

---

## v1.0.20 build 51 更新重点

- 修复歌单分类页 `_categories_loaded_once` 属性缺失导致的未捕获异常。
- 歌单分类页打开后自动加载 `/playlist/catlist`。
- 歌单分类加载完成后自动加载当前分类歌单，默认加载“全部”分类。
- 从发现页跳转歌单分类时，若分类尚未加载，会先加载分类，再按目标分类加载歌单。
- 优化歌单分类页歌单表固定列宽和最小宽高，降低歌单名、创建者、ID 被挤压的问题。
- 优化通用歌曲模型表格固定列宽、最小高度和横向滚动，确保歌曲、歌手、专辑、时长、ID 可显示。
- API 能力检测中 `/api/v2/artist/songs` 改为可选兼容接口；当前 API 不支持时显示“可选缺失”，不再计入必需接口失败。

---

## 主要功能

### 在线音乐播放

- 关键词搜索歌曲、歌手、专辑。
- 搜索结果分页加载更多。
- 双击搜索结果直接播放。
- 播放链接获取失败提示。
- 播放失败时自动停止当前播放后端，降低卡顿风险。
- 连续播放失败次数治理。

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
- 按 category 分组显示分类标签。
- 调用 `/top/playlist` 按分类分页浏览网友精选歌单。
- 双击歌单加载歌单详情。
- 当前歌单歌曲可批量加入本地歌单。
- 歌单表格与歌曲表格已优化列宽、最小宽高和横向滚动。

### 歌手与专辑

- 搜索歌手。
- 查看歌手详情和歌手简介。
- 分页加载歌手歌曲。
- 从歌手歌曲右键打开专辑。
- 搜索专辑。
- 查看专辑详情和专辑歌曲。
- 专辑歌曲内搜索。
- 单首歌曲或整张专辑加入播放队列。
- 单首歌曲或整张专辑加入本地歌单。

### 播放队列

- 查看当前播放队列。
- 播放选中歌曲。
- 移除队列歌曲。
- 清空播放队列。
- 拖拽排序。
- 上移、下移、置顶、置底。
- 排序后保持当前播放歌曲索引稳定。
- 保存为本地歌单时保留当前顺序。

### 本地歌单管理

- 新建、重命名、删除本地歌单。
- 本地歌单分类、标签和说明。
- 按分类筛选本地歌单。
- 搜索歌单内歌曲。
- 本地歌单导入、导出和去重。
- 搜索结果、歌手页、专辑页、歌单分类、收藏、播放历史、播放队列中的歌曲可加入指定本地歌单。

### 数据管理

- 导出用户数据备份。
- 导入用户数据备份。
- 导入前自动备份当前数据。
- 清空缓存、日志、下载目录、收藏、本地歌单、用户歌单缓存、播放历史和播放次数。
- 打开备份目录、数据目录、配置目录、日志目录。

### UI、性能与稳定性

- 页面切换延迟刷新，降低切换瞬间卡顿。
- 首页、歌单管理、收藏、播放历史、数据管理等页面后台加载。
- 本地音乐扫描延迟到页面显示后执行。
- 搜索页、歌手页、专辑页、歌单分类页歌曲表使用或试点 `QTableView + QAbstractTableModel`。
- 通用歌曲表格固定列宽、最小宽高和横向滚动，确保各列可读。
- v1.0.16 起修复启动阶段高概率闪退问题。
- 新增功能不在启动阶段主动请求网络接口。

### 启动自检中心

系统诊断页支持启动自检，可检查：

```text
配置文件
版本文件
数据目录
日志目录
应用图标
QSS 样式
SQLite 数据库
本地歌单 JSON
API 地址配置
关键 Python 模块导入
播放后端模块
打包资源
Release version.json
```

支持导出：

```text
logs/startup_check_<timestamp>.json
```

### Release 与打包校验

- 公开 Release 资产完整性检测脚本。
- 打包产物完整性检测脚本。
- GitHub Actions 工作流在发布前检查本地打包产物。
- GitHub Actions 工作流在发布后检查公开仓库 Release 资产。

---

## 基础使用说明

### 搜索并播放歌曲

1. 打开应用。
2. 进入「搜索」。
3. 输入歌曲名、歌手名或专辑名。
4. 点击「搜索」。
5. 点击「加载更多」继续分页获取结果。
6. 双击歌曲播放。
7. 右键歌曲可加入歌单、查看歌手全部歌曲或打开专辑。

### 浏览歌单分类

1. 进入「歌单分类」页面。
2. 页面会自动获取 `/playlist/catlist` 分类。
3. 分类加载完成后会自动加载当前分类歌单。
4. 可手动选择分类、排序方式并加载更多。
5. 双击歌单加载歌曲。
6. 可将当前歌单歌曲批量加入本地歌单。

### API 能力检测

进入「发现」页面，点击「检测接口能力」。

必需接口通过数量会单独统计；`/api/v2/artist/songs` 是可选兼容接口，当前 API 不支持时会显示“可选缺失”，不作为必需失败项。

### 启动自检

进入：

```text
系统诊断 -> 启动自检
```

可查看配置、数据目录、数据库、本地歌单 JSON、关键模块和打包资源检查结果。

---

## 发布与校验脚本

检查公开 Release 资产：

```bash
python scripts/check_public_release_assets.py --repo chenmuting/LeQi --tag v1.0.20 --build 51
```

检查本地打包产物：

```bash
python scripts/check_build_integrity.py --version 1.0.20
```

---

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

---

## 数据目录说明

```text
config/app_config.json       应用配置
data/app.db                  本地数据库
data/local_playlists.json    本地歌单
data/search_history.json     搜索历史
data/downloads/              下载目录
data/backups/                用户数据备份
logs/                        日志目录
logs/startup_check_*.json    启动自检报告
```

---

## 常见问题

### 下载链接 404

请确认对应版本的 Release 已上传：

```text
LeQiSetup-<version>.exe
LeQi-windows.zip
version.json
```

### 启动闪退

v1.0.16 起已修复启动阶段高概率闪退问题。若仍启动失败，应用会弹出错误提示，并写入：

```text
logs/error.log
```

可进入「系统诊断 -> 启动自检」检查启动依赖。

### API 接口不可用

进入「发现」页面，点击「检测接口能力」。其中 `/api/v2/artist/songs` 为可选兼容接口，返回 404 不影响主要功能。

---

## 仓库说明

- 本仓库仅用于公开发布安装包和更新文件。
- 源码仓库为私有仓库。
- 本仓库不公开源码。
- 如遇安装包或压缩包缺失，请确认 GitHub Actions 是否已成功上传 Release 资产。
