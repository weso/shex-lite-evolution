# Inline Shape Expression Definition

* Proposal: [SE-0007](0007-inline-shape-definition.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: [Guillermo Facundo](https://github.com/thewilly)
* Status: **Implemented**
* Implementation: [weso/shex-lite#80](https://github.com/weso/shex-lite/pull/80)

## Introduction

In te original ShEx Language exists the possibility to define an inline
shape expression like `:Person xsd:String` that is a Node Constraint. It
means that nodes must be of type String.

## Motivation

Sometimes we dont need to build a complex shape expression, we just want
to validate that a node has an specific type. For that propose in the
original ShEx language we have the inline shape definition, that is
defined as `shape_alias node_constraint cardinality`.

## Proposed solution

Add the corresponding rule to the parser, and add it to the AST where
it will be processed as a normal shape expression definition.

## Detailed design

In the shape definition rule add the regular expression
`shape_alias node_constraint cardinality`.

## Alternatives considered

Ban the use of inline shapes definition.
