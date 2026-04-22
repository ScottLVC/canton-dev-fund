# LongView Crew (LVC) — Non-Custodial Retail Interface for Canton Network

**Author:** Scott Long (longsw1984@gmail.com)
**Status:** Amendment to Submitted Proposal (v2.0)
**Original Submission:** 2026-04-13 (v1.0)
**Amendment Date:** 2026-04-22
**Amendment Rationale:** Significant product pivot, substantial shipped progress, updated funding ask to reflect expanded scope
**Label:** dapp-integration, retail-infrastructure, education
**Champion:** Seeking Champion

> **Note to grant reviewers:** This document amends our April 13, 2026 submission. The core project is the same — a community-facing Canton dApp by Scott Long / LongView Compute LLC — but the product has meaningfully evolved in the nine days since initial submission. Major pivots, completed milestones, and revised scope are explicitly flagged in the *What's Changed Since the April 13 Submission* section below. The core ask remains milestone-based funding to deliver a non-custodial retail dApp to MainNet; the updated ask reflects three new line items (senior engineer hire, third-party security review, and founder minimum-sustenance runway) detailed in the budget section.

---

## Summary

LongView Crew (LVC) is the first non-custodial retail dApp on Canton Network. It combines three integrated consumer products — **Canton Learn** (a structured onboarding curriculum), **Canton DeFi Toolkit** (non-custodial compose-sign-submit actions), and **LongView Crew** (a community layer with soulbound membership NFTs) — into a single front door for retail users arriving at Canton. These consumer products sit on top of a **multi-tenant issuer platform** that turns LVC into both a dApp and a piece of Canton's retail NFT infrastructure: any Canton-adjacent creator, NFT project, or community organization can apply to mint through LVC's production stack rather than building their own Daml contracts and compliance systems from scratch.

The pivotal insight driving LVC: Canton's institutional maturity (Super Validators, CIP-0103, Splice, CIP-0056 token standard) has finally opened the door to retail participation, but no retail-focused dApp has walked through it. Wallets like Bron, Nightly, and Ledger are shipping Canton support; WalletConnect went live on Canton in April 2026; the SEC's April 13, 2026 Covered User Interface Provider safe harbor clarified the compliance path. LVC is the first dApp built specifically for this moment.

The project has been built solo over roughly three weeks: ~1,100 files across a full-stack React + Spring Boot + Daml codebase; CIP-0103 wallet integration shipped; end-to-end compose-sign-submit verified on localnet; Canton Learn modules 1–5 complete; multi-tenant issuer platform live; SEC safe harbor compliance implemented throughout; SV whitelist quorum (11/14) achieved. DevNet deployment is scheduled for the week of this proposal.

This grant request funds production deployment to DevNet and MainNet, first team hire, ecosystem partnerships, and continued open-source contribution as Canton's reference retail dApp.

**Requested Funding:** 550,000 CC (~$84,034 at $0.15279/CC, milestone-based)
**Timeline:** 6 months (3 milestones)
**Change from v1.0:** +275,000 CC (v1.0 was 275,000 CC). Increase funds three new budget lines not present in v1.0: (1) senior engineer hire in M2 (~$31K), (2) third-party security review in M2 (~$8K), (3) founder minimum-sustenance runway at $5K/month through MainNet (~$30K). All three are de-risking line items, detailed in the budget section below.

---

## Problem Statement

Canton Network has world-class institutional infrastructure and is now — for the first time — accessible to retail users via CIP-0103, WalletConnect, and hardware wallet integrations. But retail has no place to land.

1. **No retail front door.** A new user who hears about Canton, opens a wallet, and holds some CC has no retail-focused application to *use* Canton for anything. Every existing Canton application is either infrastructure (validators, explorers, governance) or institutional (tokenized real-world assets, DvP settlement). Retail is addressed by no existing dApp.

2. **No systematic retail education.** Canton's documentation is excellent for developers and institutional integrators but overwhelming for a retail user. There is no structured curriculum that takes a newcomer from "what is Canton" to "I just transacted on Canton" in a coherent path.

3. **Compose-sign-submit pattern has no retail reference implementation.** CIP-0103 defines how retail wallets should interact with dApps, but no production retail dApp has yet demonstrated the full non-custodial flow (compose on dApp → sign in wallet → submit to validator → confirm on-chain) at scale. Developers learning Canton have no retail example to study.

4. **Non-custodial compliance story is unwritten.** The SEC's April 13 Covered User Interface Provider safe harbor created a clear path for non-custodial dApps, but no Canton retail dApp has yet implemented it end-to-end with documented compliance architecture. Regulators, lawyers, and subsequent developers have no reference.

5. **Featured App Right retail validation gap.** Canton's CIP-0078 Featured App Rewards program incentivizes apps that generate real transaction activity. Retail activity — small, frequent, diverse — is exactly what the reward structure is designed to encourage, but no retail dApp exists yet to demonstrate it.

6. **No retail NFT issuer platform on Canton.** Canton has institutional tokenization infrastructure (RWA, DvP, enterprise token standards) but nothing that lets a retail-scale creator, artist, NFT project, or community organization issue NFTs on Canton without building their own Daml contracts, compliance systems, and user interfaces. This is a category of infrastructure Canton doesn't have — and needs — to support a retail creator economy.

---

## What LongView Crew Is

Three integrated consumer products, plus a multi-tenant issuer platform:

### 1. Canton Learn — structured retail onboarding curriculum

A progressive, gated curriculum that takes a retail user from "what is Canton?" to "I can explain the mining round" to "I can submit a non-custodial transaction." Five modules are already live:

- **Module 1:** Canton 101 — what Canton is, how it differs, why it matters
- **Module 2:** Parties, validators, and participant nodes
- **Module 3:** The mining round mechanism
- **Module 4:** Canton vs. Ethereum vs. Solana — architectural trade-offs
- **Module 5:** Privacy and the synchronizer

Each module includes interactive content, comprehension checks, and a shipped badge on completion. Completion of the curriculum unlocks the Toolkit.

**Planned modules 6–8** (milestone 2): DeFi on Canton, Wallet security and hardware wallets, Taxes and compliance basics for US/EU users.

### 2. Canton DeFi Toolkit — non-custodial compose-sign-submit actions

The first retail implementation of the CIP-0103 compose-sign-submit pattern. Users compose transactions in the LVC UI, sign in their own wallet (Bron, Nightly, Ledger via WalletConnect), and submit through their own validator. LVC never custodies funds, never holds private keys, never submits on a user's behalf.

**Shipped actions:**
- **Transfer Composer** — send CC to another party with full preview + sign-on-wallet flow
- **Member Traffic Top-Up** — purchase validator traffic via compose-sign-submit
- **Transfer Preapproval** — set up 1-step deposit receiving
- **Canton DeFi Directory** — discover Canton DeFi protocols (Temple, OneSwap, Tradecraft) with deep-link CTAs

**Planned (milestones 2–3):** Delegation composer, DeFi protocol integrations, cross-wallet DvP using CIP-0056 token standard.

### 3. LongView Crew — community layer

Soulbound membership NFTs (founding crew, stream giveaways, learning milestones) and a badge system that rewards curriculum completion and on-chain activity. Builds compounding retention around real usage rather than speculative tokens — no LVC token exists or is planned.

---

### 4. LVC Issuer Platform — multi-tenant NFT infrastructure for Canton creators

A turnkey path for Canton creators, NFT projects, and community organizations to issue their own NFTs through LVC's production infrastructure. Rather than building separate Daml contracts, compliance systems, user interfaces, and audit infrastructure, issuers apply once and mint through the LVC stack.

**Why this matters for Canton:** Canton has excellent institutional tokenization infrastructure — RWA tokenization, DvP settlement, token standards for enterprise custody — but no retail-scale NFT issuer platform. An artist who wants to mint a 100-piece drop, a creator who wants membership passes, a community organization that wants event badges, or a small brand that wants on-chain collectibles currently has no Canton path. LVC fills that gap: apply through the platform, get reviewed, mint through LVC's shipped contracts, distribute through LVC's shipped UI.

**Shipped infrastructure (all live today):**
- **IssuerRegistration Daml template** — on-chain registration of approved issuers
- **Multi-tenant backend** — per-issuer authentication, per-issuer scoped data, full isolation between issuers (`IssuerController` + per-issuer auth layer)
- **Issuer application flow** — structured form with compliance fields (jurisdiction, legal entity, intended use case, content policy acknowledgment, audit contact)
- **Compliance layer** — Issuer Code of Conduct, platform-wide content policy, user-content policy
- **Full audit log** — every issuer action (application, approval, mint, metadata update) persisted with admin viewer
- **Per-issuer dashboards** — each issuer manages their own minting campaigns from their own dashboard
- **Application persistence** — applications and issuer records persist to disk, survive redeploys
- **Directory** — public-facing `/directory` route lists approved issuers for discovery

**Strategic significance:** This positions LVC as platform-not-just-app. The three consumer products (Learn, Toolkit, Community) are LVC's own dApps; the issuer platform is Canton infrastructure LVC operates on the ecosystem's behalf. It's a defensibility moat (takes months to replicate), a second revenue line (issuer subscriptions or mint-fee share, explored in M3), and a direct multiplier on Canton retail activity — every external issuer's mints become Canton transactions.

**Planned (milestones 2–3):**
- Onboard 3+ external issuers in Milestone 3 as proof-of-concept for the platform model
- Explore issuer revenue structure: small flat annual subscription OR per-mint fee share, aligned with Featured App Rewards rather than competing with them
- Issuer tier system based on compliance maturity (bronze / silver / gold) tied to audit history

---

## What's Already Shipped

This proposal is unusual in that a substantial portion of the work is already complete. The grant funds **deployment, scale, team, and ecosystem contribution** — not initial construction. Shipped work (~3 weeks, solo):

| Area | Shipped |
|---|---|
| **Wallet integration** | CIP-0103 dApp SDK + Discovery Component integrated; compose-sign-submit verified on localnet |
| **Smart contracts** | Daml packages for licensing, league scoring, soulbound membership NFTs, artistic NFTs |
| **Backend** | Spring Boot 3.4 + Java 21; 9 REST controllers; backend compose + submit endpoints; multi-tenant issuer architecture |
| **Frontend** | React 18 + Vite 6 + TypeScript; 16 views; wallet-first flow; mobile UX sweep complete |
| **Canton Learn** | Modules 1–5 live with badge award on completion |
| **Compliance** | SEC April 13 safe harbor implemented (12 conditions cataloged, ToS/methodology/disclaimer copy live, no CC reward claims user-facing) |
| **Badge + NFT system** | Soulbound NFTs, milestone badges, self-mint artistic NFTs with content policy |
| **Issuer platform** | Full multi-tenant infrastructure: IssuerRegistration Daml template, per-issuer auth, IssuerController, IssuerApplicationView, IssuerDashboard, public Directory, Code of Conduct, content policy, compliance audit log with admin viewer, application + issuer persistence |
| **Open-source infra** | README, LICENSE, CONTRIBUTING, SECURITY.md drafted |
| **Whitepaper** | v2.0 published reflecting non-custodial retail positioning |
| **Community** | ~20K YouTube subscribers, build-in-public on X, first SV whitelist quorum (11/14) achieved April 21, 2026 |

The DevNet deployment runbook is complete and deployment begins the week of this proposal.

---

## Technical Architecture

### Stack

| Layer | Technology |
|---|---|
| Frontend | React 18.3 + Vite 6.4 + TypeScript + Zustand |
| Backend | Spring Boot 3.4.2 + Java 21 + OpenAPI |
| Smart Contracts | Daml 3.4 (licensing, league, membership NFT, artistic NFT) |
| Wallet Layer | CIP-0103 dApp SDK + Discovery Component (supports Bron, Nightly, Loop, Zoro, Ledger via WalletConnect) |
| Ledger Communication | JSON Ledger API (Canton participant node) + PQS |
| Data | PostgreSQL 16 + Party Query Service for contract queries |
| Auth | Keycloak OAuth2 (DevNet/MainNet) + shared-secret (localnet) |
| Deployment | Docker Compose two-layer architecture (splice-node + app module), nginx reverse proxy |
| Observability | OpenTelemetry + Grafana (optional profile) |

### Codebase Metrics (as of April 22, 2026)

| Category | Count |
|---|---|
| TypeScript/TSX files | ~929 |
| Java backend files | ~60 |
| Daml source files | ~45 |
| Frontend views | 16 |
| REST API controllers | 11 |
| Docker services (devnet profile) | 17+ |
| **Total files in repo** | **~1,200** |

### Key Canton Integrations

- **CIP-0103 Discovery Component** — auto-discovers all compliant wallets; supports Bron, Nightly, Loop, Zoro, Reference Wallet, and any WalletConnect-enabled wallet including Ledger hardware.
- **CIP-0056 token standard** — scaffolded for allocation workflows; active integration planned in milestone 2.
- **Featured App Activity Markers** — wired in backend compose flow to mint markers on user-initiated transfers (subject to Tokenomics Committee approval on MainNet).
- **Splice-node validator integration** — devnet compose module connects to external splice-node validator via standard Canton ports.
- **Canton Scan API** — BFT reads from 2/3+ SV scan nodes for network-level data.

---

## What's Changed Since the April 13 Submission

The April 13, 2026 version of this proposal (v1.0, submitted) centered on a "Yield Maximizer" educational tool with a Stripe-funded Pro subscription. Two things changed immediately after submission:

1. **Canton's own CIP-0078 Featured App Rewards program became the right revenue model.** Charging retail users directly for yield tooling runs counter to the ecosystem's incentive structure. Earning CC via Featured App markers — for genuine user-initiated activity — is better aligned, keeps LVC free for end users, and channels revenue through Canton's own tokenomics.

2. **The compose-sign-submit pattern became the more important retail primitive.** A yield calculator doesn't need Canton. A non-custodial retail interface for *doing things on Canton* does. Shifting focus from passive yield education to active non-custodial transactions produced the Canton DeFi Toolkit, which demonstrates the pattern every subsequent retail dApp will need.

The current three-product structure (Learn + Toolkit + Community) plus multi-tenant issuer platform emerged from these two shifts. Canton Learn retains the educational mission of the original proposal but positions education as the onramp to action rather than the product itself.

### Tangible progress between v1.0 and v2.0 (9 days)

Beyond the positioning shift, the following was shipped between the April 13 submission and this April 22 amendment:

- CIP-0103 wallet connect integration completed and verified (phase 4.3)
- End-to-end compose-sign-submit flow shipped and verified on localnet (phase 4.4)
- Canton DeFi Toolkit shipped — Transfer Composer, Traffic Top-Up, Transfer Preapproval (phase 5)
- Canton Learn modules 4 and 5 added (Canton vs. other L1s, Privacy & synchronizer)
- Mobile UX sweep — the full frontend optimized for mobile
- SEC April 13, 2026 safe harbor compliance implemented (12 conditions cataloged and mapped to production architecture)
- Badge system + soulbound NFTs + artistic NFT self-mint shipped
- Multi-tenant issuer platform shipped with compliance audit log
- Whitepaper v2.0 published
- Homepage rewrite to reflect new positioning
- SV whitelist quorum achieved (11 of 14 SVs approved, April 21, 2026)
- DevNet deployment runbook completed; deployment begins week of April 22

This velocity is part of the amendment's thesis: the project is not speculating — it is shipping. The grant does not fund construction of an idea; it accelerates a working system into MainNet.

---

## Milestones

### Milestone 1: DevNet Deployment + Alpha Launch (Months 1–2)

**Deliverables:**
- Deploy LVC to Canton DevNet using the existing 2-layer compose architecture (splice-node validator + app module)
- Complete end-to-end verification of compose-sign-submit with three production wallets: Bron (via direct CIP-0103), Nightly (via direct CIP-0103), Ledger (via WalletConnect bridge)
- Onboard 100+ alpha users through a build-in-public campaign
- First Featured App Activity Markers created on live DevNet transactions
- Open-source the full codebase on GitHub under MIT license, with complete setup documentation and architecture diagrams
- Publish a developer walkthrough ("How to build a non-custodial retail dApp on Canton") as a Canton ecosystem reference
- Submit a first CIP based on retail dApp experience (likely: standardized retail wallet metadata extension to CIP-0103)

**Acceptance Criteria:**
- [ ] LVC accessible on DevNet at a public URL (candidate: `devnet.longviewcompute.com`)
- [ ] End-to-end non-custodial transaction verified with each of Bron, Nightly, Ledger (screenshots/video)
- [ ] GitHub repository public with MIT license, README, CONTRIBUTING, architecture.md
- [ ] 100+ unique wallet connections during alpha period (verifiable via PQS logs)
- [ ] Developer walkthrough published with at least 3 external developers having followed it successfully
- [ ] CIP submitted to canton-foundation/cips

**Funding:** 175,000 CC (~$26,738)

---

### Milestone 2: MainNet + First Team Hire + Canton Learn Expansion (Months 3–4)

**Deliverables:**
- MainNet deployment post-DevNet validation (subject to Super Validator IP whitelist approval for MainNet, which follows DevNet quorum)
- **First senior engineer hire** — mitigates solo-founder key-person risk and increases shipping velocity in parallel across frontend, backend, and Daml surfaces
- Direct WalletConnect integration (in addition to existing CIP-0103) for broader wallet coverage as WalletConnect's 700+ wallet ecosystem adds Canton
- Ledger Live native Canton flow end-to-end UX polish (sign-on-device verification UI, user-facing hardware wallet docs)
- Canton Learn modules 6–8: DeFi on Canton, wallet security and hardware wallets, US/EU tax basics for retail CC holders
- CIP-0056 token standard integration for DvP workflows (moves Transfer Composer to standardized allocation flow)
- Pilot partnership conversation with 1–2 Canton ecosystem players (target: Bron, Nightly, or an SV operating retail-adjacent infrastructure)
- Third-party security review of the LVC codebase (funded as a line item)

**Acceptance Criteria:**
- [ ] LVC live on Canton MainNet with working compose-sign-submit
- [ ] Featured App Activity Markers flowing on MainNet (subject to Tokenomics Committee approval)
- [ ] Senior engineer onboarded and shipped first production PR
- [ ] Modules 6–8 published and completion-gated
- [ ] CIP-0056 allocation flow live in Transfer Composer
- [ ] At least 1 partnership pilot agreement in writing (commercial, not equity)
- [ ] Third-party security review completed with no P0/P1 unresolved findings

**Funding:** 225,000 CC (~$34,378)

---

### Milestone 3: Scale + Ecosystem Contribution (Months 5–6)

**Deliverables:**
- 1,000+ monthly active users on MainNet
- Content layer: 10+ educational articles, 4+ YouTube videos, "Retail Canton Tax Guide" PDF for US/EU users
- Issuer platform onboarding of 3+ external issuers (NFT projects, community organizations, or creative collectives) through the existing multi-tenant infrastructure — each issuer runs through the full compliance flow (application, Code of Conduct acknowledgment, audit-tracked mints) and launches at least one NFT campaign via LVC
- Publish the first "Canton for Creators" launch guide — a walkthrough for external issuers on how to apply, mint, distribute, and comply with the LVC platform's content/conduct policies
- Explore and propose an issuer revenue structure (flat annual subscription, per-mint fee share, or tiered compliance model) in alignment with Canton Foundation's views
- 2+ additional CIPs submitted based on production retail dApp experience
- Formalized partnership with Canton Foundation or Digital Asset (target: Canton Learn becomes an officially-recommended retail onramp resource)
- Present LVC at a Canton Summit, community call, or equivalent ecosystem event
- Publish a "Retail Canton State of the Ecosystem" report synthesizing data from LVC's user base

**Acceptance Criteria:**
- [ ] 1,000+ unique active wallets within the measurement period (verifiable via PQS)
- [ ] 10+ published articles, 4+ videos, tax guide PDF
- [ ] 3+ issuer organizations onboarded and minting through LVC (each with completed application, signed Code of Conduct, and at least one live NFT campaign)
- [ ] "Canton for Creators" launch guide published
- [ ] Issuer revenue structure proposal drafted and shared with Canton Foundation
- [ ] 2+ CIPs submitted
- [ ] Canton Foundation / DA partnership in writing
- [ ] Public presentation delivered (recording or slides available)
- [ ] State of the Ecosystem report published

**Funding:** 150,000 CC (~$22,919)

---

## Budget Summary

| Milestone | Timeline | Funding (CC) | USD approx. | Primary Focus |
|---|---|---|---|---|
| M1: DevNet + Alpha + Open-Source | Months 1–2 | 175,000 | ~$26,738 | Deploy, wallet verification, open-source |
| M2: MainNet + Team + Modules 6–8 | Months 3–4 | 225,000 | ~$34,378 | Production scale, engineer hire, CIP-0056, security review |
| M3: Community + Partnerships + CIPs | Months 5–6 | 150,000 | ~$22,919 | User growth, content, ecosystem contribution, issuer onboarding |
| **Total** | **6 months** | **550,000 CC** | **~$84,034** | |

*CC → USD conversion at $0.15279/CC (Canton Scan spot price, April 22, 2026). Milestone-based disbursement — each tranche contingent on demonstrable completion of the corresponding acceptance criteria.*

**Change from v1.0 ask (275,000 CC at April 13 submission):** The v2.0 ask adds 275,000 CC. The increase funds three new budget lines not present in v1.0 — all three are de-risking measures, not scope expansion:

1. **Senior engineer hire (M2).** v1.0 did not budget for team. In the nine days since v1.0 was submitted, the solo-founder key-person risk has become the largest single risk to MainNet launch. Hiring a senior engineer with Daml literacy mitigates this risk and doubles shipping velocity across frontend, backend, and Daml surfaces. ~$31K of the increase.
2. **Third-party security review (M2).** v1.0 did not budget for external security review. Before MainNet, a third-party review of the compose-sign-submit pathway, wallet integration, and Daml contracts is a non-negotiable prerequisite for any compliance-conscious retail dApp. ~$8K of the increase.
3. **Founder minimum-sustenance runway through MainNet (6 months).** v1.0 assumed the founder could operate on nominal sustenance supplemented by future Stripe subscription revenue. With the pivot away from Stripe and with Featured App Rewards being post-MainNet revenue, there is no bridging revenue between now and the MainNet milestone. The founder has been operating full-time on LVC since before the April 13 submission, funded entirely out of personal disability income with a known expiration horizon; continued full-time commitment through MainNet requires grant-funded runway. Budgeted at $5,000/month for 6 months — this is a minimum-sustenance founder rate, materially below senior engineer market rate (~$15,000–20,000/month for comparable skill), structured as a founder discount in exchange for grant support during the critical pre-MainNet period. ~$30K of the increase.

### Use of funds (indicative, at 550K CC / ~$84K)

| Category | Allocation | Notes |
|---|---|---|
| Senior engineer salary (6 months, part-time → full-time ramp) | ~$31,000 | Hired in M2; key-person-risk mitigation |
| Founder minimum-sustenance runway (6 months × $5K/mo) | ~$30,000 | Below market (~$15–20K/mo for comparable senior engineer role); structured as founder discount |
| Third-party security review (M2) | ~$8,000 | Pre-MainNet gate; scope includes wallet integration, compose-sign-submit, Daml contracts |
| DevNet + MainNet infrastructure (validator droplet, scaling) | ~$6,000 | Ongoing operating cost |
| Content production (video, articles, tax guide) | ~$3,000 | M3 deliverables |
| Legal / compliance counsel retainer | ~$2,000 | SEC safe harbor + entity matters |
| Contingency / tooling / admin | ~$4,000 | Buffer for infra overruns, tax prep, business licenses |
| **Total** | **~$84,000** | |

---

## Team

**Scott Long** — Founder, LongView Compute LLC
- Solo developer and founder; built the existing ~1,200-file LVC codebase in approximately 3 weeks
- Full-stack engineer: React, Spring Boot / Java, Docker, Daml, Canton ecosystem tooling
- Active Canton Network participant since early-access period; familiar with Canton SDK, Splice, Canton Scan API, Party Query Service, cn-quickstart, CIP-0103 dApp SDK
- **YouTube:** [LongViewCompute](https://youtube.com/@LongViewCompute) — 20K+ subscribers with daily livestreams covering crypto investing and blockchain ecosystem analysis — built-in distribution channel for Canton community onboarding
- **X:** [@LongViewCrypto](https://x.com/LongViewCrypto) — Active presence engaging with the Canton and broader crypto community
- Proven ability to build and sustain an engaged audience — directly supports Milestone 3 community growth targets
- Contact: longsw1984@gmail.com
- Entity: LongView Compute LLC (US)

**Planned hire (Milestone 2):** Senior full-stack engineer with Daml literacy. Role covers backend, Daml, and DevOps while founder focuses on product, partnerships, and content. Hire mitigates the single-point-of-failure risk inherent in solo-founder operations and doubles shipping velocity.

---

## Why This Matters for Canton

1. **Retail front door.** Canton has infrastructure; LVC provides the application layer that lets retail users actually *use* that infrastructure. Every major L1 has a retail reference dApp (Uniswap on Ethereum, Phantom-integrated apps on Solana). Canton has none. LVC aims to be it.

2. **Compose-sign-submit reference implementation.** Every future retail dApp on Canton will need this pattern. LVC's open-source codebase demonstrates the full stack — from CIP-0103 wallet connection through Daml contract choice to PQS-backed confirmation — as a working, documented example.

3. **Wallet ecosystem validation.** LVC's compatibility with Bron, Nightly, and Ledger (the three major non-custodial retail options) validates Canton's multi-wallet story and exercises the entire integration stack including WalletConnect.

4. **Featured App Right at retail scale.** CIP-0078's reward structure is designed for genuine activity. Retail transactions — small, frequent, diverse — are a different profile than institutional DvP. LVC provides the real-world test of the reward structure at retail volume.

5. **Compliance architecture reference.** The SEC's April 13 safe harbor is only theoretically useful until someone implements it in production. LVC's architecture (non-custodial flow, SEC 12-condition mapping, on-chain audit log, no custody/no token) is the first full-stack implementation of the safe harbor and provides a template for subsequent US-regulated Canton dApps.

6. **Education pipeline.** Canton Learn systematically converts curious users into capable users. Retail growth on any L1 is bottlenecked on education; LVC provides the Canton-native curriculum.

7. **Retail NFT issuer infrastructure — a second platform Canton doesn't have.** Canton's NFT story today is institutional: RWA tokenization, DvP, enterprise custody. There is no turnkey retail-scale NFT minting platform for creators, artists, community organizations, or small brands on Canton. LVC's shipped multi-tenant issuer platform fills that gap. Every external issuer onboarded is a direct multiplier on Canton retail activity — their mints, distributions, and community drops all become Canton transactions. This is infrastructure the ecosystem needs regardless of LVC's consumer traction.

8. **Non-dilutive, community-aligned.** LVC has no token and no plans for one. There is no airdrop, no presale, no VC cap table. Value accrues to LongView Compute LLC (the operating entity) through Featured App Rewards, issuer platform revenue, and partnership revenue, and to users through genuine utility. This is the simplest possible legibility story for the Canton Foundation.

---

## Alignment with Fund Priorities

The proposal is written to qualify under both the **Canton Protocol Development Fund** and the **Canton Foundation ecosystem / community programs**. LVC hits multiple stated priority categories:

| Priority | LVC Alignment |
|---|---|
| **Developer tooling** | Open-source full-stack retail dApp reference implementation |
| **DeFi applications** | Canton DeFi Toolkit — first retail-usable composable actions |
| **Critical infrastructure** | Non-custodial compose-sign-submit pattern at production scale; multi-tenant NFT issuer platform for retail Canton creators |
| **Reference implementations** | Complete React + Spring Boot + Daml + CIP-0103 pattern |
| **Community / retail infrastructure** | First retail onramp with structured curriculum; first retail NFT issuer platform on Canton |
| **Education** | Canton Learn: 5 modules shipped, 3 more planned |
| **Compliance** | First production implementation of SEC April 2026 safe harbor |

---

## Risks and Mitigations

Honest disclosure:

1. **Solo-founder key-person risk.** The single biggest risk to this project is founder unavailability (health, burnout, or otherwise). Milestone 2 hires a senior engineer specifically to mitigate this. Until then, the codebase is open-source, well-documented, and can be continued by any capable team.

2. **Canton ecosystem trajectory risk.** LVC's revenue and user base depend on Canton's continued growth. If Canton stalls, LVC's value proposition contracts. Mitigated by: LongView Compute LLC is US-entity independent of Canton, the codebase can be adapted to other L1s, the educational content has value beyond a single chain.

3. **Featured App Rewards approval risk.** MainNet Featured App status requires Tokenomics Committee approval. If rejected or delayed, M2 revenue projection compresses. Mitigated by: LVC's partnership revenue (M2–M3) and bootstrapped runway do not require Featured App status to operate; rewards are a multiplier, not a foundation.

4. **Competitive displacement.** A well-funded team could build a similar retail dApp and out-ship LVC. Mitigated by: 3-week head start with working code, active Canton Foundation relationship, ecosystem goodwill from open-source contribution, and the moat of a shipped educational curriculum that takes months to replicate.

5. **Regulatory drift.** The SEC's April 2026 safe harbor is a policy position, not statute. It could change. Mitigated by: non-custodial architecture means LVC has no custody to misuse; any regulatory tightening would affect custodial competitors first. Legal retainer is budgeted.

---

## Process and Accountability

Each milestone disbursement is contingent on demonstrable acceptance-criteria completion, verifiable by the grant committee via:

- Public URLs (DevNet, MainNet, GitHub)
- PQS query results for user counts
- Published CIPs
- Public partnership announcements
- Community presentations (recorded / public slides)

Monthly progress reports will be published publicly (not just to the grant committee) as part of the build-in-public commitment that's already core to LVC's community model. The April 13 v1.0 proposal and this April 22 v2.0 proposal are both publicly versioned — no iteration happens in private.

---

## Relationship to the Submitted v1.0 Proposal

v1.0 (submitted April 13, 2026) anchored on a "Yield Maximizer" educational tool with a Stripe Pro subscription model. v2.0 replaces that framing with the current three-product, non-custodial retail structure plus multi-tenant issuer platform. The founder and the project entity (LongView Compute LLC) are unchanged. The deliverables differ in substance; the mission — make Canton accessible to retail — is unchanged.

We respectfully ask the grant committee to consider this v2.0 amendment in place of the v1.0 submission. If the committee prefers to evaluate v1.0 as submitted without this amendment, the founder will honor that decision; however, the v1.0 deliverables would need to be renegotiated since several are no longer part of the product roadmap (Yield Maximizer, Stripe Pro subscription). The intent of this amendment is to give the committee the most accurate and current picture of the project being funded.

v1.0 is preserved in git history at commit prior to 2026-04-22.

---

## Appendix: Recent Milestones (April 2026)

For reference, the work completed between the v1.0 proposal (April 13) and this v2.0 proposal (April 22):

- CIP-0103 wallet connect integration shipped (phase 4.3)
- Compose-sign-submit flow end-to-end verified on localnet (phase 4.4)
- Canton DeFi Toolkit shipped (phase 5) — Transfer Composer, Traffic Top-Up, Transfer Preapproval
- Multi-tenant issuer platform shipped (phase 2) — IssuerRegistration, compliance audit log, application flow
- Pivoted away from Yield Maximizer; removed Rewards page pending legal clearance
- Rewrote LVC whitepaper v2.0 for new positioning
- Rewrote HomeView + longviewcompute.com landing for new positioning
- Canton Learn modules 1–5 shipped
- Badge + artistic NFT campaigns shipped
- Mobile UX sweep
- SEC safe harbor compliance implementation
- SV whitelist quorum achieved — 11 of 14 SVs approved (April 21, 2026)
- DevNet deployment recon completed; deployment begins week of April 22

This velocity is part of the proposal's thesis: funding this team accelerates an already-shipping roadmap rather than initiating speculative work.
