# CodeFlowMu 客户下载安装与升级

本仓库用于分发 **CodeFlowMu Windows x64 专有软件的免费预览版**，不提供 CodeFlowMu 源码，也不授予开源许可证。

## 系统要求

- Windows 10/11 x64 或受支持的 Windows x64 环境
- 当前用户可写的 NTFS 分区安装目录（首次生成配置需要硬链接支持）
- 不要求预先安装 Git
- 不要求预先安装 Node.js / npm
- 不要求预先安装 Python
- 不要求访问 CodeFlowMu 源码仓库

CodeFlowMu 安装包自带经产品流水线锁定并验证的基础运行环境。

## 下载

> [!IMPORTANT]
> 当前修复包 [V2.2.2 Preview 4](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.2-preview.4) 已通过 GitHub Pre-release 提供下载，未激活自动更新，等待用户重新安装验收。Preview 17 存在初始化根目录错误；Preview 18 缺少首次启动团队配置和 EXE 内置图标，请使用 V2.2.2 Preview 4 验证本次修复。没有正式支持的稳定版。仓库为 Private，下载需要有访问权限的 GitHub 账号。

请从 GitHub 下载本次候选安装器和校验文件：

- [下载安装器：CodeFlowMu-Setup-2.2.2-preview.4-win-x64.exe](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.2-preview.4/CodeFlowMu-Setup-2.2.2-preview.4-win-x64.exe)。
- [下载 SHA256SUMS.txt](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.2-preview.4/SHA256SUMS.txt)。
- SHA-256：`4086fdc1b0f491af79f1abe2e4636aeb89aa7391376b9cf50c0145d5aa5951f5`。

本次检查覆盖隔离静默安装、8,888 项文件清单、启动、初始化、真实团队接口、重启保留团队配置和原生 EXE 退出。两个 EXE 均包含经核对的 7 个尺寸图标；首次启动生成干净的默认团队，已有客户配置保持不变。用户重新安装验收仍待完成；这些检查不包含外部 Provider 账户配置、手机业务任务或全量升级回归，不代表正式支持。

候选安装器尚未进行代码签名，可能触发 Windows SmartScreen；运行前必须校验 SHA-256。CodeFlowMu 预览版本身免费，外部 Provider 的账户、服务和调用费用彼此独立。

安装包只从本仓库的 [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases) 下载。客户只需下载以下两个文件：

```text
CodeFlowMu-Setup-<version>-<candidate>-win-x64.exe
SHA256SUMS.txt
```

文件名包含完整候选号，避免同一产品版本的多个安装包混淆。GitHub 历史 Preview 17 不包含本次修复，不能用它验证 V2.2.2 Preview 4。

其他产品清单、模块配置、安全审计和安装验收明细由发行工作台保存在内部版本记录中，不作为客户附件散发。Cursor 采用独立的 `sdk.v1` Provider Runtime，不把真实 Cursor SDK 或客户账户凭据打入安装包。

在 Release Gate 全部通过之前，本仓库不会把开发候选产物声明为正式客户版本。

## 本次修复：恢复接入通道选择

- 修复旧业务项目中的版本标记导致“公开版固定 Cursor”、通道下拉框被禁用的问题；Preview 3 不包含这项修复。
- 可选择 Cursor、Google、Claude、ChatGPT 订阅 / Codex、豆包五个现有通道；保留各通道原有接入条件、权限和运行模式边界。
- 程序版本身份由安装目录确定，不再由业务项目中的旧版标记覆盖；无需删除项目文件或密钥配置。
- 已用本次最终 EXE 在保留旧版标记的测试项目中逐项切换五个通道，并验证重启与项目切换后仍不被锁定；未保存账户配置或调用付费模型。

## 保留的修复：重启、项目切换与版本信息

- 重启使用安装包内置的启动器和 Node，不依赖客户电脑上的 npm；等待中的启动恢复任务可正常取消，避免退出超时。
- 切换到独立业务项目时，Runtime、MCP 与任务/报告监听器同步切换；退出后重新执行 EXE 会恢复上次选择的项目。
- 程序资源来自安装目录，业务项目保留自己的目录和账本；启动时补齐派生的 Skills 配置与事实源目录，不要求删除业务项目。
- 左上角与设置中恢复产品版本、八项组件版本和版本更新日志，切换业务项目不会改变已安装程序的版本信息。

本次使用最终 EXE 完成隔离安装、8,888 项文件校验、初始化、启动与退出；连续 10 次 HTTP 重启和 10 次项目切换通过，重开恢复项目选择，测试项目配置与内容保持不变。页面重启按钮也已验证：旧进程退出、新进程启动，页面自动重连并保留所选项目和版本信息。未执行付费模型任务、手机端完整业务流程或全量升级/回滚矩阵；仍是未签名的 Preview。

## 安装 CodeFlowMu

1. 校验实际下载的 CodeFlowMu 安装器 SHA-256 与 `SHA256SUMS.txt` 一致。
2. 双击安装器。
3. 按安装向导完成安装。
4. 从开始菜单或桌面快捷方式启动 **CodeFlowMu**。

安装向导先显示品牌欢迎页、产品名称、完整候选号和 Logo，再显示可编辑的目录选择页，并在写入前再次确认目标目录。

V2.2.2 Preview 4 使用当前用户安装模式；选择当前用户可写的目录，例如 `E:\CodeFlowMu`。该目录本身就是默认项目根，初始化后协作文件位于其 `fcop` 子目录，运行状态、日志、Provider 和升级缓存位于 `data`。不再默认写入 `C:\ProgramData\CodeFlowMu` 或创建 `projects\default`。

全新安装无需迁移数据；已有旧项目时先自行备份。安装器不会擅自删除历史 C 盘目录。不要把整个盘符根目录或已有重要文件的目录当作临时测试目录。

## 退出 CodeFlowMu

关闭浏览器不等于关闭后台。右键 Windows 通知区域的 CodeFlowMu 图标，选择“退出 CodeFlowMu”并确认；图标可能位于通知区域的展开列表中。

也可选择开始菜单的 **Exit CodeFlowMu**，或在安装目录运行：

```text
CodeFlowMu.exe --exit
```

程序先请求正常停止，超时才结束本次运行的进程树。退出会停止当前任务并断开手机连接；不需要手动结束其他 `node.exe` 或 `python.exe`。

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
E:\CodeFlowMu\data\providers\cursor\
├─ versions\<version>\
├─ current\
└─ current.json
```

Cursor Provider 与 CodeFlowMu 本体使用不同版本生命周期。正式支持的 Provider 版本必须与该 CodeFlowMu Release 附带的 `cursor.json` 一致；不要把未经验证的新 bridge 版本直接当作正式生产版本。

## 数据与升级

程序升级不得把客户工作数据当作程序文件覆盖或删除。升级前仍建议对重要工作区、Evidence、Audit、Reports 和配置进行备份。

PC 程序按“产品版本 + 候选号”检查签名更新源。检测到更高完整版本先提示，确认后才下载并校验完整安装包，使用当前目录升级并重启。相同版本不重复下载，旧版本不会作为升级目标。V2.2.2 Preview 4 本次仅提供 GitHub 手动下载，不在更新源中；本次也未宣称全量升级回归已完成。

发行工作台只有在安装包通过隔离安装、首次项目初始化和正常启动验收，并由维护者明确发布为 Pre-release 后，才激活该版本的更新源。仓库仍为 Private 时，未认证的外部客户无法使用 GitHub 更新源；这不会绕过公开前验收。

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
