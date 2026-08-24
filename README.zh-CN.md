# CodeFlowMu

<p align="center">
  <img src="assets/brand/codeflowmu-logo.png" alt="CodeFlowMu" width="132">
</p>

<p align="center"><strong>把一个软件需求交给本地的 PM · DEV · QA · OPS 四人数字开发团队，获得可见、可接管、可验证、可验收的交付过程。</strong></p>

<p align="center"><strong>软件开发不是一段对话，而是一条由角色、任务、工具、证据和人工决策组成的协作流。</strong></p>

<p align="center">免费公开预览 · 专有软件 · Windows x64 · 本地优先控制面</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="#五分钟启动半小时完成第一个任务">快速开始</a> ·
  <a href="FIRST-PWA-TASK.zh-CN.md">第一个 PWA 任务</a> ·
  <a href="CUSTOMER-INSTALL.zh-CN.md">安装手册</a> ·
  <a href="ARCHITECTURE.zh-CN.md">架构</a> ·
  <a href="https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases">下载</a>
</p>

> [!IMPORTANT]
> 这是 **CodeFlowMu 专有软件免费公开预览版**的发行仓库，不是源码仓库，也不授予开源许可证。当前 `v1.9.7-candidate.1` 是未签名的候选预发行版，不是稳定版或正式支持版本。仓库目前保持 Private，等待产品验收和明确的公开批准。

## 为什么不是另一个聊天窗口

一次回答不等于一次交付。真正的软件开发需要范围、分工、运行、验证、返工、证据和最终决策。CodeFlowMu 把这些环节放进同一个本地控制面：

```text
需求
→ PM 澄清、规划和分派
→ DEV 实现 + OPS 运行交付 + QA 验证回归
→ REPORT 与运行证据
→ PM 复核
→ 人工批准、驳回或继续
```

任务、报告、审批、文件、实时活动和交付证据彼此关联。人可以知道团队正在做什么、为什么这样做、实际产生了什么，以及什么时候必须接管。

## 60 秒看懂产品

[![观看 CodeFlowMu 60 秒介绍](assets/video-poster.png)](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v1.9.7-candidate.1/CodeFlowMu-60s-overview-v1.9.7.mp4)

视频使用真实产品界面，展示 PC 控制中心、任务树、人工门禁、验证证据和 CodeFlowMu Mobile PWA。[直接下载 MP4](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v1.9.7-candidate.1/CodeFlowMu-60s-overview-v1.9.7.mp4)。

## 五分钟启动，半小时完成第一个任务

### 五分钟：安装并打开控制中心

1. 使用 Windows 10/11 x64 电脑。
2. 从 [V1.9.7 Candidate 1](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v1.9.7-candidate.1) 下载安装器和 `SHA256SUMS.txt`。
3. 校验安装器 SHA-256：`15c96e86d0583540793d0178727a1082ef38395831c460c988d9efc4ad2aca86`。
4. 安装并启动 **CodeFlowMu**。
5. 确认顶部连接状态正常，并在设置中注册一个空白示例项目。

> [!WARNING]
> Candidate 1 尚未签名，Windows SmartScreen 可能警告；正式 Cursor 账户兼容门禁尚未通过。安装根不是业务项目，不能让 Agent 在安装目录中开发。Provider 账户、凭据和可能产生的调用费用与 CodeFlowMu 免费预览彼此独立。

### 半小时：让团队交付一个真正的静态 PWA

第一个标准任务不是“Hello World”，而是一个可以安装、离线使用并静态托管的 **ShipReady PWA**：

- 新增、完成、取消完成和删除今日交付事项；
- 使用 `localStorage` 保存数据；
- 适配手机与桌面；
- 提供 Web App Manifest 与 Service Worker；
- 首次加载后可离线打开；
- 不使用后端、数据库、CDN 或外部 API；
- 可部署到 GitHub Pages、Cloudflare Pages 或任意 HTTPS 静态站点。

复制下面的任务给 PM：

```text
请开发并交付一个名为 ShipReady 的静态 PWA 小应用。

用户可以新增、完成、取消完成和删除“今日交付事项”；页面显示总数、
已完成数和完成百分比；数据保存在 localStorage；支持 390px 手机宽度；
提供 manifest.webmanifest、Service Worker、192/512 图标和 README；
不使用后端、数据库、CDN 或外部 API。首次加载后断网仍可打开使用。

QA 必须逐条验证功能、刷新持久化、响应式、Manifest、Service Worker、
离线模式和控制台错误；OPS 必须提供本地运行方式。任何公网部署都要先
获得我的明确批准，再返回部署 URL 和验证证据；PM 最后汇总交付和限制。
```

完整的逐屏操作、成功信号、角色分工、验收表、静态部署和 PWA 续接流程见：[手把手完成第一个 ShipReady PWA](FIRST-PWA-TASK.zh-CN.md)。

## 第一个任务会发生什么

| 阶段 | 角色动作 | 你应该看到的成功信号 |
| --- | --- | --- |
| 需求进入 | 你把任务交给 PM 并检查发布内容 | 正式 TASK 出现在任务列表 |
| 规划分派 | PM 固定范围、验收标准和子任务 | 任务树出现 DEV、QA、OPS 工作 |
| 工程实现 | DEV 创建静态文件和 PWA 能力 | 项目中出现页面、Manifest、Service Worker 和图标 |
| 运行交付 | OPS 启动本地静态服务并记录入口 | 本地 URL 可访问；若要公网部署会先请求批准 |
| 验证回归 | QA 检查功能、手机布局、持久化和离线 | REPORT 对每条验收标准给出 PASS/FAIL 与证据 |
| 复核验收 | PM 汇总结果、限制和返工项 | 人选择接受、驳回或继续修改 |

这个案例同时展示 CodeFlowMu 的核心原则：**指令成流，证据回流，由人决策。**

## 当前产品：四人数字开发团队

| 角色 | 当前职责 | 第一个 PWA 案例中的工作 |
| --- | --- | --- |
| **PM** | 澄清需求、规划、分派和复核 | 固定范围、验收标准和交付结论 |
| **DEV** | 在授权项目内实现和重构 | 实现 UI、交互、存储、Manifest 和 Service Worker |
| **QA** | 验证标准、测试行为和报告回归 | 验证功能、390px 布局、离线、安装条件和错误 |
| **OPS** | 运行环境、构建产物和记录证据 | 启动静态服务；获批后部署并验证公网 URL |

人始终是 ADMIN：决定项目范围，持有凭据，批准外部写入和风险操作，并依据报告与证据完成最终验收。

## 从理论到工程

CodeFlowMu 不是孤立产品，而是一条从治理思想落到软件交付的连续路径：

```text
TMPA：为什么数字员工必须可治理、可追溯、可验收
  ↓
FCoP：任务、报告、问题、复核和证据如何持久化
  ↓
PM / DEV / QA / OPS：谁对哪一段工作负责
  ↓
Skills / Playbooks：每个角色按什么方法和证据标准工作
  ↓
MCP / 受控工具：角色能够连接和调用哪些工程能力
  ↓
PC 控制中心 + Mobile PWA：人在何处观察、下令、接管和审批
  ↓
REPORT / Evidence / Human Gate：如何证明完成并由人决定结果
```

| 层 | 公开项目或产品职责 |
| --- | --- |
| 理论与规范 | [TMPA / Digital Employee Works](https://github.com/joinwell52-AI/joinwell52)：治理架构、规范 Core、符合性与证据思想 |
| 协作协议 | [FCoP](https://github.com/joinwell52-AI/FCoP)：MIT 许可的文件化行为治理协议 |
| 早期产品验证 | [CodeFlowMu-open](https://github.com/joinwell52-AI/CodeFlowMu-open)：早期开源四角色团队，现已维护冻结 |
| 当前产品 | **CodeFlowMu Distribution**：专有安装产品、独立 Runtime、PC/PWA、Provider 与发行证据 |
| 长期路线 | **数字员工开发机**：生产、测试、装配和升级数字员工包；尚不是当前能力 |

思想和协议连续，产品工程与发行边界升级。`CodeFlowMu-open` 不是当前专有产品的源码，旧版安装方式、端口、能力和支持状态也不能直接套用到当前版本。

## Skill、MCP、权限与证据

| 概念 | 它回答什么 | 它不能自行决定什么 |
| --- | --- | --- |
| **Role** | 谁负责规划、实现、验证或运行 | 不能因为角色名称自动获得全部权限 |
| **Skill / Playbook** | 角色应按什么步骤、约束和证据标准工作 | Skill 不是工具，也不自动产生执行权 |
| **MCP / Tool** | Agent 可以连接并调用什么外部能力 | 工具可调用不代表任务合法、结果可信 |
| **Permission** | 本次操作是否被项目和人授权 | 不能由 Skill 或 MCP 自行扩大 |
| **FCoP** | TASK、REPORT、ISSUE、REVIEW 如何持久化与交接 | 协议记录不能替代真实运行结果 |
| **Evidence** | 如何证明文件、命令、测试或页面真实产生 | 证据本身不能替人接受业务风险 |
| **Human Gate** | 谁批准外部写入、敏感动作和最终交付 | 技术检查不能替代人的产品验收 |

Candidate 1 包含 Skill schema、FCoP 受控 MCP 执行边界和 Browser Use 运行组件；具体能力只有在产品实际提供、项目启用并获得授权时才可使用。本 README 不承诺自动安装任意社区 MCP，也不把未验证工具描述为正式支持能力。

## 真实产品界面

| PC 控制中心 | 任务树 |
| --- | --- |
| ![CodeFlowMu PC 控制中心](assets/screens/desktop-control-center.png) | ![CodeFlowMu 任务树](assets/screens/task-graph.png) |

| 运行与协议证据 | CodeFlowMu Mobile PWA |
| --- | --- |
| ![CodeFlowMu 运行证据](assets/screens/runtime-evidence.png) | <img src="assets/screens/mobile-pwa.png" alt="CodeFlowMu Mobile PWA" width="260"> |

## CodeFlowMu Mobile PWA：离开电脑后继续管理交付

CodeFlowMu Mobile PWA 是运行中 PC 实例的远程控制入口，不是脱离 PC 独立执行的第二套产品。

```text
PC 启动 CodeFlowMu
→ 在“移动端”页面刷新 Gateway 与绑定信息
→ 手机通过局域网或公网 Gateway 绑定
→ 查看 ShipReady 任务树、角色状态、REPORT 和实时活动
→ 从手机向 PM 追加“增加深色模式”
→ 阅读第二轮 QA/OPS 证据
→ 处理需要人工决定的审批与验收
```

绑定时不要分享二维码或绑定链接；丢失或停用的设备应从 PC 解除绑定。PWA、Gateway、PC 产品和 Provider 使用不同版本生命周期。完整步骤见[中文安装与 PWA 指南](CUSTOMER-INSTALL.zh-CN.md)。

## 当前能力与路线边界

### 当前已经提供

- Windows x64 安装包与内置基础 Node.js/Python Runtime；
- PC 控制中心：项目、任务、报告、审批、文件、日志、技能和运行状态；
- 固定 PM / DEV / QA / OPS 团队与可见任务树；
- FCoP 文件化任务、报告、问题、复核与证据协作；
- 人工门禁和项目授权边界；
- 绑定运行中 PC 的 Mobile PWA；
- 外部 Provider 生命周期以及 Release manifest、安全与第三方许可证据。

### 仍然只是路线

“数字员工开发机”将面向可复用数字员工包的生产、测试、装配和升级。在这些能力真实交付并具备自己的证据、兼容和生命周期合同之前，不进入当前产品承诺。

## 哪些可以公开

| 可以公开 | 必须保持私有 |
| --- | --- |
| 产品思想、架构、四角色职责和真实脱敏截图 | 当前专有产品源码和私有实现历史 |
| TMPA、FCoP 公开规范与项目关系 | 内部母版 Skill、未发布治理实验和私有评估策略 |
| Skill 格式、分层、公开模板和脱敏 Playbook 示例 | 客户项目 Skill、业务知识、任务、报告、日志和数据 |
| MCP 在架构中的位置、受控工具分类和安全原则 | Gateway 凭据、Provider 密钥、客户 MCP 配置和私有后台拓扑 |
| 安装、第一次任务、PWA 绑定和静态部署教程 | 签名材料、发行凭据、内部测试账户和私有流水线 |
| 安装包、哈希、manifest、第三方许可与公开安全证据 | 未完成脱敏和公开审查的任何构建或运行材料 |

仓库可见性变为 Public 不等于产品开源。技术检查通过也不等于产品验收完成；只有仓库所有者明确验收并批准后才能公开。

## 文档与支持

- [手把手完成第一个 ShipReady PWA](FIRST-PWA-TASK.zh-CN.md)
- [中文安装、Provider、Mobile PWA 与升级说明](CUSTOMER-INSTALL.zh-CN.md)
- [架构与信任边界](ARCHITECTURE.zh-CN.md)
- [English README](README.md)
- [Release Policy](RELEASE-POLICY.md)
- [公开仓库门禁记录](PUBLICATION-CHECKLIST.md)
- [支持政策](SUPPORT.md)
- [安全政策](SECURITY.md)
- [专有软件说明](LICENSE.md)

公开后可通过 GitHub Issues 提交脱敏后的可复现问题。严禁公开提交 API Key、绑定链接、客户数据、私有源码或内部任务；安全漏洞必须按 [SECURITY.md](SECURITY.md) 私下报告。

---

**指令成流，证据回流，由人决策。**
