# CodeFlowMu Product Distribution

本仓库是 **CodeFlowMu 客户产品分发仓库**。

> 本仓库不是 CodeFlowMu 源码仓库。正式客户产品只包含经过验证的安装器、校验文件、产品清单、第三方许可/安全证据、Provider 兼容证据和客户文档。

当前仓库保持 **Private**。产品源码继续位于独立的私有源码仓库 `joinwell52-AI/codeflowmu`。当前保持私有是因为产品化与正式发行准备仍在进行；产品完成后，再决定本分发仓库是否对外开放。

## 客户入口

- [中文：下载安装、PWA 与升级](CUSTOMER-INSTALL.zh-CN.md)
- [English: Install, PWA, and Upgrade](CUSTOMER-INSTALL.md)
- [V1.9.7 Candidate 1 测试安装包](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v1.9.7-candidate.1)：Pre-release，非正式客户版本
- [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases)：当前没有正式安装包 Release

当前目标平台：**Windows x64**。

## 正式发行内容

每个正式 CodeFlowMu Windows 版本应至少包含：

```text
CodeFlowMu-Setup-<version>-win-x64.exe
SHA256SUMS.txt
installer-manifest.json
product-manifest.json
THIRD-PARTY-NOTICES.json
runtime-security-audit.json
security-risk-acceptance.json
cursor.json                 # Cursor Provider 兼容性证据
```

其中 `runtime-security-audit.json` 记录客户产品实际依赖的安全审计结果；如果存在允许发行的低风险项，必须由 `security-risk-acceptance.json` 逐条记录接受依据和重新审阅条件。`cursor.json` 记录该 CodeFlowMu 版本真实验证通过的 Cursor `sdk.v1` bridge 版本、官方 archive SHA-256 以及 create/send/stream 等兼容性检查结果。

正式产品必须由 `joinwell52-AI/codeflowmu` 的 `main` 产品流水线生成并通过全部 Release Gate 后发布。

PR / feature branch 产物只属于开发验证，**不得作为正式客户产品发布到本仓库 Release**。

## Cursor Provider 边界

CodeFlowMu 正式产品不把真实 `@cursor/sdk` 或 Cursor bridge 二进制打进主安装包。Cursor 是独立 Provider：

```text
CodeFlowMu
→ CodeFlowMu Cursor Provider Adapter
→ Cursor sdk.v1 external bridge
→ 客户自己的 CURSOR_API_KEY
→ Cursor Service
```

CodeFlowMu 安装后通过产品内置 Provider Manager 获取并验证官方 Cursor bridge。Provider 使用独立版本生命周期和独立数据目录，因此 Cursor bridge 可以升级或回滚，而无需因为一个兼容 Provider 更新就重新安装整个 CodeFlowMu。

正式发行只允许使用已经通过 CodeFlowMu 产品兼容测试并在 Release 中附带 `cursor.json` 证据的 bridge 版本。候选或未经验证的新 Cursor bridge 版本不得自动作为正式支持版本。

## 产品与源码边界

客户分发不得包含 CodeFlowMu 开发源码工程，例如：

```text
.git/
src/
__tests__/
tests/
research/
docs/openplan/
editions/open-dev-team/
*.ts
*.tsx
source maps
开发凭据或 .env
```

产品允许包含经过构建/编译的运行产物、内置运行时、前端静态资源和必要的第三方运行依赖。外部 Provider 运行时不因为被 CodeFlowMu 支持就自动成为 CodeFlowMu 安装包的一部分。

## 发行原则

正式发行链路：

```text
codeflowmu main
→ closed-distribution boundary
→ product build
→ self-contained Windows runtime
→ Setup.exe
→ silent install
→ installed-file SHA-256 verification
→ installed runtime health check
→ effective-product security audit
→ explicit low-risk acceptance (if any)
→ real Cursor provider compatibility smoke
→ provider compatibility evidence
→ immutable GitHub Release in CodeflowMu-Distribution
```

任何 critical/high/moderate 未解决安全项、未有明确接受依据的 low 风险、Provider 兼容证据缺失、安装后健康检查失败或产品清单不一致，都必须 fail closed，不得发布。

## 当前状态

CodeFlowMu `V1.9.7` Windows 基础产品链已经完成安装与真实运行验证。Cursor SDK 解耦与 external `sdk.v1` Provider 正在独立的产品化 Draft PR 中验证；当前 Cursor bridge `1.0.28` 只作为候选版本，**尚未声明为正式 tested/supported Provider**。本分发仓库继续保持 Private，全部 Release Gate 通过前不声明正式客户版本。
