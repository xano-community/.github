# Contributing to Xano Community

Thanks for wanting to contribute. This org is a shared library of Xano code: **templates**, **integrations**, **modules**, and **actions**. The goal is discoverability — anyone should be able to find and install what they need in under a minute.

This guide covers the shared conventions that apply to every repo in the org. Individual repos may add their own `CONTRIBUTING.md` for details specific to that codebase.

---

## 1. Pick a type

Every repo must fit into exactly one of these four categories. Pick the one that matches the **scope** of what you're shipping — not the topic.

| Type | Scope | Example |
| --- | --- | --- |
| **`xano-template`** | A full or partial app: backend structure, often frontend too. A starting point for building a complete app. | `template-saas-starter`, `template-marketplace-app` |
| **`xano-integration`** | A set of endpoints, functions, or workflows that connect Xano to one external service or platform. | `integration-stripe-payments`, `integration-twilio-sms` |
| **`xano-module`** | A moderately sized, reusable unit of logic that combines multiple pieces for a broader directive. | `module-lead-qualification`, `module-ticket-triage` |
| **`xano-action`** | A single function (or a tight set) that performs one precise task. | `action-generate-slug`, `action-format-phone-number` |

**If you're unsure, go smaller.** An action that wraps `openai.chat_completion` is better than a "module" that does the same thing with extra ceremony.

Don't wrap things Xano already ships natively. If there's a first-class XanoScript statement for it (Resend via `util.send_email`, S3 via `cloud.aws.s3.*`, Redis, Algolia, Elasticsearch), point users to that instead of building a parallel wrapper.

---

## 2. Name the repo

The repo name always follows this pattern:

```
<type>-<domain>-<specific>
```

- **`<type>`** — one of `template`, `integration`, `module`, `action`
- **`<domain>`** — a broad problem space (see the domain list below)
- **`<specific>`** — the exact thing, usually the service or task name

Examples:

| Repo name | Type | Domain | Specific |
| --- | --- | --- | --- |
| `integration-stripe-payments` | integration | payments | stripe |
| `integration-openai-ai` | integration | ai | openai |
| `module-lead-qualification` | module | (embedded in name) | lead-qualification |
| `action-generate-slug` | action | (embedded in name) | generate-slug |
| `template-saas-starter` | template | saas | starter |

The `<specific>` can be omitted when the `<domain>` already pins it down — e.g. `action-generate-slug` doesn't need a `<specific>` because "generate-slug" is already specific.

Keep names kebab-case, lowercase, no underscores.

---

## 3. Add topics

Every repo gets **3–5 GitHub topics** chosen from three tiers:

### Tier 1 — Type (required, exactly one)

| Topic | For |
| --- | --- |
| `xano-template` | Templates |
| `xano-integration` | Integrations |
| `xano-module` | Modules |
| `xano-action` | Actions |

### Tier 2 — Domain (required, 1–2 max)

Broad problem spaces. These should describe the _product surface area_, not the technology. Pick from:

- `auth`
- `payments`
- `database`
- `files`
- `notifications`
- `messaging`
- `realtime`
- `ai`
- `search`
- `security`
- `analytics`
- `monitoring`
- `commerce`
- `crm`
- `support`
- `devops`

If none fit, propose a new one in your PR — we'd rather add a domain than have it stuffed into `other`.

### Tier 3 — Specific (optional)

The exact thing, when it's useful for discovery. Examples:

- Integrations: `stripe`, `openai`, `twilio`, `checkout`, `webhooks`
- Modules: `lead-qualification`, `message-routing`, `ticket-triage`
- Actions: `slug`, `rate-limit`, `jwt`, `email-validation`
- Templates: `saas`, `marketplace`, `crm`, `chat`

**Total: 3–5 topics per repo.** Any more is noise.

---

## 4. Meet the quality bar

These rules apply to all types:

- **One definition per `.xs` file.** One function per file, one table per file. Never mix.
- **No hardcoded credentials.** API keys, tokens, webhook URLs — all go through `$env.*`. Document every env var in `.env.example`.
- **MIT license** unless you have a specific reason. Copyright holder is your name or org.
- **Include a README.** At minimum: what this is, how to install, what env vars it needs, one usage example.

Type-specific rules:

### Integrations
- Every `api.request` must be followed by a status-code `precondition`. Non-2xx responses must raise, never silently succeed. This is the single most important hygiene rule for this category.
- Use `set_ifnotempty` for optional params (not `set_ifnotnull`) — empty strings matter on form submissions.
- `json_encode` response bodies before concatenating into error messages.

### Modules
- Modules combine multiple functions. Each sub-function lives in its own `.xs` file.
- If a module needs tables, include them in `tables/`.

### Actions
- One function, one job. If you find yourself writing a second function, it's probably a module.
- Keep inputs and outputs explicit and well-described.

### Templates
- Include both frontend (if applicable) and backend in clearly separated directories.
- The README should walk a new user from clone to running app.

---

## 5. Submit your work

1. **Draft in your own org or account.** Use the appropriate scaffold as a starting point:
   - Templates → [`template-starter-full-app`](https://github.com/xano-community/template-starter-full-app)
   - Integrations → [`template-starter-integration`](https://github.com/xano-community/template-starter-integration)
   - Actions → [`template-starter-snippet`](https://github.com/xano-community/template-starter-snippet)
   - Modules → no scaffold yet; use `template-starter-integration` as a loose reference and [open an issue](https://github.com/xano-community/.github/issues) so we can build one
2. **Validate your XanoScript** using the [Xano MCP](https://github.com/xano-inc/xano-developer-mcp)'s `validate_xanoscript` tool, or `xano-cli xs validate <file>`.
3. **Test against a real workspace.** `xano workspace:push` the repo and exercise the functions with real inputs.
4. **Open an issue** on [`xano-community/.github`](https://github.com/xano-community/.github/issues) with:
   - A link to your draft repo
   - Which type/domain/specific tags you'd use
   - A short description
5. **We'll review**, work with you on any tweaks, and transfer ownership into `xano-community`.

---

## 6. Updating an existing repo

- Open a PR against the repo directly.
- Keep changes focused. If you're fixing a bug, don't also refactor.
- Bump the version in `xano-template.json` (if present) when input/output shapes change.

---

## Questions

Open an issue on [`xano-community/.github`](https://github.com/xano-community/.github/issues) or drop into the [Xano community forum](https://community.xano.com).
