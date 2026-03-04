# Sybil resistance

## The problem
If one person can cheaply appear as many, then “one member = one vote” (and quadratic mechanisms) collapse.

Sybil resistance is the craft of making membership/voice **costly to fake at scale** without demanding invasive identity.

## The goal
A good system should be:

- **Inclusive:** doesn’t require government ID by default
- **Private:** proves *enough* (uniqueness / eligibility), not everything
- **Composable:** different co-ops/DAOs can choose different gates
- **Economically robust:** attacks become uneconomic, not “impossible”

## Practical toolbox (mix-and-match)

- **Admission rules:** sponsor/vouching, stake/bond, rate limits, probation periods
- **Proofs of participation:** attestations from real activity (work, tenure, contributions)
- **Composite scores:** multiple weak signals combined beat any single oracle
- **ZK / selective disclosure:** prove claims without doxxing

## Why it matters for Luminism
Luminism leans on co-ops and participatory governance.

Without Sybil resistance:
- voting becomes pay-to-attack
- subsidy programs get farmed
- “fair pricing” turns into “many fake accounts”

With it:
- quadratic voting/funding becomes usable
- co-op membership stays credible
- baseline access programs can be enforced without surveillance

## Design note
Treat Sybil resistance like security engineering: layered defenses, clear threat models, and simple failure modes.

(See also: **Co-op Primitives → Membership & Accountability** for the “membership + dues/bond” framing.)
