# Cryptographic timestamps

This repository exists so that each poem, and the source it is traced to, can be shown to have existed when it did. Three independent dates back that up:

1. **The push.** GitHub records when each commit reached this public repository.
2. **OpenTimestamps.** Every protocol, prediction and ledger file carries a `<name>.md.ots` proof beside
   it, which commits the file's SHA-256 to the Bitcoin blockchain. Anyone can check it without trusting
   this repository, GitHub or the author.
3. **RFC 3161.** A weekly manifest of every tracked file is signed by three independent trust
   authorities, one of them eIDAS-qualified. See [`timestamps/README.md`](./timestamps/README.md).

## One file, one stamp

`ots stamp` overwrites an existing proof, so a revised file first has its earlier proof renamed to
`<file>.rN.ots` by hand, keeping the evidence of what the earlier version said, and the revision is logged below.
The weekly job adds a proof to any document that has none and never touches an existing one. A
new document is stamped by hand when it is pushed, not left to the weekly job.

## What a proof does not show

A timestamp proves that this exact text existed no later than a given moment and has not changed
since. It says nothing about who wrote it, whether it is original, or whether it is right.

## Checking a proof

```sh
pip install opentimestamps-client
ots verify <file>.md.ots
./tsa-verify.sh <file>.md
```

A full check against Bitcoin uses a local node. Without one, the proof still names a specific block,
whose Merkle root can be compared with any public block explorer.

## Log

*Stamps, rotations and checks are recorded here, newest first.*

### 2026-10-21 — design record stamped

`DESIGN.md` was added and stamped (`DESIGN.md.ots`, calendar attestations only until the weekly upgrade). The README
was reworded in the same commit (the promise changed from life and work to meditation and citation); it carries no
proof of its own, so no earlier proof was rotated.

### 2026-10-15 — repository created

The timestamping is in place before the first document.
