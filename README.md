# ScholarSphere – On-chain Student Identity & Registration

ScholarSphere is a sample implementation we've experimented with alongside the Medici on-chain program (see other GitHub repo). It allows users to create, verify and publish their scholarship profiles directly on-chain. Built with React and Anchor, it connects wallet-authenticated students to a decentralized profile system used by the Medici donor network.

---

## Features

- Submit student profiles via connected Solana wallet  
- Verified identity backed by on-chain metadata  
- On-chain account creation via Anchor PDA  
- Smart contracts written in Rust / Anchor framework  
- Modular React UI with form flow for profile setup

---

## Smart contract overview

ScholarSphere includes a minimal Solana program that:

- Initializes a **StudentAccount PDA** tied to a wallet
- Stores public metadata (name, bio, funding amount)
- Validates signer and prevents duplicate account creation
- Is extendable for on-chain edits, attestations and milestones

### On-chain layout

```
programs/scholarsphere/
├── src/
│   ├── lib.rs                     # Anchor program entrypoint
│   ├── instructions/
│   │   └── initialize_student.rs  # Account creation logic
│   ├── state/
│   │   └── student_account.rs     # Account struct + space calc
│   ├── seeds.rs                   # PDA seeds
│   └── types.rs                   # Canonical profile types
```

Built using [Anchor](https://book.anchor-lang.com/) for safety, ergonomics and easy CPI expansion.

---

## App structure (React front-end)

```
src/
├── components/     # Form inputs, student dashboard UI
├── pages/          # Register and profile views
├── hooks/          # useWallet, useForm
├── solana/         # Smart contract client helpers
├── context/        # Session state
├── styles/         # Tailwind config
```

---

## Running locally

```bash
# install dependencies
pnpm install

# start React dev server
pnpm dev

# optionally build Solana program locally
anchor build
```

You'll need `solana-cli`, `anchor-cli` and a funded devnet wallet to fully test the on-chain interactions.

---
