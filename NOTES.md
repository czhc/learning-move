# Notes
## Bookmarks

* [Sui Docs](https://docs.sui.io/)
* [Sui 101](https://docs.sui.io/guides/developer/sui-101)    
* [Docs: Embedding the Move Language](https://docs.solanalabs.com/proposals/embedding-move)
* [Move is Solana compatible](https://solana.com/news/solana-now-supports-libra-s-move-vm)
* [What's behind the Move movement](https://www.youtube.com/watch?v=2xJahzrjTRQ&list=PLilwLeBwGuK4H0t-tYR3C1KQFGmyZLNMG)
* [An introduction to MOVE](https://www.certik.com/resources/blog/3o4Cg1cjQH4IwA88aT8OwT-an-introduction-to-move)
* What gives Move built-in security? [An Introduction to Move](https://www.certik.com/resources/blog/3o4Cg1cjQH4IwA88aT8OwT-an-introduction-to-move) | [Formal Verification, the Move Language, and the Move Prover](https://www.certik.com/resources/blog/2wSOZ3mC55AB6CYol6Q2rP-formal-verification-the-move-language-and-the-move-prover)

## Dev Notes

1. Protocol upgrades: 

```
Network protocol version is ProtocolVersion(44), but the maximum supported version by the binary is 43. Please upgrade the binary. panic.file="crates/sui-protocol-config/src/lib.rs" panic.line=1252 panic.column=9
```

* Check latest network protocol version: https://github.com/MystenLabs/sui/releases
* Upgrade sui client: `brew upgrade sui`


2. Construct

* Package = Contract, has an address (case-insensitive). Package can also be a dep of another package.
* Account
* Object
* Transactions
    * Transactions specify a **Gas Object** / Coin used to pay for gas. Txns also specify a gas **Price** and **Budget** similar to ethereum txns. 
* Transaction Blocks: chain multiple commands in a single transaction


3. MOVE language unique properties

* In Move, each account that owns a token typically has a **piece of data stored in an account that directly represents the token**. This contrasts with the representation of tokens in Solidity, which is typically a single large “mapping” from accounts to the numbers of tokens they own.

* If a transaction involves two accounts that interact only with each other, that transaction can happen in parallel with other transactions. **Programmable resources** supports higher thruput
    * it possible to automatically verify that programs do not have certain kinds of errors: for example, that a resource is never silently dropped or duplicated

* Move also has built-in support for **formal verification** and intentionally excludes language constructs that tend to make formal verification difficult.

* Move supports **[generics](https://diem.github.io/move/generics.html)**
    * programming paradigm that allows types (such as data structures and functions) to be parameterized by other types. This enables writing code that can work with different types without sacrificing type safety or code duplication
    * Type-safety (is specified), but the type is a generic identity function `T`

* Move implements a Rust-like ownership system for values of **struct** types, where each value is owned by the variable or field that contains it
    *  References do not own any values to which they point. By default, struct values can only be moved to another owner. They cannot be copied or dropped.
    * Move has a typing feature called abilities that controls what actions are permissible for a value of a given type - Copy, Drop, Store, Key

* A **resource** is a struct that has only key and store abilities. Resources cannot be copied or dropped. This makes resources suitable for directly representing items of value such as coins

* A **reference** is a type of pointer that includes restrictions on how it can be used. When code creates a reference, the reference does not take ownership of the data. Instead, the code borrows the ability to read or write the data to avoid dangling references that can lead to vulnerabilities.
    * References to references are not allowed, and references cannot be stored in structs

* Move has only expressions, not statements. The left-hand side and right-hand side of an if expression must have the same types.

* In formal verification, a programmer writes specifications to mathematically express the desired behavior of the code. A tool checks the code meets the specs.  If the check succeeds, the tool could not find any situation under which the specification would be violated. 
    * But, there's always the possibility that the tool or the compiler contains a bug that could cause such a violation.
    * It may also fail to check complex code and requires specifications for smaller parts of the code to be added

* Solidity has SMTChecker tool for `requires` and `asserts`. Move formal verification  enables the specification of more complex properties. The Move development environment includes a checker called the **Move Prover**. The Move Prover uses  [Satisfiability Modulo Theory](https://en.wikipedia.org/wiki/Satisfiability_modulo_theories) to prove specifications

