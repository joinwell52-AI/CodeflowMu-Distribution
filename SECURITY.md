# Security Policy

## Release status

CodeFlowMu does not yet have a formally supported stable release. `v1.9.7-candidate.1` is an unsigned public-preview candidate. Its Release notes identify the outstanding Cursor account compatibility gate.

The candidate includes SHA-256, installed-file inventory, third-party notices and security review artifacts. These artifacts are evidence for review, not a claim that pre-release software is risk-free.

## Report a vulnerability privately

Do not open a public issue for a suspected vulnerability. Use this repository's **Security → Report a vulnerability** flow:

<https://github.com/joinwell52-AI/CodeflowMu-Distribution/security/advisories/new>

Include the affected version, component, impact, reproduction steps and any safe proof of concept. Remove API keys, bind links, customer data and unrelated private source. We will acknowledge and triage reports on a best-effort basis during the preview.

## Current candidate notes

- The Candidate 1 installer is not code-signed and may trigger Windows SmartScreen. Verify the published SHA-256 before execution.
- Cursor is an external Provider runtime and uses customer-owned credentials. Candidate 1 has not passed the formal real-account compatibility gate.
- `security-risk-acceptance.json` records a contextual low-severity acceptance for `body-parser 2.2.2`. Repository visibility is a review trigger; this public-preview documentation preserves the mitigation assumptions and does not promote Candidate 1 to a formal release.
- The effective runtime audit and the explicit risk-acceptance artifact use different reporting scopes. Review both artifacts together; do not infer formal release readiness from a zero effective-count field alone.

## Customer precautions

- Download only from this repository's Releases and compare hashes.
- Keep credentials out of projects, screenshots, reports and Git history.
- Register only projects the digital team is authorized to access.
- Review human gates and evidence before accepting sensitive changes.
- Revoke lost Mobile devices and expired or exposed bind links.
- Back up important project and evidence data before upgrading or uninstalling.

## Distribution integrity

The public repository must not contain CodeFlowMu product source, source maps, development credentials, customer data or committed installers. Installers and immutable release evidence belong only in GitHub Releases. See [RELEASE-POLICY.md](RELEASE-POLICY.md).

---

## 中文摘要

CodeFlowMu 目前没有正式支持的稳定版；`v1.9.7-candidate.1` 是未签名的公开预览候选版。运行前必须校验 SHA-256。Cursor 使用外部 Provider Runtime 和客户自己的凭据，该候选版尚未通过真实账户兼容门禁。

请勿公开报告漏洞。使用仓库 **Security → Report a vulnerability** 私下提交，并删除 API Key、绑定链接、客户数据和无关私有源码。预览期按尽力原则确认和处理报告。
