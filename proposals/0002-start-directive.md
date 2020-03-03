# Directive: Start Shape Expression

* Proposal: [SE-0002](0002-start-directive.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: [Guillermo Facundo](https://github.com/thewilly)
* Status: **Accepted**

## Introduction

The shape expression might be selected by label or it might default
to a special shape called the start shape. A schema can have one more shape
expression called the start expression. This serves as start here advice from
the schema author and is useful when describing a graph with a single purpose.

It is not mandatory to specify a start expression. Additionally, only one start expression can be specified at most. If more than one start expressions are present an error should be returned.

## Motivation

Consider the following code:
```shex-lite
start = @<Patient>

<Patient> {
  ...
}
```
In the compact syntax, the directive start = @<Patient> declares that the shape expression <Patient> will be used by default if a shape is not explicitly provided in the shapes map.

In shape maps, it is possible to declare that a node must be validated against the shape map by using the keyword START. For example, the following shape map:
```shex-lite
:alice@START,
:bob@<Doctor>
```
would validate :alice against the start shape expression (in the previous example, it would be <Patient>) and :bob against <Doctor>.

## Detailed design

* Add parser rule.
* Add AST node.
* Modify identification visitor to support the expected behaviour of the directive.
* Modify the checking visitor to check that the start shape reference is declared.
