# Generic RDF model for publishing a nanopublication

RDF model for publishing an enrichment. This model is the foundation of specific models, e.g. publishing enrichments about [objects](../objects/rdf.md) or about [provenance events](../provenance-events/rdf.md). The generic model is an implementation of the [Nanopublications model](https://nanopub.net/).

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
    # The contribution of a user (see the specific models in other files)
    # <https://nanopublication.example/1> a <http://www.w3.org/ns/oa#Annotation>
    # <https://nanopublication.example/1> a <http://www.cidoc-crm.org/cidoc-crm/E13_Attribute_Assignment>
}

temp-nanopub-id:provenance {
    temp-nanopub-id:asserting-activity a prov:Activity .

    temp-nanopub-id:assertion
        prov:wasGeneratedBy temp-nanopub-id:asserting-activity ;
        prov:wasAttributedTo <https://n2t.net/ark:/27023/b062d006e928da1bfec6791bf75adf40> .

    <https://n2t.net/ark:/27023/b062d006e928da1bfec6791bf75adf40>
        rdfs:label "Name of person" ;
        prov:actedOnBehalfOf <https://n2t.net/ark:/27023/5eaead661201a601aa9b6b8109e13849> ;
        prov:qualifiedDelegation temp-nanopub-id:delegation .

    temp-nanopub-id:delegation
        a prov:Delegation ;
        prov:agent <https://n2t.net/ark:/27023/5eaead661201a601aa9b6b8109e13849> ;
        prov:hadActivity temp-nanopub-id:asserting-activity .

    <https://n2t.net/ark:/27023/5eaead661201a601aa9b6b8109e13849>
        rdfs:label "Name of community" .
}

temp-nanopub-id:pubinfo {
    # Tool used for creating the nanopublication
    <https://app.colonialcollections.nl/>
        a npx:SoftwareTool ;
        rdfs:label "Colonial Collections" .

    temp-nanopub-id:
        a cc:Nanopub, # Generic type, so that we can easily retrieve all nanopubs of Colonial Collections, regardless of their specific type
            cc:SomeSpecificTypeVersion1 ; # Specific type, including a version number, so that we can distinguish between multiple versions of the specific type
        dcterms:license <https://creativecommons.org/licenses/by/4.0/> ;
        npx:wasCreatedWith <https://app.colonialcollections.nl/> ;
        npx:introduces <https://nanopublication.example/1> . # Reference to the information contributed by a user (see the specific models in other files)
}
```
