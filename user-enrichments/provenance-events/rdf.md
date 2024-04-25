# Provenance events: RDF model

RDF model for describing a provenance event. The model is a translation of the [conceptual model](./conceptual.md). The model uses [Linked Art](https://linked.art/model/provenance/) as foundation, using [attribute assignments](https://linked.art/model/assertion/) to associate additional information to the provenance event (e.g. the likelihood of the event).

## Generic model for publishing a nanopublication

An implementation of the [Nanopublications model](https://nanopub.net/)

```turtle
@prefix cc: <https://data.colonialcollections.nl/schemas/nanopub#> . # Does not resolve yet
@prefix dcterms: <http://purl.org/dc/terms/license> .
@prefix np: <http://www.nanopub.org/nschema#> .
@prefix npx: <http://purl.org/nanopub/x/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix temp-nanopub-id: <http://purl.org/nanopub/temp/temp-nanopub-id/> .

temp-nanopub-id:Head {
    temp-nanopub-id:
        a np:Nanopublication ;
        np:hasAssertion temp-nanopub-id:assertion ;
        np:hasProvenance temp-nanopub-id:provenance ;
        np:hasPublicationInfo temp-nanopub-id:pubinfo .
}

temp-nanopub-id:assertion {
    # The contribution of a user (see the specific models underneath)
}

temp-nanopub-id:provenance {
    temp-nanopub-id:assertion prov:wasAttributedTo <https://www.linkedin.com/in/person/> .
}

temp-nanopub-id:pubinfo {
    # Tool used for creating the nanopublication
    <https://app.colonialcollections.nl/>
        a npx:SoftwareTool ;
        rdfs:label "Colonial Collections" .

    temp-nanopub-id:
        a cc:Nanopub, # Generic type, so that we can easily retrieve all nanopubs of Colonial Collections, regardless of their specific type
          cc:ProvenanceEventVersion1 ; # Specific type, including a version number, so that we can distinguish between multiple versions of the specific type
        dcterms:license <https://creativecommons.org/licenses/by/4.0/> ;
        npx:wasCreatedWith <https://app.colonialcollections.nl/> ;
        npx:introduces <https://nanopublication.example/1> . # Reference to the information contributed by a user (see the models underneath)

    # Additional information about the user who created the nanopublication.
    # Be aware that both the IRI and the additional information of the user can change,
    # if/when the user changes his or her profile settings in e.g. LinkedIn.
    # These triples capture the information as it was at the moment of creation of the nanopublication.
    <https://www.linkedin.com/in/person/>
        rdfs:label "Name of person" ;
        dcterms:isPartOf <https://example.org/community-1> .

    <https://example.org/community-1>
        rdfs:label "Name of community" .
}
```

## Specific model: acquisition

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

## Specific model: transfer of custody

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
