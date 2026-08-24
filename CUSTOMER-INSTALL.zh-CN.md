# CodeFlowMu 客户下载安装与升级

本仓库用于分发 **CodeFlowMu Windows x64 专有软件的免费公开预览版**，不提供 CodeFlowMu 源码，也不授予开源许可证。

## 系统要求

- Windows 10/11 x64 或受支持的 Windows x64 环境
- 不要求预先安装 Git
- 不要求预先安装 Node.js / npm
- 不要求预先安装 Python
- 不要求访问 CodeFlowMu 源码仓库

CodeFlowMu 安装包自带经产品流水线锁定并验证的基础运行环境。

## 下载

> [!IMPORTANT]
> 当前仓库已经提供可下载的候选 pre-release，但尚无正式支持的稳定版。候选软件只用于预览和安装测试。

需要在另一台 Windows x64 电脑上进行安装测试时，可使用明确标注为非正式版的 [V1.9.7 Candidate 1 Pre-release](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v1.9.7-candidate.1)：

- [直接下载安装程序](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v1.9.7-candidate.1/CodeFlowMu-Setup-1.9.7-win-x64.exe)
- SHA-256：`15c96e86d0583540793d0178727a1082ef38395831c460c988d9efc4ad2aca86`

该文件只用于安装测试；它没有通过正式 Cursor Provider Release Gate，不得作为正式客户版本或正式支持版本。

候选安装器尚未进行代码签名，可能触发 Windows SmartScreen；运行前必须校验 SHA-256。CodeFlowMu 预览版本身免费，外部 Provider 的账户、服务和调用费用彼此独立。

正式安装包只从本仓库的 [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases) 下载。Release 上线后，请下载至少以下文件：

```text
CodeFlowMu-Setup-<version>-win-x64.exe
SHA256SUMS.txt
installer-manifest.json
product-manifest.json
THIRD-PARTY-NOTICES.json
runtime-security-audit.json
security-risk-acceptance.json
cursor.json
```

`runtime-security-audit.json` 是该版本客户产品的有效依赖安全审计；如果存在被接受的低风险项，`security-risk-acceptance.json` 会给出对应依据和重新审阅条件。`cursor.json` 是 Cursor Provider 的真实兼容性证据，记录 CodeFlowMu 已验证的 `sdk.v1` bridge 版本、官方 archive SHA-256 和关键兼容检查。

在 Release Gate 全部通过之前，本仓库不会把开发候选产物声明为正式客户版本。

## 安装 CodeFlowMu

1. 校验 `CodeFlowMu-Setup-<version>-win-x64.exe` 的 SHA-256 与 `SHA256SUMS.txt` 一致。
2. 双击安装器。
3. 按安装向导完成安装。
4. 从开始菜单或桌面快捷方式启动 **CodeFlowMu**。

默认程序文件安装在 Windows `Program Files` 下；可变运行数据与程序文件分离，写入 CodeFlowMu 的产品数据目录。

产品运行不依赖源码目录，也不应依赖开发机上的 Git、npm、系统 Node.js 或系统 Python。

安装完成后，建议先按[手把手完成第一个 ShipReady PWA](FIRST-PWA-TASK.zh-CN.md)走通 PM、DEV、QA、OPS 的完整交付闭环，再接入真实业务项目。

## 使用 Mobile PWA

Mobile PWA 是 CodeFlowMu 的手机端入口，当前公网地址：

<https://ai.chedian.cc/cfm/>

PWA 不能脱离 PC 上的 CodeFlowMu 单独执行任务。使用时需要保持 PC 上的 CodeFlowMu 正在运行，并完成手机与该 PC Runtime 实例的绑定。

### 公网 Gateway 绑定

1. 在 PC 上启动 CodeFlowMu。
2. 在左侧导航打开 **移动端**，点击 **刷新**。
3. 确认 Gateway 状态为在线，并显示 **公网 Gateway 绑定二维码**。
4. 用手机浏览器扫描该二维码；也可以复制页面显示的绑定链接到手机打开。
5. 完成绑定后，手机会出现在 PC 的 **已绑定设备** 列表中。
6. 在手机浏览器菜单中选择“添加到主屏幕”或“安装应用”，即可像普通应用一样打开 PWA。

公网 Gateway 模式不要求手机与电脑位于同一个局域网，但 PC 必须能够连接 CodeFlowMu Gateway，手机也必须能够访问上述 HTTPS 地址。

### 局域网绑定

1. 让手机与电脑连接同一个 Wi-Fi。
2. 在 PC 的 **移动端** 页面点击 **刷新**。
3. 扫描 **局域网绑定二维码**，或复制局域网绑定链接到手机。
4. 如果手机打不开链接，请在 Windows 防火墙中允许 CodeFlowMu 的 TCP `18766` 端口入站，然后重新刷新绑定信息。

请勿把二维码或绑定链接发送给无关人员。每台手机需要独立绑定；手机丢失或不再使用时，应在 PC 的 **移动端 → 已绑定设备** 中解除绑定。绑定码过期、Gateway 离线或 PC 已关闭时，重新启动 CodeFlowMu 并点击 **刷新** 生成新的绑定信息。

PWA、Mobile API、Gateway 和 PC 主程序使用独立版本号。PWA 页面更新不等于 PC 安装包已经发布，PC 安装包升级也不应被描述为 PWA 已完成升级。

## 启用 Cursor Provider

Cursor 不再作为真实 `@cursor/sdk` 被打进 CodeFlowMu 主安装包。CodeFlowMu 使用独立的 Cursor `sdk.v1` Provider Runtime。

正式版本发布后，先为客户自己的 Cursor 账户配置 `CURSOR_API_KEY`，再运行产品提供的 Provider 安装入口：

```text
CodeFlowMu --install-cursor-provider
```

Provider Manager 只接受 CodeFlowMu 声明的候选/已测试版本，下载 Cursor 官方 standalone bridge 和官方 `SHA256SUMS.txt`，校验 SHA-256 与 `sdk.v1` manifest 后安装到 CodeFlowMu 产品数据目录。

典型目录：

```text
C:\ProgramData\CodeFlowMu\providers\cursor\
├─ versions\<version>\
├─ current\
└─ current.json
```

Cursor Provider 与 CodeFlowMu 本体使用不同版本生命周期。正式支持的 Provider 版本必须与该 CodeFlowMu Release 附带的 `cursor.json` 一致；不要把未经验证的新 bridge 版本直接当作正式生产版本。

## 数据与升级

程序升级不得把客户工作数据当作程序文件覆盖或删除。升级前仍建议对重要工作区、Evidence、Audit、Reports 和配置进行备份。

正式升级包必须继续通过：

```text
安装文件完整性
→ 产品 manifest
→ SHA-256
→ 安装后 Runtime 健康检查
→ 有效产品安全审计
→ 低风险逐条接受（如有）
→ Provider 真实兼容测试
→ Provider compatibility evidence
```

Cursor Provider 可独立升级和回滚，不要求仅因为一个兼容的 Provider 更新就重新安装 CodeFlowMu 本体。

## 卸载

可通过 Windows“已安装的应用/应用和功能”卸载 CodeFlowMu。

卸载程序与客户数据是两个不同边界。正式产品默认不得因为卸载程序而静默删除客户的任务、Evidence、Audit、Provider 状态或其他持久数据。

## 校验产品来源

正式客户版本只认本仓库的 GitHub Release，并且必须能追溯到 `joinwell52-AI/codeflowmu` 的一个已验证 `main` source commit。

不要把 PR Artifact、feature branch 构建、源码目录压缩包、未经兼容测试的 Provider，或未经 Release Gate 的 Setup.exe 当作正式客户版本。
