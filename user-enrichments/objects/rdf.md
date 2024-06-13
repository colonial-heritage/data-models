# Objects: RDF model

RDF model for describing an object enrichment. The model is a translation of the [conceptual model](./conceptual.md). The model uses the [Web Annotation Vocabulary](https://www.w3.org/TR/annotation-vocab/) as foundation.

## Enrichment about a certain property

```turtle
@prefix oa: <http://www.w3.org/ns/oa#> .
@prefix cc: <https://data.colonialcollections.nl/schemas/nanopub#> . # Example
@prefix dc: <http://purl.org/dc/elements/1.1/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

<https://nanopublication.example/1>
    a oa:Annotation ;
    oa:hasBody [
        a oa:TextualBody ;
        rdf:value "A comment about the name of an object"@en ;
        rdf:comment "A citation or reference to a work that supports the comment"@en ;
        dc:format "text/plain" ;
        dc:language "en"
    ] ;
    oa:hasTarget [
        oa:hasScope cc:name ; # The scope or context in which the resource is used within the Annotation, e.g. an annotation about the name of a heritage object
        oa:hasSource <https://example.org/object> # Reference to the object
    ] .
```
