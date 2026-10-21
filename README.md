# Vaporware Detective

**Evidence-first AI investigation of crypto projects, tokens, websites, and claims.**

**Status:** Planning / initial repository. This README describes the product we intend to build, **not** capabilities currently deployed or verified.

Vaporware Detective is an independent, clean-room alternative inspired by the *investigation workflow* of [frfr.xyz](https://frfr.xyz/). It is **not** affiliated with frfr.xyz, does not use its private code, and will have original design, assets, wording, scoring, and branding.

## Mission

Answer one question with reproducible receipts: **Does the available evidence support what this project claims?**

We will separate two assessments that must not be conflated:
- **Claim authenticity:** what can actually be verified about the website, product, team claims, and code.
- **Token risk:** observable liquidity, holder concentration, authority settings, developer transactions, and related on-chain risks.

A real product can have a risky token; a missing data source is not evidence of fraud.

## Intended product

1. Paste a Solana mint address (future support: EVM token addresses, website URLs, X post URLs and public X accounts).
2. Watch **genuine** investigation events, not a fabricated progress animation.
3. Read a shareable, timestamped report with evidence-backed findings, source links, limitations, two separate assessments, and a plain-English explanation.
4. Re-run a check and compare immutable historic reports.
5. Ask questions grounded in the report; new research requires a clearly labeled new job.

## MVP — Solana first

- Input validation and exact asset resolution using **chain + contract/mint address**, never ticker alone.
- Market, token, holder, and on-chain security data from documented, authorized APIs and Solana RPC.
- Developer / creator-wallet transactions and launch signals where the evidence supports them; uncertainty explicitly recorded.
- Durable, resumable background investigations with QUEUED, RUNNING, PARTIAL, COMPLETE, and FAILED states.
- Deterministic rules for measurable token risks; AI only to synthesize evidence and explain conclusions.
- Versioned, shareable reports with sources, observation timestamps, and explicit UNKNOWN findings.
- Responsive, mobile-first site with input, real job progress, feed, report page, previous-check comparison, and sensible empty/error states.
- Cost caps, caching, rate limiting, tests, and developer setup documentation.

Do not introduce trading, live wallet signatures, token launching, paid services, or financial transactions in the MVP.

## Follow-on capabilities

### Website verification
Run Playwright in disposable, isolated workers to inspect public project websites, capture screenshots, follow links, and test benign product interactions. Compare actual observed behavior with specific advertised claims. Websites are untrusted; do not execute downloads or authorize wallet transactions.

### Social and source-code intelligence
Use authorized X access to inspect public claims and trace contract mentions when possible. Inspect publicly linked GitHub repositories to distinguish real source implementations from placeholder READMEs and unsupported claims. Mark unavailable data as UNKNOWN rather than fabricating findings.

### Developer and launch intelligence
Build creator-wallet profiles, repeat-launch histories, token-holder distribution studies, launch-block purchase analysis, and links to on-chain receipts. Shared funding and correlated timing are **signals**, not proof of common ownership or wrongdoing.

### Cross-chain expansion
Add EVM chain adapters only after the Solana workflow is independently tested and stable.

## Suggested architecture (design candidates, not yet implemented)

| Layer | Candidate |
| --- | --- |
| Frontend / API | Next.js, TypeScript, Tailwind CSS |
| Data | PostgreSQL (e.g. Neon), schema migrations |
| Jobs | Durable queue and separate worker runtime |
| Web investigation | Sandboxed Playwright |
| Solana | Solana RPC and Helius where authorized |
| Market data | DEX Screener and authorized GMGN endpoints where available |
| Social and source | Authorized X API, GitHub API |
| AI | Configurable evidence-grounded model provider |
| Hosting | Vercel web frontend; separate isolated worker deployment |

### Pipeline

```text
Input → Validate / resolve → Cache / dedupe → Durable job
      → Parallel read-only evidence collectors
      → Normalize evidence and compute coverage
      → Deterministic measurements and risk indicators
      → Grounded AI synthesis
      → Immutable versioned report → Public report URL
```

## Evidence contract

Every material finding must record:
- The precise claim or property being investigated.
- What was observed, how, and when.
- Source URL, chain and transaction signature, or verified capture reference.
- Evidence classification: VERIFIED, CONTRADICTED, PARTIAL, or UNKNOWN.
- Coverage, limitations, confidence, and scoring-rubric version.

Never turn missing evidence into proof of a scam. Never invent screenshots, transactions, metrics, social posts, references, prices, or browser tests. Distinguish score confidence from token-price outlook. Reports are not trading recommendations or guarantees.

## Security and operations

- Read-only blockchain investigation; **no private keys, trades, approvals, funds, or automatic signing**.
- Block SSRF, internal IP destinations, cloud metadata, DNS rebinding, unsafe redirects, and injected instructions from third-party pages.
- Use isolated browser workers with network restrictions, resource budgets, and disposable state.
- Sanitize evidence before rendering it; protect provider secrets on the server.
- Impose hard limits on model tokens, concurrency, API usage, retries, and browser steps.
- Never quietly activate paid providers, services, billing, or deployments.

## Build and release discipline

1. Inspect the existing [Real or BS skill](https://github.com/0xSneaks/phantom-skills) or other actual skill location **before** integrating; do not guess its contents or rewrite it. Treat the skill and this application as separate projects.
2. Build a functioning Solana investigation end-to-end, not just a polished demo.
3. Add automated tests for input identity, provider failure, job recovery, evidence integrity, SSRF, malicious webpages, concurrent requests, and responsive flows.
4. Label delivered work **VERIFIED**, **BLOCKED**, or **UNTESTED**, backed by command/test output.
5. Use a feature branch and PR; keep production and main protected from unreviewed changes.
6. Get owner approval before merging, public deployment, paid expenses, or enabling financial functionality.

## Agent assignments

- **Muse — OpenCode Go / Kimi K2.7 Code:** coordination, scoped coding tasks, tests, integration handoffs.
- **GPT-6.1 Sol:** lead engineer for core architecture and research engine, implementation support, complex debugging.
- **Astra:** independent architecture, evidence-quality, and security review.

**GLM is not part of this project's model stack.** Agents must confirm actual availability and authentication before using any model.

## Acceptance criteria for first working release

A user can submit a **real Solana mint address**, receive a report backed by *actually fetched* public-chain and market observations, open every supported source, see explicit uncertainty where data is missing, revisit the immutable report URL, and run passing automated tests. No mock result may be misrepresented as live.

---

**Repository:** https://github.com/0xSneaks/Vaporware-detective

**Roadmap:** Solana evidence engine → sandboxed website tests → social/repository research → history & developer profiles → additional chains.
