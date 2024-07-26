# Provenance events: RDF model

RDF model for describing a provenance event. The model is a translation of the [conceptual model](./conceptual.md). The model uses [Linked Art](https://linked.art/model/provenance/) as foundation, using [attribute assignments](https://linked.art/model/assertion/) to associate additional information to the provenance event (e.g. the likelihood of the event).

## Acquisition

A cultural heritage object was acquired by an actor from another actor

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://nanopublication.example/1>
    a crm:E13_Attribute_Assignment ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300435722> ;
    crm:P177_assigned_property_of_type crm:P24i_changed_ownership_through ;
    # Encapsulate the information of the provenance event
    crm:P141_assigned [
        a crm:E8_Acquisition ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300417642> ;
        crm:P24_transferred_title_of <https://example.org/object> ;
        crm:P23_transferred_title_from <http://www.wikidata.org/entity/Q517> ;
        crm:P22_transferred_title_to <http://www.wikidata.org/entity/Q171480> ;
        crm:P4_has_time-span [
            a crm:E52_Time-Span ;
            rdfs:label "Provenance Activity Timespan" ;
            crm:P82a_begin_of_the_begin "1855-01-01"^^xsd:date ;
            crm:P82b_end_of_the_end "1855-12-31"^^xsd:date ;
        ] ;
        crm:P7_took_place_at <https://sws.geonames.org/2988507/> ;
        crm:P67i_is_referred_to_by [
            a crm:E33_Linguistic_Object ;
            crm:P190_has_symbolic_content "Bought for 1500 US dollars" ;
            crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
        ] ;
        crm:P67i_is_referred_to_by [
            a crm:E33_Linguistic_Object ;
            crm:P190_has_symbolic_content "See webpage http://example.org/3" ;
            crm:P2_has_type <http://vocab.getty.edu/aat/300435423> ; # "Citation"
        ] ;
    ] .

<http://vocab.getty.edu/aat/300435722>
    rdfs:label "Possibly" .

<http://vocab.getty.edu/aat/300417642>
    rdfs:label "Purchase" .

<http://www.wikidata.org/entity/Q517>
    rdfs:label "Napoleon" .

<http://www.wikidata.org/entity/Q171480>
    rdfs:label "Joséphine de Beauharnais" .

<https://sws.geonames.org/2988507/>
    rdfs:label "Paris" .
```

## Transfer of custody

A cultural heritage object was transferred from an actor to another actor

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://nanopublication.example/1>
    a crm:E13_Attribute_Assignment ;
    crm:P177_assigned_property_of_type crm:P30i_custody_transferred_through ;
    # Encapsulate the information of the provenance event
    crm:P141_assigned [
        a crm:E10_Transfer_of_Custody ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300445014> ;
        crm:P30_transferred_custody_of <https://example.org/object> ;
        crm:P28_custody_surrendered_by <http://www.wikidata.org/entity/Q131691> ;
        crm:P29_custody_received_by <http://www.wikidata.org/entity/Q9439> ;
        crm:P4_has_time-span [
            a crm:E52_Time-Span ;
            rdfs:label "Provenance Activity Timespan" ;
            crm:P82a_begin_of_the_begin "1850-02-01"^^xsd:date ;
            crm:P82b_end_of_the_end "1850-07-13"^^xsd:date ;
        ] ;
        crm:P7_took_place_at <https://sws.geonames.org/2643743/> ;
        crm:P67i_is_referred_to_by [
            a crm:E33_Linguistic_Object ;
            crm:P190_has_symbolic_content "Returned to the owner" ;
            crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
        ] ;
        crm:P67i_is_referred_to_by [
            a crm:E33_Linguistic_Object ;
            crm:P190_has_symbolic_content "See webpage http://example.org/3" ;
            crm:P2_has_type <http://vocab.getty.edu/aat/300435423> ; # "Citation"
        ] ;
    ] .

<http://vocab.getty.edu/aat/300445014>
    rdfs:label "Returning" .

<http://www.wikidata.org/entity/Q131691>
    rdfs:label "Arthur Wellesley" .

<http://www.wikidata.org/entity/Q9439>
    rdfs:label "Victoria" .

<https://sws.geonames.org/2643743/>
    rdfs:label "London" .
```

## Querying enrichments

Endpoint: https://virtuoso.nps.knowledgepixels.com/sparql

```sparql
PREFIX cc: <https://n2t.net/ark:/27023/9819f32405815dc7f2e0ecd9d8a9e604#>
PREFIX crm: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX np: <http://www.nanopub.org/nschema#>
PREFIX npa: <http://purl.org/nanopub/admin/>
PREFIX npx: <http://purl.org/nanopub/x/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?dateCreated
  ?license
  ?creator ?creatorName
  ?group ?groupName
  ?qualifier ?qualifierName
  ?source
  ?type
  ?transferredTitleFrom ?transferredTitleFromName
  ?transferredTitleTo ?transferredTitleToName
  ?additionalType ?additionalTypeName
  ?location ?locationName
  ?beginOfTheBegin ?endOfTheEnd
  ?description
  ?language
  ?citation
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
      npx:introduces ?attributeAssignment ;
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
    ?attributeAssignment crm:P141_assigned ?provenanceEvent .

    OPTIONAL {
      ?attributeAssignment crm:P2_has_type ?qualifier .
      ?qualifier rdfs:label ?qualifierName .
    }

    {
      ?provenanceEvent a ?type ;
        crm:P24_transferred_title_of ?source .

      OPTIONAL {
        ?provenanceEvent crm:P23_transferred_title_from ?transferredTitleFrom .
        ?transferredTitleFrom rdfs:label ?transferredTitleFromName .
      }

      OPTIONAL {
        ?provenanceEvent crm:P22_transferred_title_to ?transferredTitleTo .
        ?transferredTitleTo rdfs:label ?transferredTitleToName .
      }
    }
    UNION
    {
      ?provenanceEvent a ?type ;
        crm:P30_transferred_custody_of ?source .

      OPTIONAL {
        ?provenanceEvent crm:P28_custody_surrendered_by ?transferredTitleFrom .
        ?transferredTitleFrom rdfs:label ?transferredTitleFromName .
      }

      OPTIONAL {
        ?provenanceEvent crm:P29_custody_received_by ?transferredTitleTo .
        ?transferredTitleTo rdfs:label ?transferredTitleToName .
      }
    }

    OPTIONAL {
      ?provenanceEvent crm:P2_has_type ?additionalType .
      ?additionalType rdfs:label ?additionalTypeName .
    }

    OPTIONAL {
      ?provenanceEvent crm:P7_took_place_at ?location .
      ?location rdfs:label ?locationName .
    }

    OPTIONAL {
      ?provenanceEvent crm:P4_has_time-span ?timeSpan .
      ?timeSpan crm:P82a_begin_of_the_begin ?beginOfTheBegin ;
        crm:P82b_end_of_the_end ?endOfTheEnd .
    }

    OPTIONAL {
      ?provenanceEvent crm:P67i_is_referred_to_by [
        crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # Provenance statement
        crm:P190_has_symbolic_content ?description ;
      ] .

      BIND(LANG(?description) AS ?language)
    }

    OPTIONAL {
      ?provenanceEvent crm:P67i_is_referred_to_by [
        crm:P2_has_type <http://vocab.getty.edu/aat/300435423> ; # Citation
        crm:P190_has_symbolic_content ?citation ;
      ] .
    }
  }
}
ORDER BY DESC(?dateCreated)
```
