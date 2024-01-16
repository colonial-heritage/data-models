# Persons: RDF model

The model uses [Linked Art](https://linked.art/model/actor/) as foundation.

## Status

Draft

## Example

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix dig: <http://www.ics.forth.gr/isl/CRMdig/> .
@prefix la: <https://linked.art/ns/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix schema: <https://schema.org/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

# Original IRI of dataset: https://dataprovider.nl/dataset1
# Original IRI of person: https://dataprovider.nl/person1

# MD5 of original IRI of person
<https://n2t.net/ark:/27023/37cd45dfd4d863a8509fcff5aed4fdc7>
    a crm:E21_Person ;

    ####################
    # Name
    ####################

    crm:P1_is_identified_by <https://n2t.net/ark:/27023/bc19ea4349fb2a752d383acdc7b3ad1d> ;

    ####################
    # Birth
    ####################

    crm:P98i_was_born <https://n2t.net/ark:/27023/0254159eeb62f4e68bdd454a3c170b75> ;

    ####################
    # Death
    ####################

    crm:P100i_died_in <https://n2t.net/ark:/27023/ecc3b6cea79246cbb39425664c14adff> ;

    ####################
    # Part of dataset
    ####################

    la:member_of <https://n2t.net/ark:/27023/bb31a8ed445e5800a192eded125d7cdb> .

####################
# Name
####################

# MD5 of original IRI of person + 'name'
<https://n2t.net/ark:/27023/bc19ea4349fb2a752d383acdc7b3ad1d>
    a crm:E33_E41_Linguistic_Appellation ;
    rdfs:label "John Doe" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ; # Name
    crm:P190_has_symbolic_content "John Doe" .

####################
# Birth
####################

# MD5 of original IRI of person + 'birth'
<https://n2t.net/ark:/27023/0254159eeb62f4e68bdd454a3c170b75>
    a crm:E67_Birth ;
    crm:P4_has_time-span <https://n2t.net/ark:/27023/9c6cf905d3061b3734decf4372583d95> ;
    crm:P7_took_place_at <https://n2t.net/ark:/27023/926cae587514cfd9d018a7d8927ad763> .

####################
# Date of birth
####################

# MD5 of original IRI of person + 'datebirth'
<https://n2t.net/ark:/27023/9c6cf905d3061b3734decf4372583d95>
    a crm:E52_Time-Span ;
    crm:P82a_begin_of_the_begin "1889-05"^^xsd:gYearMonth ;
    crm:P82b_end_of_the_end "1890-12"^^xsd:gYearMonth .

####################
# Place of birth (if not linked to GeoNames)
####################

# MD5 of original IRI of person + 'placebirth'
<https://n2t.net/ark:/27023/926cae587514cfd9d018a7d8927ad763>
    a crm:E53_Place;
    crm:P2_has_type <http://vocab.getty.edu/aat/300008389> ; # City (if known from the data)
    crm:P1_is_identified_by <https://n2t.net/ark:/27023/1c1b9961929734fd4cd82639088b1675> .

####################
# Name of place of birth
####################

# MD5 of original IRI of person + 'placebirthname'
<https://n2t.net/ark:/27023/1c1b9961929734fd4cd82639088b1675>
    a crm:E33_E41_Linguistic_Appellation ;
    rdfs:label "Amsterdam" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ; # Name
    crm:P190_has_symbolic_content "Amsterdam" .

####################
# Death
####################

# MD5 of original IRI of person + 'death'
<https://n2t.net/ark:/27023/ecc3b6cea79246cbb39425664c14adff>
    a crm:E69_Death ;
    crm:P4_has_time-span <https://n2t.net/ark:/27023/f6655931570be44a9fd264f33ed135a0> ;
    crm:P7_took_place_at <https://n2t.net/ark:/27023/b6312be7015e62fb78dedac685cbaceb> .

####################
# Date of death
####################

# MD5 of original IRI of person + 'datedeath'
<https://n2t.net/ark:/27023/f6655931570be44a9fd264f33ed135a0>
    a crm:E52_Time-Span ;
    crm:P82a_begin_of_the_begin "1889-05"^^xsd:gYearMonth ;
    crm:P82b_end_of_the_end "1890-12"^^xsd:gYearMonth .

####################
# Place of death (if not linked to GeoNames)
####################

# MD5 of original IRI of person + 'placedeath'
<https://n2t.net/ark:/27023/b6312be7015e62fb78dedac685cbaceb>
    a crm:E53_Place;
    crm:P2_has_type <http://vocab.getty.edu/aat/300008389> ; # City (if known from the data)
    crm:P1_is_identified_by <https://n2t.net/ark:/27023/ba95f880264e35db39fbcd71dbb9a528> .

####################
# Name of place of death
####################

# MD5 of original IRI of person + 'placedeathname'
<https://n2t.net/ark:/27023/ba95f880264e35db39fbcd71dbb9a528>
    a crm:E33_E41_Linguistic_Appellation ;
    rdfs:label "The Hague" ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ; # Name
    crm:P190_has_symbolic_content "The Hague" .

####################
# Dataset
####################

# MD5 of original IRI of dataset
<https://n2t.net/ark:/27023/bb31a8ed445e5800a192eded125d7cdb>
    a schema:Dataset, prov:Entity ;
    prov:wasDerivedFrom <https://dataprovider.nl/dataset1> ; # Link to original dataset of the data provider
    prov:wasGeneratedBy [
        a prov:Activity ;
        prov:endedAtTime "2023-12-14T00:00:00-04:00"^^xsd:dateTime ;
    ] ;
    prov:wasAssociatedWith [
        a prov:SoftwareAgent ;
        rdfs:label "ETL" ;
    ] .
```
