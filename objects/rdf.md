# Cultural Heritage Objects: RDF model

The model uses [Linked Art](https://linked.art/) as foundation.

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
# Original IRI of object: https://dataprovider.nl/object1

# MD5 of original IRI of object
<https://n2t.net/ark:/27023/b062d006e928da1bfec6791bf75adf40>
    a crm:E22_Human-Made_Object ;

    ####################
    # Types
    ####################

    crm:P2_has_type <http://vocab.getty.edu/aat/300033618> ; # Paintings

    ####################
    # Materials
    ####################

    crm:P45_consists_of <http://vocab.getty.edu/aat/300015050> ; # Oil paint

    ####################
    # Subjects
    ####################

    crm:P62_depicts <http://vocab.getty.edu/aat/300152441> ; # Celebrations

    ####################
    # Owners
    ####################

    crm:P52_has_current_owner <https://dataprovider.nl/> ;

    ####################
    # Identifiers
    ####################

    crm:P1_is_identified_by <https://n2t.net/ark:/27023/7380268038466c67b09e6f6fae8d7657> ;

    ####################
    # Names
    ####################

    crm:P1_is_identified_by <https://n2t.net/ark:/27023/d0c910b09e220797e726b9cce0484626> ;

    ####################
    # Descriptions
    ####################

    crm:P67i_is_referred_to_by <https://n2t.net/ark:/27023/13fcc150b326ff6dacdee7a3011ff60b> ;

    ####################
    # Dimensions: width
    ####################

    crm:P43_has_dimension <https://n2t.net/ark:/27023/ff1f990a536656a4748e6864aa0b1d00> ;

    ####################
    # Dimensions: height
    ####################

    crm:P43_has_dimension <https://n2t.net/ark:/27023/4dc66d66e8820c52a68c6b548b53219b> ;

    ####################
    # Inscriptions
    ####################

    crm:P128_carries <https://n2t.net/ark:/27023/a591bfec40471029fb5785a447363283> ;

    ####################
    # Production events
    ####################

    crm:P108i_was_produced_by <https://n2t.net/ark:/27023/7978f044b5bab743788a9c05fc436ac6> ;

    ####################
    # Visual items
    ####################

    crm:P65_shows_visual_item <https://n2t.net/ark:/27023/c085970357b8c90b719486d0fdf5e472> ;

    ####################
    # Part of dataset
    ####################

    la:member_of <https://n2t.net/ark:/27023/bb31a8ed445e5800a192eded125d7cdb> .

####################
# Identifier
####################

# MD5 of original IRI of object + 'identifier' + sequence number
<https://n2t.net/ark:/27023/7380268038466c67b09e6f6fae8d7657>
    a crm:E42_Identifier ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300404626> ; # Identification number
    crm:P190_has_symbolic_content "1234" .

####################
# Name
####################

# MD5 of original IRI of object + 'name' + sequence number
<https://n2t.net/ark:/27023/d0c910b09e220797e726b9cce0484626>
    a crm:E33_E41_Linguistic_Appellation ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ; # Name
    crm:P190_has_symbolic_content "Object 1" ;
    crm:P72_has_language <http://vocab.getty.edu/aat/300388277> . # English

####################
# Description
####################

# MD5 of original IRI of object + 'description' + sequence number
<https://n2t.net/ark:/27023/13fcc150b326ff6dacdee7a3011ff60b>
    a crm:E33_Linguistic_Object ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300435416> ; # Description
    crm:P190_has_symbolic_content "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean ultrices velit vitae vulputate tincidunt. Donec dictum tortor nec tempus mollis." ;
    crm:P72_has_language <http://vocab.getty.edu/aat/300388277> . # English

####################
# Dimension: width
####################

# MD5 of original IRI of object + 'width' + sequence number
<https://n2t.net/ark:/27023/ff1f990a536656a4748e6864aa0b1d00>
    a crm:E54_Dimension ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055647> ; # Width
    crm:P90_has_value 120.0 ;
    crm:P91_has_unit <http://vocab.getty.edu/aat/300379098> . # Centimeters

####################
# Dimension: height
####################

# MD5 of original IRI of object + 'height' + sequence number
<https://n2t.net/ark:/27023/4dc66d66e8820c52a68c6b548b53219b>
    a crm:E54_Dimension ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300055644> ; # Height
    crm:P90_has_value 112.0 ;
    crm:P91_has_unit <http://vocab.getty.edu/aat/300379098> . # Centimeters

####################
# Inscription
####################

# MD5 of original IRI of object + 'inscription' + sequence number
<https://n2t.net/ark:/27023/b64aec6a0f5fbb5532c8557caf08ebdd>
    a crm:E33_Linguistic_Object ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300028702> ; # Inscription
    crm:P190_has_symbolic_content "Maecenas commodo est neque" .

####################
# Creator
####################

# MD5 of original IRI of object + 'creator' + sequence number
<https://n2t.net/ark:/27023/17c8d9e5e5275425714135a56ef7cbbd>
    a crm:E21_Person ;
    rdfs:label "Vincent van Gogh" .

####################
# Date of creation
####################

# MD5 of original IRI of object + 'datecreation' + sequence number
<https://n2t.net/ark:/27023/9e381563cea95ccedf510a6dc6500636>
    a crm:E52_Time-Span ;
    crm:P82a_begin_of_the_begin "1889-05"^^xsd:gYearMonth ;
    crm:P82b_end_of_the_end "1890-12"^^xsd:gYearMonth .

####################
# Production event
####################

# MD5 of original IRI of object + 'production' + sequence number
<https://n2t.net/ark:/27023/7978f044b5bab743788a9c05fc436ac6>
    a crm:E12_Production ;
    crm:P32_used_general_technique <http://vocab.getty.edu/aat/300133274> ; # Albumen process
    crm:P14_carried_out_by <https://n2t.net/ark:/27023/17c8d9e5e5275425714135a56ef7cbbd> ;
    crm:P4_has_time-span <https://n2t.net/ark:/27023/9e381563cea95ccedf510a6dc6500636> ;
    crm:P7_took_place_at <https://sws.geonames.org/3382998/> . # Suriname

####################
# Digital object
####################

# MD5 of original IRI of object + 'digitalobject'+ sequence number
<https://n2t.net/ark:/27023/02656bc2fee98af173d11607e8861ee4>
    a dig:D1_Digital_Object ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300215302> ; # Digital image
    la:access_point <http://images.memorix.nl/rce/thumb/1600x1600/e0164095-6a2d-b448-cc59-3a8ab2fafed7.jpg> .

####################
# Right of digital object
####################

# MD5 of original IRI of object + 'digitalobjectrights'+ sequence number
<https://n2t.net/ark:/27023/a663867ce99ac68a054618926e0a606c>
    a crm:E30_Right ;
    crm:P2_has_type <https://creativecommons.org/licenses/by/1.0/> .

####################
# Copyright statement of digital object
####################

# MD5 of original IRI of object + 'digitalobjectstatement' + sequence number
<https://n2t.net/ark:/27023/a663867ce99ac68a054618926e0a606c>
    a crm:E33_Linguistic_Object ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300435434> ; # 'A formal statement of the copyright or licensing of a work, and/or any restrictions placed on it.'
    crm:P190_has_symbolic_content "Some statement" ;
    crm:P72_has_language <http://vocab.getty.edu/aat/300388277> . # English

####################
# Visual item
####################

# MD5 of original IRI of object + 'visualitem' + sequence number
<https://n2t.net/ark:/27023/c085970357b8c90b719486d0fdf5e472>
    a crm:E36_Visual_Item ;
    la:digitally_shown_by <https://n2t.net/ark:/27023/02656bc2fee98af173d11607e8861ee4> ;
    crm:P104_is_subject_to <https://n2t.net/ark:/27023/a663867ce99ac68a054618926e0a606c> ;
    crm:P67i_is_referred_to_by <https://n2t.net/ark:/27023/a663867ce99ac68a054618926e0a606c> .

####################
# Dataset
####################

# MD5 of original IRI of dataset
<https://n2t.net/ark:/27023/bb31a8ed445e5800a192eded125d7cdb>
    a schema:Dataset ;
    prov:wasDerivedFrom <https://dataprovider.nl/dataset1> . # Link to original dataset of the data provider
```
