# Communities: RDF model

RDF model for describing a community and its members. The model is a translation of the [conceptual model](./conceptual.md). The model uses [Linked Art](https://linked.art/model/actor/) as foundation.

## Group

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .

<https://example.org/community-1>
    a crm:E74_Group ;
    crm:P2_has_type <http://vocab.getty.edu/aat/300435377> ; # Community
    la:has_member <https://example.org/member-1> ;
    crm:P1_is_identified_by [
        a crm:E33_E41_Linguistic_Appellation ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300404670> ; # Name
        crm:P190_has_symbolic_content "Suriname"
    ] ;
    crm:P1_is_identified_by [
        a crm:E42_Identifier ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300404621> ; # Repository number
        crm:P190_has_symbolic_content "1234" # ID assigned by the data source
    ] .
```

## Member

```turtle
@prefix crm: <http://www.cidoc-crm.org/cidoc-crm/> .
@prefix la: <https://linked.art/ns/terms/> .

<https://example.org/member-1>
    a crm:E21_Person ;
    la:member_of <https://example.org/community-1> ;
    crm:P1_is_identified_by [
        a crm:E42_Identifier ;
        crm:P2_has_type <http://vocab.getty.edu/aat/300404621> ; # Repository number
        crm:P190_has_symbolic_content "1234" # ID assigned by the data source
    ] .
```
