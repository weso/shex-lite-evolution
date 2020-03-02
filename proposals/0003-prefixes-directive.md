# Directive: Prefix

* Proposal: [SE-0003](0003-prefix-directive.md)
* Authors: [Guillermo Facundo](https://github.com/thewillt)
* Review Manager: TBD
* Status: **Awaiting Review**

## Introduction

Shapes Expression language is based in turtle and therefore must be support for `PREFIX` declarations. A prefix declaration defines an IRI and associates it with a name that is used by the shapes definition to reference the IRI.

## Motivation

In order not to write the IRIs everytime we need them the `PREFIX` directive has been defined in turtle. This directive helps by allowing to associate an IRI to an alias. That way, anytime we need to reference the URI we can simply invoke the alias.

```shex-lite
PREFIX xsd : <http://scheema.org/>
PREFIX foaf : <http://foaf.org/>

<person> : {
  foaf:name xsd:string
}
```

This way `xsd = <http://scheema.org/>` and `foaf = <http://foaf.org/>`.

Also, notice that prefix definitions don't have to be compulsory above the shapes definitions. They can perfectly go mixed, and even redefine the same alias.

Example:
```shex-lite
PREFIX xsd : <http://scheema.org/>
PREFIX foaf : <http://foaf.org/>

<person> : {
  foaf:name xsd:string  // <http://foaf.org/name> <http://scheema.org/string>.
}

PREFIX foaf : <http://foaf2.org/> // Redefine alias `foaf`.
PREFIX weso : <http://weso.es/>   // Redefine aloas `weso`.

<person> : {
  foaf:name xsd:string ;  // <http://foaf2.org/name> <http://scheema.org/string>.
  weso:secret xsd:string  // <http://weso.es/secret> <http://scheema.org/string>.
}

```


## Detailed design

In order to implement this directive we need to:
* Add the rule to the parser.
* Add the corresponding AST node.
* Modify the identification visitor to process all the references.
* Modify the checking visitor to check if all references are good.

## Alternatives considered

No alternatieves have been considered.
