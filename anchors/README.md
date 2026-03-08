# Anchors

This folder contains daily Merkle root anchor files.

Each file is named by date: YYYY/MM/DD.json

Each file contains:
- merkle_root: The root hash of all sessions verified that day
- session_count: Number of sessions included in the tree
- timestamp: UTC timestamp of when the anchor was generated
- signed_by: SIQ ED25519 public key fingerprint

These files are committed daily by the SIQ signing server.
Each commit is GPG-signed by SIQ Trading Cards.

The chain of Merkle roots in this folder forms an unbreakable
record of every trading session ever verified on the platform.
