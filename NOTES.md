# Notes
## Bookmarks

* [Sui Docs](https://docs.sui.io/)
* [Docs: Embedding the Move Language](https://docs.solanalabs.com/proposals/embedding-move)
* [Move is Solana compatible](https://solana.com/news/solana-now-supports-libra-s-move-vm)
* [What's behind the Move movement](https://www.youtube.com/watch?v=2xJahzrjTRQ&list=PLilwLeBwGuK4H0t-tYR3C1KQFGmyZLNMG)


## Dev Notes

1. Protocol upgrades: 

```
Network protocol version is ProtocolVersion(44), but the maximum supported version by the binary is 43. Please upgrade the binary. panic.file="crates/sui-protocol-config/src/lib.rs" panic.line=1252 panic.column=9
```

* Check latest network protocol version: https://github.com/MystenLabs/sui/releases
* Upgrade sui client: `brew upgrade sui`


2. Nomenclature

* Package
* Object
* Transactions