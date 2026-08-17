---
title: Security Policy — Planning Poker - Best Planner
---

# Security Policy

**App:** Planning Poker - Best Planner

**Last updated:** 14 August 2026

[← Documentation home](index.md)

This policy describes how Planning Poker - Best Planner ("the app"), developed and maintained by Vudia, protects your data and manages security risk. It complements our [Privacy Policy](privacy.md).

## 1. Architecture and Hosting

The app is built on **Atlassian Forge** and runs entirely on Atlassian's infrastructure. It has no servers of its own, stores no data outside Atlassian, and makes no outbound network calls — the Forge platform blocks them entirely, and the app declares no external permissions in its manifest.

Because of this, most of the infrastructure-level controls a traditional SaaS vendor would have to build and operate themselves — TLS termination, HSTS, DDoS protection, encryption of data at rest, physical security, and platform patching — are provided directly by Atlassian under its shared responsibility model, and are covered by Atlassian's own SOC 2 Type II and ISO 27001 certifications. We do not operate any infrastructure of our own that would fall outside that model.

## 2. Data We Handle

Full detail is in the [Privacy Policy](privacy.md); in summary:

- We store game configuration, participant account IDs, display names, avatar URLs, work item keys and summaries, votes with timestamps, and final estimates — in **Forge's key-value storage**, encrypted at rest by Atlassian, in the same region as your Atlassian Cloud site.
- We never store passwords, email addresses, payment details, or full issue content.
- Every read from Jira happens through the requesting user's own Jira permissions; the app never shows a user anything they couldn't already see in Jira.
- The only write back to Jira is the final estimate, sent only when a facilitator explicitly clicks **Save estimate**, using that facilitator's own edit permissions.
- The "Suggest estimate" feature runs a local JQL query over your own Jira data — it does not call any AI/ML service, and no data leaves Atlassian's infrastructure for it.
- CSV exports are generated client-side, in your browser, from data already on screen — they are never generated or stored on a server.
- Deleting a game immediately and irreversibly removes its data from Forge storage. Estimates already written to Jira issues are not affected. Uninstalling the app follows Atlassian's standard Forge app lifecycle and data-removal policy.

## 3. Authentication and Access Control

The app has no login or credential system of its own. Every request is authenticated and scoped by Atlassian's Forge platform using the installing site's own Jira session — we never collect, transmit, or store Atlassian usernames, passwords, or API tokens.

Within the app, permissions map directly onto Jira: to participate in a game, a user needs **Browse Projects** on the relevant project; to save an estimate as facilitator, they need **Edit Issues**. The app does not grant any access beyond what a user already has in Jira.

The app's declared scopes are limited to what the product needs: read access to projects, work items, JQL and users; write access to work items; board read access; and Forge storage. No external or outbound permissions are declared.

## 4. Internal Security Practices

- **Team access:** Development is done by a small team; access to the GitHub organization (`uvd020-tech`) and the Atlassian Developer Console is limited to the people who need it.
- **MFA:** Multi-factor authentication is enforced on our GitHub organization, Atlassian Developer Console, and email accounts.
- **Credential storage:** Team members use a password manager for all work-related credentials; no shared or reused passwords for these systems.
- **Dependency management:** Dependabot is enabled on our GitHub repositories and automatically opens pull requests when a dependency has a known vulnerability.
- **Code changes:** Changes are made on feature branches and reviewed before being merged and deployed via the Forge CLI.

## 5. Vulnerability Management

We follow OWASP Top 10 guidance during development and rely on Dependabot to flag vulnerable dependencies as they're disclosed.

We are evaluating enrollment in the Atlassian Marketplace–managed security bug bounty program (via Bugcrowd), which Atlassian provides to partners at no cost, ahead of Atlassian's requirement that such programs be public by June 30, 2026.

Vulnerabilities reported to us — whether by Atlassian, a researcher, or a customer — are triaged and fixed within Atlassian's Marketplace SLA timeframes for cloud apps (currently 10 days for Critical severity, 28 days for High severity).

## 6. Incident Response

If we identify or are notified of a security incident affecting the app:

1. We investigate and confirm scope and impact.
2. We notify Atlassian within 24 hours via a P1 support ticket, as required of Marketplace partners.
3. We contain and remediate the issue.
4. We notify affected customers directly if their data was affected.
5. We review the incident afterward and adjust our practices if needed.

To report a suspected vulnerability or security incident, email **security@vudia.site**. For general support, use **info@vudia.site** (response within two business days); security reports are prioritized ahead of general support requests.

## 7. Business Continuity

Because the app has no infrastructure of its own, its availability depends on Atlassian Forge's own SLAs and uptime — we do not operate servers, databases, or backups that could independently fail. There is no customer data to back up outside of Forge storage, which Atlassian operates and protects as part of the platform.

## 8. Third-Party Risk

The only third party in our data flow is **Atlassian** itself, which hosts, encrypts, and operates the Forge storage the app uses, under its own SOC 2 Type II, ISO 27001, and other certifications. We do not use any other subprocessor, analytics service, or external API.

## 9. Compliance

We do not hold independent security certifications (e.g., SOC 2, ISO 27001) at this time; as a Forge app, we inherit the corresponding infrastructure, storage, and hosting controls from Atlassian's certified platform. We comply with Atlassian's Marketplace security requirements for cloud apps.

## 10. Policy Review

This policy is reviewed at least annually, and whenever we make a material change to the app's architecture, data handling, or team.

## Contact

- **Security reports / vulnerability disclosure:** security@vudia.site
- **General support:** info@vudia.site — see [Support](support.md)
- **Privacy questions:** see our [Privacy Policy](privacy.md)

---

[← Privacy Policy](privacy.md) · [Documentation home](index.md) · [Support →](support.md)
