# Triple Expression Definition Parser Rule

* Proposal: [SE-0008](0008-triple-expression-definition-parser-rule.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Rejected**

## Introduction

A shape expression (not inline one) is defined as the `shape_lbl` and a
`triple_expr`. Therefore is the triple expression the one that needs to
define the constraints. This proposal tries to define the parse rule for the
shape expressions.

## Motivation

We're defining the core and base of the language. The triple expressions are
the core of a shape expression and that implies that they are the core of
validation too. In order to implement them correctly we must define a nice
parser rule that allows the right expresivity to group all the posibilities
included in a triple expression.

## Proposed solution

Notice the following antlr rule:
```antlr
triple_expr
 : ex1=triple_expr op=(AND|OR) ex2=triple_expr
 | NOT triple_epr
 | shape_inv
 | '{' triple_constraint* '}'
```

## Alternatives considered

No alternatives have been considered. Open to any suggestion.
