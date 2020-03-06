# Node constraint types

* Proposal: [SE-0006](0006-node-constraint-types.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Awaiting Review**

## Introduction

Node constraints describe the allowed values of a node. These include
specification of RDF node kind, literal datatype, string and numeric facets,
and value sets.

## Motivation

One of the key points of validating rdf data is to validate the type of the
nodes. Therefore there is a need to represent the node type as a constraint.

## Proposed solution

The proposed solution is to use exactly the same node types as in the original
ShEx Language. This is from a high point of view. Then each type will be reduced
to the specific desired subset. For example the Value sets might be only
implemented to accept unit values.
