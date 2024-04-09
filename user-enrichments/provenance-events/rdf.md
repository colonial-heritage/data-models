# Provenance events: RDF model

RDF model for describing a provenance event. The model is a translation of the [conceptual model](./conceptual.md). The model uses [Linked Art](https://linked.art/model/provenance/) as foundation, using [attribute assignments](https://linked.art/model/assertion/) to associate additional information to the provenance event (e.g. the likelihood of the event).

## Example: an object was sold to someone, but it's uncertain whether this actually happened ('it possibly happened')

```trig
@prefix cc: <https://data.colonialcollections.nl/schemas/nanopub#> .
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix dcterms: <http://purl.org/dc/terms/license> .
@prefix np: <http://www.nanopub.org/nschema#> .
@prefix npx: <http://purl.org/nanopub/x/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix temp-nanopub-id: <http://purl.org/nanopub/temp/temp-nanopub-id/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

temp-nanopub-id:assertion {
    <https://nanopublication.example/1> # Actually: a blank node
        a crm:E13_Attribute_Assignment ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300435722> ;
        crm:P177_assigned_property_of_type crm:P24i_changed_ownership_through ;
        # Encapsulate the information of the provenance event that 'possibly happened':
        crm:P141_assigned [
            a crm:E8_Acquisition ;
            crm:P2_has_type <http://vocab.getty.edu/aat/300417642> ;
            crm:P24_transferred_title_of <https://example.org/object> ;
            crm:P23_transferred_title_from <http://www.wikidata.org/entity/Q517> ; # Seller
            crm:P22_transferred_title_to <http://www.wikidata.org/entity/Q171480> ; # Buyer
            crm:P4_has_time-span [
                a crm:E52_Time-Span ;
                rdfs:label "Provenance Activity Timespan" ;
                crm:P82a_begin_of_the_begin "1855"^^xsd:gYear ;
                crm:P82b_end_of_the_end "1855"^^xsd:gYear ;
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
}

temp-nanopub-id:Head {
    temp-nanopub-id:
        a np:Nanopublication ;
        np:hasAssertion temp-nanopub-id:assertion ;
        np:hasProvenance temp-nanopub-id:provenance ;
        np:hasPublicationInfo temp-nanopub-id:pubinfo ;
}

temp-nanopub-id:provenance {
    temp-nanopub-id:assertion prov:wasAttributedTo <https://www.linkedin.com/in/person/>
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
        npx:introduces <https://nanopublication.example/1> .

    # Additional information about the actor who created the nanopublication.
    # Be aware that both the IRI and the additional information of the actor can change,
    # e.g. because the actor changes his or her profile settings in e.g. LinkedIn.
    # These triples capture the information as it was at the moment of creation of the nanopublication.
    <https://www.linkedin.com/in/person/>
      rdfs:label "Person" .
}
```
