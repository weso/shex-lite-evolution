# Make the `AND` keyword compulsory

* Proposal: [SE-0009](0009-compulsory-and-keyword.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Awaiting Review**
* Implementation: [shex-lite/shex-lite-2.0-dev#19@8b0aaab](https://github.com/weso/shex-lite/pull/19/commits/8b0aaabba4fcca194cd30baa31a5ef7999a73a0a)

## Introduction

By default the `AND` keyword is optional but this adds lots of ambiguity to the grammar. If we make it compulsory to use we're still in the subset of ShEx but reducing ambiguity.

## Motivation

We test both options againts the ANTLR profiler. When allowing AND not to be pressent we had a red warning about our grammar being ambiguos and a parse of almost 4 ms with a k of 100+. On the other hand if the AND keyword is mandatory the parse time is 0.9 ms and the k value lows to 21 with no ambiguity warning.

## Proposed solution

Make the `AND` keyword compulsory.
