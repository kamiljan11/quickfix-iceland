# QuickFix — Handyman Services, Reykjavík

[![Quality Gate](https://github.com/kamiljan11/quickfix-iceland/actions/workflows/quality.yml/badge.svg)](https://github.com/kamiljan11/quickfix-iceland/actions/workflows/quality.yml)

**Live:** [quickfix.is](https://quickfix.is) · **Status:** production · **Built & operated by** [Kamil Jan](https://kamiljan.com)

Brand + multilingual marketing site (EN / PL / IS) for a Reykjavík handyman service — service pages, before/after gallery, floating WhatsApp contact, deposit-saver landing page. Brand and full sales flow shipped in 72 hours.

## What this repository is

This is a **public reference repo, not the application** — there is no `package.json`, no
`src/`, nothing to `npm install` or run. The site's source is private (see
[Source](#source) below); what lives here is the documentation trail: what the product does,
why it's built the way it is, and how to tell if it's still alive. See
[`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the map and
[`docs/adr/0001-public-repo-is-a-reference-not-the-source.md`](docs/adr/0001-public-repo-is-a-reference-not-the-source.md)
for why the split exists.

## The live product

- Multilingual marketing site: English / Polish / Icelandic
- Service pages, before/after photo gallery
- Floating WhatsApp contact button (the actual conversion path — no contact form)
- Deposit-saver landing page

## Checking it's alive

No local run, so the only "test" that means anything here is the live site itself:

```bash
curl -I https://quickfix.is   # 200 = up
```

CI (`.github/workflows/quality.yml`) runs a secrets scan and Semgrep on this repo's own
content (docs, workflows) on every push/PR — there's no application code for it to lint,
typecheck or build, so those steps no-op by design (`if: hashFiles('package.json') != ''`).

## Source

Application source: [`homehug-services`](https://github.com/kamiljan11/homehug-services) — proprietary; access may be restricted. The product is live at [quickfix.is](https://quickfix.is).

## Licence

See [`LICENSE`](LICENSE) — proprietary, published for reference only.
