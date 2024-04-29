# Move Book

Learning notes from https://move-book.com/

This book is dedicated to Move, a smart contract language that captures the essence of safe programming with digital assets. Move is designed around the following values:

Secure by default: Insecure languages are a serious barrier both to accessible smart contract development and to mainstream adoption of digital assets. The first duty of a smart contract language is to prevent as many potential safety issues as possible (e.g. re-entrancy, missing access control checks, arithmetic overflow, ...) by construction. Any changes to Move should preserve or enhance its existing security guarantees.

Expressive by nature: Move must enable programmers to write any smart contract they can imagine. But we care as much about the way it feels to write Move as we do about what Move allows you to do - the language should be rich enough that the features needed for a task are available, and minimal enough that the choice is obvious. The Move toolchain should be a productivity enhancer and a thought partner.

Intuitive for all: Smart contracts are only one part of a useful application. Move should understand the broader context of its usage and design with both the smart contract developer and the application developer in mind. It should be easy for developers to learn how to read Move-managed state, build Move powered transactions, and write new Move code.

The core technical elements of Move are:

Safe, familiar, and flexible abstractions for digital assets via programmable objects.
A rich ability system (inspired by linear types) that gives programmers extreme control of how values are created, destroyed, stored, copied, and transferred.
A module system with strong encapsulation features to enable code reuse while maintaining this control.
Dynamic fields for creating hierarchical relationships between objects.
Programmable transaction blocks (PTBs) to enable atomic client-side composition of Move-powered APIs.
