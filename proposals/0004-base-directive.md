# Directive: Base

* Proposal: [SE-0004](0004-base-directive.md)
* Authors: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: [Guillermo Facundo](https://github.com/thewilly)
* Status: **Awaiting Implementation**

## Introduction

Base directive is the default prefix for relative IRIs. `BASE <http://example.org>` defines that every relative IRI defined in the document will be an extension of `example.org`. If no base directive is defined the default one will be used. Also multiple base directives can be used. In that case the last one used from top to down is the one used to resolve the IRI.

```shex-lite
BASE <http://default.org>
...

<person> {  // <http://default.org/person>.
  :name .
}

// Changes the base directive.
BASE <http://default-new.org>

<car> {  // <http://default-new.org/car>.
  :badge .
}

```

## Proposed solution

The solution proposed is based in the same implementation used in the full ShEx-S implementation where we introduce the rule in the parser and then in the checking visitor we use a variable that is overriden each time a base definition id found to solve the base references found.

## Alternatives considered

* Do not allow to override the base declarations.
* Remove base declarations and therefore relative IRIs.
