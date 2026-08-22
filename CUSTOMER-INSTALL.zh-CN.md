# CodeFlowMu 客户下载安装与升级

本仓库用于分发 **CodeFlowMu Windows x64 产品安装包**，不提供 CodeFlowMu 源码。

## 系统要求

- Windows 10/11 x64 或受支持的 Windows x64 环境
- 不要求预先安装 Git
- 不要求预先安装 Node.js / npm
- 不要求预先安装 Python
- 不要求访问 CodeFlowMu 源码仓库

CodeFlowMu 安装包自带经产品流水线锁定并验证的运行环境。

## 下载

正式版本发布后，请从本仓库对应 GitHub Release 下载至少以下文件：

```text
CodeFlowMu-Setup-<version>-win-x64.exe
SHA256SUMS.txt
installer-manifest.json
product-manifest.json
THIRD-PARTY-NOTICES.json
runtime-security-audit.json
```

在 Release Gate 全部通过之前，本仓库不会把开发候选产物声明为正式客户版本。

## 安装

1. 校验 `CodeFlowMu-Setup-<version>-win-x64.exe` 的 SHA-256 与 `SHA256SUMS.txt` 一致。
2. 双击安装器。
3. 按安装向导完成安装。
4. 从开始菜单或桌面快捷方式启动 **CodeFlowMu**。

默认程序文件安装在 Windows `Program Files` 下；可变运行数据与程序文件分离，写入 CodeFlowMu 的产品数据目录。

产品运行不依赖源码目录，也不应依赖开发机上的 Git、npm、系统 Node.js 或系统 Python。

## 数据与升级

程序升级不得把客户工作数据当作程序文件覆盖或删除。升级前仍建议对重要工作区、Evidence、Audit、Reports 和配置进行备份。

正式升级包必须继续通过：

```text
安装文件完整性
→ 产品 manifest
→ SHA-256
→ 安装后 Runtime 健康检查
→ 安全审计
→ 第三方许可 Gate
```

## 卸载

可通过 Windows“已安装的应用/应用和功能”卸载 CodeFlowMu。

卸载程序与客户数据是两个不同边界。正式产品默认不得因为卸载程序而静默删除客户的任务、Evidence、Audit 或其他持久数据。

## 校验产品来源

正式客户版本只认本仓库的 GitHub Release，并且必须能追溯到 `joinwell52-AI/codeflowmu` 的一个已验证 `main` source commit。

不要把 PR Artifact、feature branch 构建、源码目录压缩包或未经 Release Gate 的 Setup.exe 当作正式客户版本。
