# Stellar & Soroban Collaborative Pair Programming Guidelines

## 1. Overview
This specification outlines the collaborative standards and verification protocols for peer programming across decentralized Stellar and Soroban smart contract development.

## 2. Core Tenets
1. **Checks-Effects-Interactions (CEI)**: Every contract state mutation must occur prior to invoking external transfer or token contracts to mitigate re-entrancy vectors.
2. **Arithmetic Invariant Defense**: Unchecked arithmetic operations (`+`, `-`, `*`) on user-controlled inputs are forbidden; explicit saturating (`saturating_add`, `saturating_sub`) or checked operations must be utilized.
3. **Idempotency Guard**: All transactional operations must derive and enforce unique, deterministic operation identifiers (`op_id`).
4. **Dual Peer Review**: Every pull request must be co-authored, peer-reviewed, and verified against full automated test suites prior to merge.

## 3. Verification Matrix
- All test suites must execute with 100% green exit codes.
- Type integrity (`tsc`, `cargo check`) must complete with zero errors.
- Strict linter passes (`clippy`, `eslint`) must show zero blocking warnings.
