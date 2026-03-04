# Resource co-ops

A **resource co-op** is a member-governed utility that funds and manages shared capacity (energy, bandwidth, compute, messaging, etc.) using an explicit fairness rule.

The goal: make “normal life” feel stress-free while still pricing the behaviors that create real scarcity.

## The core pricing idea: charge for *above-mean* consumption

Within a given service area (the co-op’s customer set), measure usage over a rolling window (weekly/monthly):

- Let **μ** be the rolling mean consumption for a customer class.
- Let **uᵢ** be member *i*’s usage over the same window.

A simple rule:

- **Billᵢ = fixed_fee + rate · max(0, uᵢ − μ)**

Intuition:
- Below-mean members pay little beyond the fixed fee.
- Overuse pays, without needing a hard cap.

### Why “global mean” still works here

“Global” means **global within the local co-op**, not global across the planet.

Including large businesses in the same system is important, but you typically want **separate customer classes** (residential vs commercial/industrial) with their own μ, so industrial variance doesn’t distort “comfortable living” baselines.

## Scarcity is about peaks, not averages

Above-mean pricing is a fairness mechanism. Scarcity often shows up as **congestion** (peak demand, limited bandwidth, limited blockspace).

A real resource co-op must define a peak policy.

### Three peak policies (pick one, or combine)

1) **Time-of-use / surge pricing**
- Charge more during peak windows.
- Works when you can measure time slices.

2) **Quotas + priority classes**
- Baseline quota (per member or per household) and explicit priority lanes.
- Useful for critical needs (medical, safety, operations).

3) **Capacity markets (reservation)**
- Members reserve capacity ahead of time.
- Overages cost more.

## Storage/time-shift: when spikes are solvable

If the resource is storable, members can “bank” cheap-time capacity to handle expensive peaks:

- **Energy**: batteries, thermal storage.
- **Bandwidth**: caching/prefetching, delayed bulk transfers.
- **Messaging**: batching, queueing, delayed delivery.

But not everything is meaningfully storable (some latency-sensitive services), so the peak policy must be explicit.

## Metering & privacy

A co-op needs usage measurement, but not necessarily raw surveillance.

Practical approach:
- meters produce signed usage statements (per epoch)
- publish **only aggregated stats** and **commitments**
- members can prove correctness (selective disclosure / ZK, where needed)

## Examples

### Electricity co-op
- Class means: residential vs commercial vs industrial.
- Peak policy: time-of-use pricing + baseline quota.
- Storage: home batteries + community storage.

### XMTP messages / “messaging co-op”
- Resource: send/receive capacity + storage + anti-spam moderation costs.
- Peak policy: surge pricing for bursts + per-member quota.
- Storage: queueing/batching.

### Ethereum gas / “blockspace co-op”
- Resource: access to inclusion.
- Peak policy: reservation + surge (it already exists as fee market); the co-op layer can fund public goods and protect baseline access for members.

## What success looks like

- Baseline access is reliable and affordable.
- Overuse is priced, not moralized.
- Members can exit cleanly (export history, revoke permissions).
