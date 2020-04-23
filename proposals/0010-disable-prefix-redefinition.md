# Disable prefix redefinition

* Proposal: [SE-0010](0010-disable-prefix-redefinition.md)
* Authors: [Guillermo Facundo Colunga](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Implemented**
* Implementation: [weso/shex-lite#80](https://github.com/weso/shex-lite/pull/80)

## Introduction

When semantically validating the prefixes declarations and references in a shex-lite source file we have two options:

### First option
Allow prefix redefinitions, but this way a prefix must be always declared before its reference appears, that means that for example this `.shexl` file will fail.
```shexl
:User .     # The ':' prefix is not defined.

prefix :<s>
```
But with this approach we can redefine a prefix and use it with different URIs, for example:
```shexl
prefix a: <a>

a:User .		# Resolves to <a#User>

prefix a: <b>

a:User .		# Resolves to <b#User>
```


### Second option
Disable prefix redefinitions and allow prefix declarations anywhere in the source file. This approach helps to avoid errors but when a prefix redefinition is found needs to throw an error/warning because only the last declaration is the one that will be used.

For example the next source file will compile.
```shexl
:User .     # Resolves to <s#User>.

prefix :<s>
```
But this source will generate an error and therefore wont compile.
```shexl
prefix a: <a>

a:User .		# Resolves to <a#User>

prefix a: <b>   # ERROR (prefix redefinition not allowed).

a:User .		
```

## Comments
After the meeting held by the core team, it is decided that for now the policy to be applied will be as follows:

To maintain the integrity of the language, no re-definition will be allowed. At least for the moment. In this way, when a redefinition is found, the user will be informed that he is performing an action not allowed by means of an error.

Likewise, and in order not to conflict with prefixes defined in other source files that are related by means of the import directive, it is agreed that each prefix is ​​identified atomically by the name of its source file, its line and its column.
