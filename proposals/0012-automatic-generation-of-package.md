# Automatic generation of package declaration for java generated POJO's

* Proposal: [SE-0012](0012-automatic-generation-of-package.md)
* Authors: [Daniel Fernández Álvarez](https://github.com/DaniFdezAlvarez)
* Review Manager: [Guillermo Facundo Colunga](https://github.com/thewilly)
* Status: **Awaiting Review**

## Introduction

Allow the compiler, by means of a flag, to automatically generate package declarations for java codegen.

## Proposed solution

Create a new flag in the compiler that allows to automatically generate the package declaration of each created POJO class.
