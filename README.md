# Reel - Privacy-Preserving Dark Pool DEX

A multi-layer privacy trading platform on Solana combining **Arcium MPC** encrypted orderbooks, **MagicBlock TEE**-protected sessions, and **Starpay ZK Swap** payments.

**Built for Solana Privacy Hack 2026**

## Features

- **Encrypted Orderbook** - Orders are encrypted using Arcium MPC. Price and quantity remain hidden until matched.
- **TEE-Protected Sessions** - Trade in Intel TDX secure enclaves with sub-50ms execution using MagicBlock Private Ephemeral Rollups.
- **ZK Swap Deposits** - Break the on-chain link between your wallet and trading activity with privacy-preserving deposits via Starpay.
- **Front-Running Protection** - Hidden orders prevent MEV and front-running attacks.
- **Compliance-Ready** - Audit trails via Intel TDX attestation for institutional use.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     PRIVACY LAYERS                          │
├─────────────────────────────────────────────────────────────┤
│  Layer 1: MagicBlock TEE (Private Ephemeral Rollups)       │
│  - State delegation to Intel TDX secure enclave            │
│  - Sub-50ms execution latency                              │
├─────────────────────────────────────────────────────────────┤
│  Layer 2: Arcium MPC (Encrypted Orderbook)                 │
│  - Orders encrypted before submission                       │
│  - Matching in encrypted space                             │
├─────────────────────────────────────────────────────────────┤
│  Layer 3: Starpay (ZK Swap Payments)                       │
│  - Anonymous deposits via ZK proof                          │
│  - Privacy-preserving withdrawals                          │
└─────────────────────────────────────────────────────────────┘
```

## Quick Start

### Prerequisites

- Node.js 18+
- Rust 1.75+
- Solana CLI 2.0+
- Anchor CLI 0.31+

### Installation

```shell
# Install dependencies
pnpm install

# Build Anchor program
pnpm anchor-build

# Start development server
pnpm dev
```

### Running Tests

```shell
# Run Anchor tests
pnpm anchor-test
```

## Sponsor Integrations

### Arcium - Encrypted Compute ($10k Bounty)

MPC circuits for encrypted orderbook operations:

- `init_orderbook` - Initialize encrypted order book
- `place_encrypted_order` - Place order with hidden price/quantity
- `match_and_execute_order` - Match in encrypted space
- `cancel_encrypted_order` - Cancel without revealing details

### MagicBlock - Private Ephemeral Rollups ($5k Bounty)

TEE-protected trading sessions:

- `delegate_trading_session` - Start private session
- `commit_trading_session` - Checkpoint to base layer
- `end_trading_session` - Finalize and undelegate

### Starpay - ZK Swap Payments ($3.5k Bounty)

Anonymous fund flows:

- `request_zk_swap_deposit` - Anonymous deposit
- `request_zk_swap_withdrawal` - Private withdrawal
- Card issuance for fiat spending (future)

## Project Structure

```
Reel/
├── anchor/
│   ├── programs/hybrid-dex/    # Main Solana program
│   │   ├── delegation.rs       # MagicBlock TEE integration
│   │   ├── starpay.rs          # Starpay ZK Swap integration
│   │   └── lib.rs              # Core trading logic + Arcium
│   └── encrypted-ixs/          # Arcium MPC circuits
├── src/
│   ├── components/
│   │   ├── magicblock/         # TEE session components
│   │   ├── starpay/            # Payment components
│   │   └── trading/            # Trading UI components
│   └── app/trade/              # Main trading page
└── bounty.md                   # Full bounty submission
```

## Commands

| Command                                        | Description              |
| ---------------------------------------------- | ------------------------ |
| `pnpm dev`                                     | Start development server |
| `pnpm build`                                   | Build for production     |
| `pnpm anchor-build`                            | Build Anchor program     |
| `pnpm anchor-test`                             | Run Anchor tests         |
| `pnpm anchor deploy --provider.cluster devnet` | Deploy to devnet         |

## License

MIT

---

_Privacy is necessary for an open society._
# reel
