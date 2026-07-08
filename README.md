# Futarchy-Gated Funding Pools for Open-Source Infrastructure on Avalanche

**A proposal for the Avalanche Foundation / ecosystem grants program**

---

## Problem

Current OSS funding mechanisms (committee grants and quadratic voting) fail to price in **whether infrastructure will actually be used**. Futarchy — using prediction markets instead of voting — has a working implementation in MetaDAO on Solana, but nothing equivalent exists on Avalanche.

This proposal: a **futarchy-based funding primitive for OSS infrastructure grants** on Avalanche, with mechanism design that explicitly corrects for the self-fulfilling-prophecy problem.

## Mechanism

**Spend-cap + futarchy-gated tranches**, modeled on Futard.io:

- **Default allowance** — small fixed draw per period, no market needed, keeps projects alive independent of market sentiment
- **Futarchy-gated approval** — anything above the allowance requires a conditional YES/NO market to approve
- **TWAP-confirmed unlock tranches** — follow-on funding unlocks in stages as usage KPIs (not price) sustain above thresholds over defined windows
- **Standing kill-switch** — contributors can raise a futarchy proposal to halt unlocks and reclaim the pool at any time

### Why this works

- Reflexivity is contained: only *growth* of funding is market-gated, not survival
- Usage-based metrics avoid volatile-asset noise
- TWAP windows prevent single-snapshot gaming
- Minimum liquidity floors, position caps, and bonded oracle reporting resist manipulation

## Milestones

| Phase | Timeline | Deliverable |
|-------|----------|-------------|
| 1. Spec + legal wrapper | Weeks 1-3 | Contract design, KPI schema, Grants BORG via MetaLeX |
| 2. Core contracts | Weeks 4-8 | ConditionalVaultFactory, TWAP module, testnet deploy |
| 3. Pilot round | Weeks 9-14 | Live round with 3-5 real OSS projects, public post-mortem |
| 4. Generalize | Weeks 15-20 | Reusable module for any Avalanche subnet/DAO |

## Differentiation

- First futarchy-based grant primitive on Avalanche
- Spend-cap + TWAP-unlock structure directly addresses futarchy's reflexivity weakness
- Builds on proven MetaDAO/Futard.io design, adapted for OSS usage metrics
