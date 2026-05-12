# 更新日志

## v1.0.13 build 44

- 应用内仓库链接和发布页面链接统一指向公开发布仓库 `chenmuting/LeQi`。
- 应用内下载增强：下载前检测 Release 文件是否存在。
- 应用内下载增强：显示 HTTP 错误原因，特别是 404 文件不存在和 403 访问受限。
- 应用内下载增强：下载完成后校验文件大小，避免保存空文件或异常小文件。
- 应用内下载增强：下载完成后支持打开文件、打开下载目录、复制文件路径。
- 公开仓库补充 `LICENSE`、`CHANGELOG.md`、`SUPPORT.md`。

## v1.0.12 build 43

- 私人源码仓库打包，公开发布仓库发布安装包。
- Release 资产上传目标迁移到 `chenmuting/LeQi`。
- 应用内更新检查迁移到公开仓库 Release 的 `version.json`。
- 应用内 ZIP / EXE 下载地址迁移到公开发布仓库。
- 工作流使用 `PUBLIC_RELEASE_TOKEN` 跨仓库发布 Release。
- `version.json` 作为 Release asset 一并上传。

## 下载文件

每个正式 Release 应包含：

```text
LeQi-windows.zip
LeQiSetup-<version>.exe
version.json
```
