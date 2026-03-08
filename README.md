# SIQ Trading Cards — Public Integrity Ledger

This repository serves as the public cryptographic anchor for the
SIQ Trading Cards verification platform.

Every verified trading session issued at siqtradingcards.com is
recorded in an immutable, append-only ledger. Daily Merkle root
hashes are committed to this repository as a permanent,
tamper-evident public record.

---

## What This Repository Contains

- Daily Merkle root commits anchoring all verified session records
- The SIQ public key for independent signature verification
- A running chain of ledger integrity proofs

---

## How Verification Works

1. Every trading session verified on the SIQ platform is assigned
   a unique Session ID (SID) — a BLAKE3 cryptographic hash of the
   canonical session payload.

2. Each session is signed with SIQ's ED25519 private key.
   The corresponding public key is published in this repository
   so anyone can independently verify that a session signature
   is genuine.

3. Every 24 hours, a Merkle tree is built from all session hashes
   recorded that day. The Merkle root is committed to this
   repository with a GPG-signed commit.

4. Anyone on earth can verify that no session record has ever
   been altered by checking the Merkle root chain in this
   repository against the session data returned by the
   SIQ verification API.

---

## SIQ Public Key

Used to verify ED25519 signatures on all session records.
Published in: /keys/siq_public_key.pub

---

## Ledger Structure

/anchors/YYYY/MM/DD.json   — Daily Merkle root and session count
/keys/siq_public_key.pub   — SIQ ED25519 public key

---

## Independent Verification

To independently verify any SIQ Trading Card session:

1. Retrieve session data from:
   https://siqtradingcards.com/verify/{SID}

2. The API response includes a proof object containing:
   - leaf_hash
   - merkle_root
   - merkle_path

3. Verify the ED25519 signature using the public key in this
   repository to confirm the session was signed by SIQ.

4. Confirm the merkle_root matches the corresponding daily
   commit in this repository.

If all three checks pass, the session is cryptographically
confirmed as genuine and unmodified.

---

## Trust Model

- Sessions are immutable once registered. No updates. No deletes.
- The signing private key has never touched a networked computer.
- Merkle root commits are GPG-signed by SIQ.
- This repository is the public source of truth for ledger integrity.

---

## Links

- Verification page: https://siqtradingcards.com/verify
- Main website: https://siqtradingcards.com
- Support: strikeiqalgos@gmail.com

---

*Screenshots fade. Trading Cards are forever.*
