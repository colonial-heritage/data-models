# Local Contexts Notices: RDF model

RDF model for describing a [Local Contexts Notice](https://localcontexts.org/notices/about-the-notices/) enrichment. The model uses the [Web Annotation Vocabulary](https://www.w3.org/TR/annotation-vocab/) as foundation.

```turtle
@prefix as: <https://www.w3.org/ns/activitystreams#> .
@prefix oa: <http://www.w3.org/ns/oa#> .
@prefix dc: <http://purl.org/dc/elements/1.1/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

<https://nanopublication.example/1>
    a oa:Annotation ;
    oa:hasBody [
        a oa:TextualBody ;
        rdf:value "A description about the use of a Notice"@en ;
        dc:format "text/plain" ;
        dc:language "en" ;
        as:context <https://localcontexts.org/notice/authorization/> ; # Reference to a Notice
    ] ;
    oa:hasTarget <https://example.org/object> . # Reference to the object
```
