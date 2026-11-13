# Zend positioning: the money network for the internet

Status: draft for review. Lives in `zend-docs/drafts/` (ignored by the Mintlify build).

## The shift

Today Zend is presented as a payments app ("Send, receive, pay, split bills… it just works like magic!"), and the developer products are presented one at a time: a payments API (Pay with Zend), a CLI, an app toolkit (AppKit), and links (Zlinks) that don't have a public face.

We should present Zend as a **network**: a set of people, money and places that every app shares. The Zend app is the first app on the network, not the whole product. AppKit, Pay with Zend and money links are the ways to build on it.

Why this framing is true, not just aspirational:

- **One identity across every app.** A person's `appUserId` is the same in every ZApp, and their @name works everywhere.
- **Money behaves the same in every app.** A payment, ask link or money link made by a ZApp is the same object the Zend app makes, with the same screens and records.
- **Apps share the same surfaces.** Cards from any app appear in the same chats and Activity feed.
- **Anyone can join.** Any Zend account can create a ZApp in a minute. Private apps need no approval.
- **Zend doesn't hold the money.** Balances sit in each person's own account; money links sit in a contract until collected. Zend runs the rules and the screens.

## One line, per audience

| Audience | Line | Support |
|---|---|---|
| Everyone (keep the live site's line) | **Money for the internet.** | Everyone has an @name. Send to anyone in seconds, with no fees, even if they're not on Zend yet. |
| Developers | **Build on the money network for the internet.** | Every app gets people with @names, money that moves in seconds, and a place in the chats and feed people already use. |
| Partners / press | **Zend is a money network where every person has an @name and anyone can build apps that move money.** | Built for Nigeria first, priced in Naira. |

## Message house

Three layers. Every page, pitch and screen should map to one of them.

| Layer | What it is | Consumer copy | Developer copy | Proof in the product |
|---|---|---|---|---|
| **People** | @names and one Zend identity | "Just @theirname." | Sign in with Zend. One stable ID per person across every app. No sign-up screen to build. | `identity.get`, `verifySession`, people picker |
| **Money** | Send, ask, money links, splits, prizes | "Send to anyone in seconds. No fees." | Payments, ask links, money links, splits, prizes and spend allowances, priced in Naira. Zend draws every money screen. | `pay`, `request`, `createLink`, `splits`, `prize.*`, `allowance` |
| **Reach** | Chats, feed, Discover, and links that work anywhere | "Send it as a link. They don't need Zend yet." | Two ways to build: inside Zend (ZApps in chats, the feed and Discover) or anywhere (Pay with Zend links that open in the app or the web). | chat actions, cards, `/apps/<slug>`, `/i/<id>`, `zdfi.me` links |

Supporting proof points for developers:

1. **You never build a payment screen.** Zend shows its own confirm sheet, checks limits, and records the payment.
2. **Zend doesn't hold your users' money.** Money only moves when its owner confirms on their phone.
3. **Results anyone can check.** Random draws are recorded once on Sui; attestations are signed and chained.
4. **Free to start.** Users pay no fees. Zend covers the network cost of your links and prizes up to a monthly budget.

## Naming

| Thing | Public name | Notes |
|---|---|---|
| The company, network and app | **Zend** | Drop the "Zend!" exclamation in new copy or use it everywhere; today the site uses "Zend!" and everything else "Zend". Pick one. |
| Apps built on Zend | **ZApps** | Not "mini apps" (World's term). |
| Browser and server SDK | **AppKit** (`@zendfi/appkit`) | |
| API for any website or backend | **Pay with Zend** | Recommend moving `pay-with-zend-sdk` to `@zendfi/pay` so all packages share one scope. |
| Give links | **money links** | "Zlinks" is the internal name. Developer docs can say "money links (Zlinks)" once. |
| Requests to be paid | **ask links** | |
| CLI | **Zend CLI** (`zend`) | It now covers apps, not just payments. Recommend publishing as `@zendfi/cli` and keeping `pay-with-zend-cli` as an alias. |

## Words

Use: network, @name, your Zend, money link, ask link, collect, take back, build on Zend, ZApp, in seconds, priced in Naira.

Don't use in consumer copy: everything in the user-facing language rule (Sui, chain, crypto, token, wallet, gas, transaction, …).

Don't claim anywhere, because it isn't true yet:

- "Open protocol", "permissionless", "decentralized". Zend runs the APIs, the review and the limits.
- "AppKit works on any website". Outside Zend, AppKit calls fail with `NOT_IN_ZEND`. Pay with Zend is the way to reach other websites today.
- User or volume numbers we haven't published.
- "Instant". Say "in seconds".
- "Free for developers" without the network budget caveat.

## Surface by surface

### Developer docs (done in this change)

- Homepage leads with the network and the two ways to build.
- New pages: How the network works, Pay with Zend, Test on your phone, Build with AI, Grow your app.
- Money links page frames links as money that travels as a URL.

### AppKit and CLI packages (done in this change)

- AppKit README intro and `package.json` description use the network line.
- CLI `--help` and `package.json` description now say it builds on Zend, not only "Pay with Zend".

### Consumer site (`usezend-app`, proposed, not changed)

1. Keep the title "Money for the internet".
2. Hero subline: "Everyone has an @name. Send to anyone in seconds, with no fees, even if they're not on Zend yet."
3. Replace `CryptoRailsSection` ("Get paid in crypto and fiat, from any chain and any bank!"). It breaks the user-facing language rule, and crypto deposits are turned off (commit b81f24a). Suggested replacement, a "Built on Zend" section: "Games, splits and tournaments, right in your chats. Apps on Zend use your @name and your balance, and every payment is confirmed by you."
4. Add **Developers** to the nav and footer, linking to the docs.

### In the app (proposed)

- Discover header: "Apps on Zend".
- Settings → Developer: link to the docs and "Build on Zend".

### Launch post (outline)

1. Zend is a money network: @names, money in seconds, no fees.
2. Today we're opening it to builders: ZApps inside Zend, Pay with Zend anywhere.
3. What you don't have to build: sign-up, payment screens, payment security, a realtime server.
4. Coin Flip as the 10-minute demo, Accident as the flagship.
5. Free to start, limits by tier, link to docs.

## Lessons from World, applied

| World does | Lesson | Our action | Status |
|---|---|---|---|
| Homepage with one card per product | Make the parts of the network visible | Homepage cards for ZApps, Pay with Zend, money links, CLI | Done |
| GIFs of each native sheet, good/bad design videos | Show the screens Zend draws | Capture the confirm sheet, consent sheet and each card template | Needs captures from the app |
| QR code to open your app on a phone | Make the first run physical | "Test on your phone" page | Done (static steps; an interactive QR needs a custom component) |
| MCP tabs, `SKILL.md`, "Build with LLMs" | Developers build with AI now | "Build with AI" page with MCP setup and `llms.txt` | Done, once the docs domain is live |
| `create-mini-app`, templates, UI kit | Remove setup from the first hour | `npm create zapp` with page, `zapp.json` and webhook handler | Proposed |
| Growth playbook | Builders want users, not just APIs | "Grow your app" page built on Zend's real distribution (chat actions, cards, Discover, links) | Done |
| Developer story videos | Social proof | Showcase Accident and early ZApps once live | Later |
| Mixed voices, crypto in the API, marketing stats in docs | Don't copy | One voice; amounts in Naira; no third-party growth stats | Ongoing |

## Rollout

1. Docs, AppKit README, package descriptions (this change).
2. Decide on names: "Zend" vs "Zend!", `@zendfi/pay`, `@zendfi/cli`.
3. Consumer site: replace the crypto section, add Developers link.
4. Visuals for the docs from the app.
5. Starter package and showcase.
6. Launch post.
