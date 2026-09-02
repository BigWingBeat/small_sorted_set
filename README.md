# small_sorted_set

[![small_sorted_set crate](https://img.shields.io/crates/v/small_sorted_set.svg)](https://crates.io/crates/small_sorted_set)
[![small_sorted_set documentation](https://docs.rs/small_sorted_set/badge.svg)](https://docs.rs/small_sorted_set)

A [`SmallVec`](https://docs.rs/smallvec/latest/smallvec/struct.SmallVec.html)-backed, sorted vec, with no duplicate elements.

This is a type that is very comparable to a [`BTreeSet`](https://doc.rust-lang.org/stable/std/collections/btree_set/struct.BTreeSet.html), but is all stored in a single, contiguous vector, instead of being split across a tree of separately allocated nodes. This makes it simpler and more cache friendly, improving performance of construction, ser/de, and reads. The tradeoff is that mutations may be slower, by virtue of requiring larger copies and reallocations.

Additionally, being backed by a `SmallVec` rather than a std `Vec` allows it to be automatically inlined on the stack for small numbers of elements, significantly improving performance for small collections.

### MSRV

The minimum supported Rust version for this crate is `1.85`, due to using edition 2024.

## See Also
- [smallvec](https://crates.io/crates/smallvec) - The backing vector type.
- [sdset](https://crates.io/crates/sdset) - Fast set operations on sorted and deduplicated slices.
- [sorted-vec](https://crates.io/crates/sorted-vec) - Prior art. Backed by a std [`Vec`](https://doc.rust-lang.org/stable/std/vec/struct.Vec.html) instead of a `SmallVec`. (Psst: `sorted-vec2` is actually less maintained than `sorted-vec`, despite what it claims...)
