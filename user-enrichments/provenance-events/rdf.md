# Provenance events: RDF model

RDF model for describing a provenance event. The model is a translation of the [conceptual model](./conceptual.md). The model uses [Linked Art](https://linked.art/model/provenance/) as foundation, using [attribute assignments](https://linked.art/model/assertion/) to associate additional information to the provenance event (e.g. the likelihood of the event).

## Acquisition

A cultural heritage object was acquired by an actor from another actor

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://nanopublication.example/1> # IRI for illustration only; will be a blank node in practice
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

<https://nanopublication.example/1> # IRI for illustration only; will be a blank node in practice
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
