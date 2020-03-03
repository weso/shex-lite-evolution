# Directive: import

* Proposal: [SE-0005](0005-import-directive.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Awaiting Review**

## Introduction

Implement a directive `IMPORT + shapel_file.shexl` that allows to import
and use another shex-lite file in the current workspace. There may be a minimum of 0 and an undefined maximum of imports.

## Motivation

Sometimes you need to write shape expressions in different files in order to
keep you files clean and not to end with a very long file. But at the same time
there is the need to use those already-implemented shapes in other files.
For that reason we need the `IMPORT` directive.

## Proposed solution

Implement in the parser a new `IMPORT + shapel_file.shexl` rule. Next we will
have to modify the checking visitor to ensure that the file is imported
correctly and check that there are no inconsistencies between what imports
define and what defines the current file.

## Detailed design

A proposed design could be the loading algorithm of a single import. In this
way we would first check that the file exists, then the content of the file
would be loaded into the AST. Subsequently, the content of the current document
would be loaded into the AST. And finally the corresponding visitors would be
passed to the entire tree.

## Alternatives considered

The non-implementation of the directive.
