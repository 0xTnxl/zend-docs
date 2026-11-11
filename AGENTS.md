> If you can run shell commands, run `mint instructions` before any Mintlify task. If `mint` is not installed, run `npx mint@latest instructions`.

# Zend developer docs

## About this project
- Mintlify site for developers building on Zend. Pages are MDX with YAML frontmatter; config is `docs.json`.
- Sources of truth:
  - ZApp SDK (`@zendfi/appkit`): the `zend-appkit` repo, `src/index.ts`, `src/server.ts` and `docs/`.
  - CLI (`pay-with-zend-cli`, command `zend`): the `zend-cli` repo, `src/commands/`.
  - API behaviour: the Zend backend (`src/app_*.rs`, `src/app_manifest.rs`, routes in `src/main.rs`).
- When the SDK or CLI changes, update the matching page here in the same change.

## Layout
- `index`, `quickstart`, `concepts`: get started.
- `guides/`: building a ZApp (manifest, identity, interactions, cards, live rooms, picker, screen).
- `money/`: pay, links, splits, allowance, prizes, verifying payments.
- `fairness/`: random draws and attestations.
- `ship/`: public apps, limits, copy guide.
- `reference/`: client SDK, server SDK, REST API, webhooks, errors.
- `cli/`: one page per command group.

## Terminology
- "ZApp" for an app built on Zend. "Zend" for the product, never "ZendFi" in reader-facing text.
- "money link" (not escrow link or give link), "ask link" for `request`, "collect" (not claim), "take back" (not reclaim).
- "app key" for `zapp_sk_...`; "API key" for account keys from `zend keys` (`zdev_live_...`).
- `appUserId` / `app_user_id` (`zu_...`) for the per-user id apps see.
- Package names: `@zendfi/appkit` and `@zendfi/appkit/server`; CLI package `pay-with-zend-cli`, command `zend`.

## Style preferences
- Active voice, second person ("you"), one idea per sentence.
- Sentence case for headings.
- Bold for UI elements: tap **Approve**.
- Code formatting for file names, commands, paths, fields and error codes.
- These docs are for developers, so technical terms are fine. Copy that we tell developers to show their users must follow `ship/copy-guide.mdx`.

## Content boundaries
- Don't document endpoints the Zend client calls on the page's behalf (`/apps/by-slug/*`, `/apps/cards`, …) beyond listing them as internal.
- Don't document admin review endpoints or internal environment settings.
