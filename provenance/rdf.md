# Provenance information: RDF model

Based on [Linked Art](https://linked.art/model/provenance/).

Status: draft

## Example

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://data.museum.nl/object/1234>
    a crm:E22_Human-Made_Object ;
    crm:P1_is_identified_by [
        a crm:E33_E41_Linguistic_Appellation ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ;
        crm:P190_has_symbolic_content "Fragment van een figuur" ;
    ] ;
    crm:P52_has_current_owner <https://museum.nl/> ;
    crm:P24i_changed_ownership_through <https://data.museum.nl/object/1234/provenance/event/1/activity/1> ,
                                       <https://data.museum.nl/object/1234/provenance/event/2/activity/1> ;
    crm:P30i_custody_transferred_through <https://data.museum.nl/object/1234/provenance/event/3/activity/1> ,
                                         <https://data.museum.nl/object/1234/provenance/event/4/activity/1> ;
.

<https://data.museum.nl/object/1234/provenance/event/1/activity/1>
    a crm:E8_Acquisition ;
    rdfs:label "Acquisition of object from seller" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300417642> ; # "Purchase"
    crm:P24_transferred_title_of <https://data.museum.nl/object/1234> ;
    crm:P23_transferred_title_from <https://data.museum.nl/person/1> ; # Seller
    crm:P22_transferred_title_to <https://data.museum.nl/person/2> ; # Buyer
    crm:P9i_forms_part_of <https://data.museum.nl/object/1234/provenance/event/1> ;
.

<https://data.museum.nl/object/1234/provenance/event/1>
    a crm:E7_Activity ;
    rdfs:label "Purchase of object" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055863> ; # "Provenance event"
    crm:P4_has_time-span [
        a crm:E52_Time-Span ;
        rdfs:label "Provenance Activity Timespan" ;
        crm:P82a_begin_of_the_begin "1855"^^xsd:gYear ;
        crm:P82b_end_of_the_end "1855"^^xsd:gYear ;
    ] ;
    crm:P7_took_place_at <https://sws.geonames.org/1642911/> ;
    crm:P67i_is_referred_to_by [
        a crm:E33_Linguistic_Object ;
        crm:P190_has_symbolic_content "Bought for 1500 US dollars" ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
    ] ;
    crm:P9_consists_of <https://data.museum.nl/object/1234/provenance/event/1/activity/1> ;
    crm:P183_ends_before_the_start_of <https://data.museum.nl/object/1234/provenance/event/2> ;
.

<https://data.museum.nl/object/1234/provenance/event/2/activity/1>
    a crm:E8_Acquisition ;
    rdfs:label "Acquisition of object from seller" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300417642> ; # "Purchase"
    crm:P24_transferred_title_of <https://data.museum.nl/object/1234> ;
    crm:P23_transferred_title_from <https://data.museum.nl/person/2> ; # Seller
    crm:P22_transferred_title_to <https://museum.nl> ; # Buyer
    crm:P9i_forms_part_of <https://data.museum.nl/object/1234/provenance/event/2> ;
.

<https://data.museum.nl/object/1234/provenance/event/2/activity/1>
    a crm:E7_Activity ;
    rdfs:label "Purchase of object" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055863> ; # "Provenance event"
    crm:P4_has_time-span [
        a crm:E52_Time-Span ;
        rdfs:label "Provenance Activity Timespan" ;
        crm:P82a_begin_of_the_begin "1879"^^xsd:gYear ;
        crm:P82b_end_of_the_end "1879"^^xsd:gYear ;
    ] ;
    crm:P7_took_place_at <https://sws.geonames.org/2759794/> ;
    crm:P67i_is_referred_to_by [
        a crm:E33_Linguistic_Object ;
        crm:P190_has_symbolic_content "Bought at an auction" ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
    ] ;
    crm:P9_consists_of <https://data.museum.nl/object/1234/provenance/event/2/activity/1> ;
    crm:P183i_starts_after_the_end_of <https://data.museum.nl/object/1234/provenance/event/1> ;
    crm:P183_ends_before_the_start_of <https://data.museum.nl/object/1234/provenance/event/3> ;
.

<https://data.museum.nl/object/1234/provenance/event/3/activity/1>
    a crm:E10_Transfer_of_Custody ;
    rdfs:label "Theft of object from owner" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055292> ; # "Theft"
    crm:P30_transferred_custody_of <https://data.museum.nl/object/1234> ;
    crm:P28_custody_surrendered_by <https://museum.nl/> ; # Owner
    crm:P9i_forms_part_of <https://data.museum.nl/object/1234/provenance/event/3> ;
.

<https://data.museum.nl/object/1234/provenance/event/3>
    a crm:E7_Activity ;
    rdfs:label "Theft of object" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055863> ; # "Provenance event"
    crm:P4_has_time-span [
        a crm:E52_Time-Span ;
        rdfs:label "Provenance Activity Timespan" ;
        crm:P82a_begin_of_the_begin "1901"^^xsd:gYear ;
        crm:P82b_end_of_the_end "1901"^^xsd:gYear ;
    ] ;
    crm:P7_took_place_at <https://sws.geonames.org/2759794/> ;
    crm:P67i_is_referred_to_by [
        a crm:E33_Linguistic_Object ;
        crm:P190_has_symbolic_content "Illegally obtained" ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
    ] ;
    crm:P9_consists_of <https://data.museum.nl/object/1234/provenance/event/3/activity/1> ;
    crm:P183i_starts_after_the_end_of <https://data.museum.nl/object/1234/provenance/event/2> ;
    crm:P183_ends_before_the_start_of <https://data.museum.nl/object/1234/provenance/event/4> ;
.

<https://data.museum.nl/object/1234/provenance/event/4/activity/1>
    a crm:E10_Transfer_of_Custody ;
    rdfs:label "Return of object to owner" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300445014> ; # "Returning"
    crm:P30_transferred_custody_of <https://data.museum.nl/object/1234> ;
    crm:P29_custody_received_by <https://museum.nl/> ; # Owner
    crm:P9i_forms_part_of <https://data.museum.nl/object/1234/provenance/event/4> ;
.

<https://data.museum.nl/object/1234/provenance/event/4>
    a crm:E7_Activity ;
    rdfs:label "Return of object" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055863> ; # "Provenance event"
    crm:P4_has_time-span [
        a crm:E52_Time-Span ;
        rdfs:label "Provenance Activity Timespan" ;
        crm:P82a_begin_of_the_begin "1939"^^xsd:gYear ;
        crm:P82b_end_of_the_end "1939"^^xsd:gYear ;
    ] ;
    crm:P7_took_place_at <https://sws.geonames.org/2988507/> ;
    crm:P67i_is_referred_to_by [
        a crm:E33_Linguistic_Object ;
        crm:P190_has_symbolic_content "Found in a basement" ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300444174> ; # "Provenance statement"
    ] ;
    crm:P9_consists_of <https://data.museum.nl/object/1234/provenance/event/4/activity/1> ;
    crm:P183i_starts_after_the_end_of <https://data.museum.nl/object/1234/provenance/event/3> ;
.
```
