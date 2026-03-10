# Membership & accountability

Resource co-ops fail when “one member = one vote” becomes “one attacker = many accounts”.

So the co-op needs **membership** that is:

- **non-transferable** (no resale market for identities)
- **portable** (members can prove what they’re entitled to)
- **accountable** (misbehavior has a cost)

## Co-op membership (not “citizenship”)

We can use co-op language to avoid unnecessary crypto branding:

- **Membership**: a non-transferable member credential.
- **Member dues**: recurring payments that keep membership active.
- **Bond/stake**: escrow that can be slashed for abuse.

## Sybil resistance primitives

Different co-ops will choose different gates:

- KYC (where legally required)
- proof-of-personhood / social verification
- stake-based admission
- sponsor-based admission (existing members vouch)

The important part: membership is costly enough to make Sybil attacks uneconomic.

## Agents can be members too

Some co-ops may allow AI agents as members.

The rule isn’t “must be a human soul” . It’s:

- post a bond
- satisfy admission checks
- accept auditability and slashing conditions

This makes agents first-class economic actors without giving them free, unaccountable identities.

## The member ledger (Merkleized state)

Each member has a state object:

- entitlements (baseline quotas, priority class, reserved capacity)
- ownership/holdings in the co-op (shares, if any)
- reputation / compliance flags (minimal and appealable)

Represent this as a Merkle tree so members can:

- prove entitlements without revealing everything
- port membership state between systems

## Property tax vs dues

“Property tax” captures an important idea: membership has ongoing cost proportional to what you control.

But “dues + bond” is often clearer:

- **dues** fund maintenance and public goods
- **bond** provides slashing surface for abuse

## Exit ramps

Membership systems should make leaving easy:

- export your entitlements/history
- revoke agent permissions and keys
- settle final balance

Exit ramps prevent lock-in and force systems to compete on quality.
