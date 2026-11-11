# Zend developer docs

Mintlify site for building ZApps with `@zendfi/appkit` and the `zend` CLI.

## Preview locally

```bash
npm i -g mint
mint dev
```

Open http://localhost:3000.

## Check before pushing

```bash
mint validate
mint broken-links
```

## Publishing

Install the Mintlify GitHub app from the [dashboard](https://dashboard.mintlify.com/settings/organization/github-app). Pushes to the default branch deploy automatically.

## Where content comes from

| Section | Source |
|---|---|
| Guides, Money, Fair results, SDK reference | `zend-appkit` (`src/`, `docs/`) and the Zend backend |
| CLI | `zend-cli` (`src/commands/`) |

See `AGENTS.md` for terminology and style.
