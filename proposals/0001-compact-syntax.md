# Use compact syntax as base syntax

* Proposal: [SE-0001](0001-compact-syntax.md)
* Author: [Guillermo Facundo](https://github.com/thewilly)
* Review Manager: TBD
* Status: **Awaiting Review**

## Introduction

Shape Expressions can be expressed in multiple syntax, JSON-LD, RDF and compact one (turtle). Compact syntax provides a human-friendly form.

## Motivation

The following example shows perfectly how the compact syntax is more human-friendly than others like JSON-LD:

```shex-lite
PREFIX dc: <http://purl.org/dc/terms/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
BASE <http://a.example/schema>

<#book> {
  dc:title xsd:string ;
  dc:creator @<#person>+ ;
}

<#person> {
  foaf:name xsd:string+ ;
  foaf:homepage IRI?
}
```

```json-ld
{
  "type": "Schema",
  "@context": "http://www.w3.org/ns/shex.jsonld",
  "shapes": [
    {
      "type": "Shape",
      "id": "http://a.example/schema#book",
      "expression": {
        "type": "EachOf",
        "expressions": [
          {
            "type": "TripleConstraint",
            "predicate": "http://purl.org/dc/terms/title",
            "valueExpr": {
              "type": "NodeConstraint",
              "datatype": "http://www.w3.org/2001/XMLSchema#string"
            }
          },
          {
            "type": "TripleConstraint",
            "predicate": "http://purl.org/dc/terms/creator",
            "valueExpr": "http://a.example/schema#person",
            "min": 1,
            "max": -1
          }
        ]
      }
    },
    {
      "type": "Shape",
      "id": "http://a.example/schema#person",
      "expression": {
        "type": "EachOf",
        "expressions": [
          {
            "type": "TripleConstraint",
            "predicate": "http://xmlns.com/foaf/0.1/name",
            "valueExpr": {
              "type": "NodeConstraint",
              "datatype": "http://www.w3.org/2001/XMLSchema#string"
            },
            "min": 1,
            "max": -1
          },
          {
            "type": "TripleConstraint",
            "predicate": "http://xmlns.com/foaf/0.1/homepage",
            "valueExpr": {
              "type": "NodeConstraint",
              "nodeKind": "iri"
            },
            "min": 0,
            "max": 1
          }
        ]
      }
    }
  ]
}
```


## Proposed solution

Allow the use of compact syntax. This affects the grammar directly at:

* Syntax, as it needs to match compact spec.

## Alternatives considered

Use of other syntaxes like JSON-LD or N-Triples.
