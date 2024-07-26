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

## Querying enrichments

Endpoint: https://virtuoso.nps.knowledgepixels.com/sparql

```sparql
PREFIX as: <https://www.w3.org/ns/activitystreams#>
PREFIX cc: <https://n2t.net/ark:/27023/9819f32405815dc7f2e0ecd9d8a9e604#>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX oa: <http://www.w3.org/ns/oa#>
PREFIX np: <http://www.nanopub.org/nschema#>
PREFIX npa: <http://purl.org/nanopub/admin/>
PREFIX npx: <http://purl.org/nanopub/x/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?dateCreated
  ?license
  ?creator ?creatorName
  ?group ?groupName
  ?source
  ?context
  ?value
  ?language
  ?comment
WHERE {
  graph npa:graph {
    ?np npa:hasHeadGraph ?head ;
      dcterms:created ?dateCreated .
  }

  graph ?head {
    ?np np:hasProvenance ?provenance ;
      np:hasPublicationInfo ?pubInfo ;
      np:hasAssertion ?assertion .
  }

  graph ?pubInfo {
    ?np a cc:Nanopub ;
      npx:introduces ?annotation ;
      dcterms:license ?license .
  }

  graph ?provenance {
    ?assertion prov:wasAttributedTo ?creator .
    ?creator rdfs:label ?creatorName .

    OPTIONAL {
      ?creator prov:qualifiedDelegation [
        prov:agent ?group
      ] .
      ?group rdfs:label ?groupName
    }
  }

  graph ?assertion {
    ?annotation a oa:Annotation ;
       oa:hasTarget ?source .

    ?annotation oa:hasBody ?body .
    ?body as:context ?context .

    OPTIONAL {
      ?body rdf:value ?value .
      OPTIONAL {
        ?body dc:language ?language .
      }
      OPTIONAL {
        ?body rdfs:comment ?comment
      }
    }
  }
}
ORDER BY DESC(?dateCreated)
```
