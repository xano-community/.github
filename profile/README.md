# Xano Community

Open-source Xano code, shared by the community. Push it to your workspace with the [Xano CLI](https://docs.xano.com/cli) — or hand the repo URL to [Claude Code](https://github.com/xano-inc/xano-developer-mcp) and let it install for you — then make it yours.

🌐 [xano.com](https://xano.com) &nbsp;·&nbsp; 📚 [docs](https://docs.xano.com) &nbsp;·&nbsp; 💬 [community](https://community.xano.com)

---

## 📦 Repo types

Every repo falls into one of four categories. Filter by topic to browse.

| Type | What it is | Filter by |
| :--- | :--- | :--- |
| 🏗️ **Template** | A full or partial app — backend (often frontend too), meant to be forked as a starting point | [`xano-template`](https://github.com/xano-community?q=topic%3Axano-template) |
| 🔌 **Integration** | Functions, endpoints, or workflows that connect Xano to an external service | [`xano-integration`](https://github.com/xano-community?q=topic%3Axano-integration) |
| 🧩 **Module** | A reusable unit that combines multiple pieces for a broader directive (audit logging, RBAC, retries) | [`xano-module`](https://github.com/xano-community?q=topic%3Axano-module) |
| ⚡ **Action** | A single function (or tight set) that does one precise thing | [`xano-action`](https://github.com/xano-community?q=topic%3Axano-action) |

Every repo also carries 1–2 **domain** topics (`payments`, `notifications`, `ai` …) and an optional **specific** topic (`stripe`, `openai`, `slug`). Stack filters in GitHub search to narrow down — e.g. [`topic:xano-integration topic:payments`](https://github.com/xano-community?q=topic%3Axano-integration+topic%3Apayments).

Full tag taxonomy and naming conventions in [CONTRIBUTING.md](https://github.com/xano-community/.github/blob/main/CONTRIBUTING.md).

---

## 🔌 Integrations

Third-party API wrappers. Each repo ships XanoScript functions you can push straight to your workspace.

#### Payments & Commerce
- [integration-stripe-payments](https://github.com/xano-community/integration-stripe-payments) — payments, customers, subscriptions, checkout
- [integration-paypal-payments](https://github.com/xano-community/integration-paypal-payments) — checkout orders and captures
- [integration-square-payments](https://github.com/xano-community/integration-square-payments) — card payments and customers
- [integration-plaid-banking](https://github.com/xano-community/integration-plaid-banking) — bank account linking
- [integration-shopify-commerce](https://github.com/xano-community/integration-shopify-commerce) — product catalog and orders

#### Messaging & Communications
- [integration-slack-messaging](https://github.com/xano-community/integration-slack-messaging) — messages, channels, file uploads
- [integration-discord-messaging](https://github.com/xano-community/integration-discord-messaging) — channel notifications via bot or webhook
- [integration-intercom-messaging](https://github.com/xano-community/integration-intercom-messaging) — contacts and in-app messages
- [integration-twilio-sms](https://github.com/xano-community/integration-twilio-sms) — SMS, WhatsApp, phone verification
- [integration-resend-email](https://github.com/xano-community/integration-resend-email) — transactional email
- [integration-mailchimp-email](https://github.com/xano-community/integration-mailchimp-email) — subscribers and campaigns

#### CRM & Support
- [integration-salesforce-crm](https://github.com/xano-community/integration-salesforce-crm) — leads and record queries
- [integration-hubspot-crm](https://github.com/xano-community/integration-hubspot-crm) — contacts and deals
- [integration-zendesk-support](https://github.com/xano-community/integration-zendesk-support) — ticket management
- [integration-gorgias-support](https://github.com/xano-community/integration-gorgias-support) — tickets, messages, customer sync

#### Developer Tools
- [integration-github-issues](https://github.com/xano-community/integration-github-issues) — issues and webhooks
- [integration-gitlab-devops](https://github.com/xano-community/integration-gitlab-devops) — issues, merge requests, webhooks
- [integration-jira-issues](https://github.com/xano-community/integration-jira-issues) — issue creation and workflow transitions

#### Infrastructure & Monitoring
- [integration-cloudflare-edge](https://github.com/xano-community/integration-cloudflare-edge) — cache purging and DNS
- [integration-datadog-monitoring](https://github.com/xano-community/integration-datadog-monitoring) — custom events and metrics
- [integration-pagerduty-incidents](https://github.com/xano-community/integration-pagerduty-incidents) — incident creation and resolution
- [integration-launchdarkly-feature-flags](https://github.com/xano-community/integration-launchdarkly-feature-flags) — feature flag management

#### AI & Productivity
- [integration-openai-ai](https://github.com/xano-community/integration-openai-ai) — text completions and embeddings
- [integration-google-sheets](https://github.com/xano-community/integration-google-sheets) — read, write, and append rows

<sub>**Also:** [template-integration-discord](https://github.com/xano-community/template-integration-discord) — the original webhook-focused Discord example, preserved as a reference.</sub>

---

## 🏗️ Templates

Finished apps and reusable pieces you can fork.

#### Full apps

Each ships a XanoScript backend you push to your workspace and a single-file HTML frontend that prompts for your Xano instance URL on first load.

| App | What it is |
| :--- | :--- |
| [support-ticketing](https://github.com/xano-community/support-ticketing) | Support / helpdesk ticketing with SLAs, priorities, categories, comments, and a dashboard |
| [asset-tracking](https://github.com/xano-community/asset-tracking) | IT asset inventory with assignments, maintenance logs, locations, and categories |
| [purchase-approvals](https://github.com/xano-community/purchase-approvals) | Purchase requisitions with line items, vendors, and sequential multi-step approvals |
| [template-full-app-guestbook](https://github.com/xano-community/template-full-app-guestbook) | Guestbook backend plus a vanilla-JS frontend |

#### Snippets

- [template-snippet-slugify](https://github.com/xano-community/template-snippet-slugify) — reusable slug function *(snippet is the older term for **action**)*

#### Scaffolds

Starting points for publishing your own template, integration, or action.

| Scaffold | Use for |
| :--- | :--- |
| [template-starter-full-app](https://github.com/xano-community/template-starter-full-app) | Full-stack app |
| [template-starter-integration](https://github.com/xano-community/template-starter-integration) | Third-party API wrapper |
| [template-starter-snippet](https://github.com/xano-community/template-starter-snippet) | Single function (use for actions) |

---

## 🧩 Modules

Reusable building blocks — bigger than an action, smaller than an app. Each ships tables, helper functions, and a tight HTTP surface you can drop into any workspace.

| Module | What it is |
| :--- | :--- |
| [audit-log](https://github.com/xano-community/audit-log) | Append-only audit-event capture with a reusable record function and filtered query/stats APIs, so any XanoScript can log who did what to which resource |
| [rbac](https://github.com/xano-community/rbac) | Role-based access control with roles, permissions, user assignments, and a single `check` function you can drop into any endpoint to gate access |
| [notify-router](https://github.com/xano-community/notify-router) | Multi-channel notification router that fans a single `notify` call out to email, SMS, Slack, and webhook channels based on per-user, per-topic preferences |
| [webhook-inbox](https://github.com/xano-community/webhook-inbox) | Inbound webhook receiver with per-source HMAC verification, automatic idempotency on replays, and every request persisted for downstream processing |
| [job-retry](https://github.com/xano-community/job-retry) | Durable job queue with atomic claim, exponential-backoff retries, and a dead-letter tier you can inspect and requeue from |

Got an idea for another? [Open an issue](https://github.com/xano-community/.github/issues).

---

## ⚡ Actions

*Coming soon.* Want to contribute one? [Open an issue](https://github.com/xano-community/.github/issues) with your idea, or start from [`template-starter-snippet`](https://github.com/xano-community/template-starter-snippet).

---

## 🛠️ Install anything in this org

**Option A — Claude Code** (with the [Xano MCP](https://github.com/xano-inc/xano-developer-mcp) enabled)

> Install the repo at `<URL>` into my Xano workspace.

**Option B — Xano CLI**

```sh
git clone <repo-url>
cd <repo>
xano workspace:push . -w <your-workspace-id>
```

Full CLI docs → https://docs.xano.com/cli

---

## 🤝 Contributing

We welcome templates, integrations, modules, and actions from the community. See [CONTRIBUTING.md](https://github.com/xano-community/.github/blob/main/CONTRIBUTING.md) for tag taxonomy, naming conventions, and the quality bar.

---

## 🧰 More from Xano

- [**Xano CLI**](https://github.com/xano-inc/cli) — use Xano from your terminal
- [**Xano MCP**](https://github.com/xano-inc/xano-developer-mcp) — plug Xano into AI coding agents
- [**Docs**](https://docs.xano.com) &nbsp;·&nbsp; [**Community**](https://community.xano.com) &nbsp;·&nbsp; [**Blog**](https://xano.com/blog)
