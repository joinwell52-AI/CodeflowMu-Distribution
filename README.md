# CodeFlowMu Product Distribution

本仓库是 **CodeFlowMu 客户产品分发仓库**。

> 本仓库不是 CodeFlowMu 源码仓库。正式客户产品只包含经过验证的安装器、校验文件、产品清单、第三方许可/安全证据和客户文档。

当前仓库保持 **Private**。产品源码继续位于独立的私有源码仓库 `joinwell52-AI/codeflowmu`。当前保持私有是因为产品化与正式发行准备仍在进行；产品完成后，再决定本分发仓库是否对外开放。

## 客户入口

- [中文：下载安装与升级](CUSTOMER-INSTALL.zh-CN.md)
- [English: Install and Upgrade](CUSTOMER-INSTALL.md)
- GitHub Releases：本仓库的 Releases 页面

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
```

其中 `runtime-security-audit.json` 记录客户产品实际依赖的安全审计结果；如果存在允许发行的低风险项，必须由 `security-risk-acceptance.json` 逐条记录接受依据和重新审阅条件。未记录的风险不能因为严重级别较低而自动放行。

正式产品必须由 `joinwell52-AI/codeflowmu` 的 `main` 产品流水线生成并通过全部 Release Gate 后发布。

PR / feature branch 产物只属于开发验证，**不得作为正式客户产品发布到本仓库 Release**。

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

产品允许包含经过构建/编译的运行产物、内置运行时、前端静态资源和必要的第三方运行依赖。

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
→ third-party license/redistribution gate
→ immutable GitHub Release in CodeflowMu-Distribution
```

任何 critical/high/moderate 未解决安全项、未有明确接受依据的 low 风险、第三方再分发许可未确认、安装后健康检查失败或产品清单不一致，都必须 fail closed，不得发布。

## 当前状态

CodeFlowMu `V1.9.7` Windows 产品技术链已经完成安装与真实运行验证。当前分发仓库仍保持 Private，正式 Release 继续受第三方再分发许可等 Release Gate 约束；在全部 Gate 通过前不声明正式客户版本。
