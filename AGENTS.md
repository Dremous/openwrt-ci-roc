# AGENTS.md — OpenWrt 云编译项目

## 项目性质
此为 OpenWrt 固件自动编译仓库，非传统软件开发项目。核心工作流：修改配置 → 触发 GitHub Actions → 下载编译好的固件。

## 上游仓库
- **ImmortalWrt**: https://github.com/laipeng668/immortalwrt （rebase 方式更新）
- **LibWrt**: https://github.com/laipeng668/openwrt-6.x （merge 方式更新，DTS 更丰富，支持更多机型）

## 定制固件
- 修改 `configs/` 目录下对应 `.config` 文件增删插件
- 不需要的包把 `y` 改成 `n`，仅加 `#` 注释无效
- 修改默认 IP、插件包等高级设置编辑 `scripts/Roc-script.sh`
- 添加/修改 `.github/workflows/xx.yml` 后点击 Actions 运行对应 workflow

## 默认固件信息
- 管理地址：`192.168.2.1`
- 用户：`root`
- 密码：无（none）

## 设备支持
- `x86-64-ImmortalWrt.yml` — x86-64 平台
- `JDCloud-ImmortalWrt.yml` / `JDCloud-NoWiFi-ImmortalWrt.yml` — 京东云
- `IPQ807X-LibWrt.yml` — IPQ807X 芯片
- `IPQ60XX-LibWrt.yml` — IPQ60XX 芯片

## 编译说明
- 编译耗时约 1-2 小时
- 完成后在 Releases 对应 Tag 下载固件
- 配置文件对应关系：`x86-64.config` ↔ `x86-64-ImmortalWrt.yml` 等

## 关键文件
- `configs/*.config` — 固件功能配置
- `scripts/Roc-script.sh` — 编译时自定义脚本
- `.github/workflows/*.yml` — CI 编译流程
