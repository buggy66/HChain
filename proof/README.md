# Board digests

One file per published trading day. Each holds the SHA-256 of the board file as it
was served that day, plus the hash of the day before it -- a chain.

```
sha256sum <(curl -s https://option.42069.me/data/board/<date>.json)
```

Compare with the `sha256` line in `proof/<date>.txt`. If they differ, the published
board is not the one this repository committed.

The chain is also served as `https://option.42069.me/data/proof.json`, and
`python scripts/proof.py` verifies a local build against it.

Chain head: `d6c6a74e919453e843c36a773093b3c551ba35c391da86818f4262ab3615fd1f`
Anchor repository: https://github.com/buggy66/HChain

*Why this exists:* a backfilled track record is the most valuable thing a copycat
can produce, and the cheapest way to produce it is to edit old numbers. Editing one
breaks every hash after it, and the commits here are the timestamps that make the
edit visible.
