# Automatic generation of imports

* Proposal: [SE-0011](0011-automatic-generation-of-imports.md)
* Authors: [Daniel Fernández Álvarez](https://github.com/DaniFdezAlvarez)
* Review Manager: [Guillermo Facundo Colunga](https://github.com/thewilly)
* Status: **Awaiting Review**

## Introduction
Up to now the compiler never generates imports. Would be nice if the compiler, by means of a flag, allow to fully generate imports for those java classes that are part of the std lib.

## Motivation

Even though is not compulsory for a POJO to include its package declaration the imports of the classes from the st lib that it uses are compulsory for it to compile. Therefore a flag for those users that want to automatically generate those imports would be an awesome feature.

## Proposed solution

Include a flag / configuration option that allow to dis/en-able this feature.
