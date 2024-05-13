# Objects: RDF model

RDF model for describing an object enrichment. The model is a translation of the [conceptual model](./conceptual.md). The model uses the [Web Annotation Vocabulary](https://www.w3.org/TR/annotation-vocab/) as foundation.

## Enrichment about a certain property

Example: a user has made an enrichment about the name/title a cultural heritage object

```turtle
@prefix oa: <http://www.w3.org/ns/oa#> .
@prefix cc: <https://data.colonialcollections.nl/schemas/nanopub#> . # Does not resolve yet
@prefix dc: <http://purl.org/dc/elements/1.1/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

<https://nanopublication.example/1> # IRI for illustration only; will be a blank node in practice
    a oa:Annotation ;
    oa:hasBody [
        a oa:TextualBody ;
        rdf:value "A comment about the name of an object"@en ;
        rdf:comment "A citation or reference to a work that supports the comment"@en ;
        dc:format "text/plain" ;
        dc:language "en"
    ] ;
    oa:hasTarget cc:name . # Reference to the resource the enrichment is about, e.g. the name of the object

cc:name
    a oa:SpecificResource ;
    oa:hasSource <http://example.org/object> . # Reference to the object
```
