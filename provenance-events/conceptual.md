# Provenance events: conceptual model

Model for describing a provenance event. The aim of the model is to track the events in which a cultural heritage object is created or discovered, transferred between owners or custodians, until it is lost, destroyed or in its present location. The model uses [CIDOC-CRM](https://www.cidoc-crm.org/) as foundation.

## Entities

### Provenance Event

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the event|`https://example.org/prov-event-2`|
|Type|1|Type of the event|`Acquisition` (for transfer of legal ownership), `Transfer of Custody` (for transfer of physical custody or the legal responsibility for physical custody)|
|Classification|0 or 1|Identifier (from the AAT) of the classification of the type of the event|`http://vocab.getty.edu/aat/300417637`|
|Qualifier|0 or 1|Identifier (from the AAT) of the qualifier of the classification|`http://vocab.getty.edu/aat/300435722`|
|Name|0 or 1|Name of the event|`Acquisition of object from seller`, `Theft of object from owner`|
|Description|0 or 1|Description of the event|-|
|Transferred from|0 or 1|Identifier (from Wikidata or from an authority file of the data provider) of the actor who owned or held the object|See [the model](../actors/conceptual.md)|
|Transferred to|0 or 1|Identifier (from Wikidata or from an authority file of the data provider) of the actor who received the object|See [the model](../actors/conceptual.md)|
|Location|0 or 1|Identifier (from GeoNames) of the location of the event|`https://sws.geonames.org/1642911/`|
|Date|0 or 1|Date of the event|`1887`, `1887-06-05`, `1887-1889`|
|Source|0 or 1|Sources on which the provenance information is based, e.g. URLs of websites, book titles|`See webpage http://example.org/3`|
|Starts after|0 or 1|Identifier to another provenance event, earlier in time|`https://example.org/prov-event-1`|
|Ends before|0 or 1|Identifier to another provenance event, later in time|`https://example.org/prov-event-3`|
|Related to|0 or more|Identifier (from Wikidata) of an event to which the provenance event is (somehow) related|`http://www.wikidata.org/entity/Q2201391` ("Dutch intervention in Lombok and Karangasem")|

## TBD

1. Do we know - from the source data - whether a provenance event was a transfer of _legal_ ownership? Or is this unknown and do we only know that an object has been 'moved' to another actor?
1. NMVW's data contains the names and roles of the persons involved in provenance events. For example: the curator that bought an object. Is it useful to register this? Or are only the organisations to which the persons belonged important? -> For now we'll register this information in the 'Description' attribute
1. NMVW primarily registers the transfers of custody. That's because the museum is not the legal owner of objects - that's the Dutch government.
1. NMVW registers provenance information from a data provider's perspective, not from an object's perspective. For example: if an object was handed over to a museum in Indonesia, the museum registers this as a 'deaccession' event. But from an object's perspective this is not a deaccession - it lives on at a different location, in the hands of a new owner and custodian.
1. NMVW registers 'administrative' changes as provenance events, e.g. if an object received a new object number. But the owner or the custodian did not change. Should we expose this information? See also: https://linked.art/model/provenance/curation/.
1. NMVW sometimes 'discovers' objects in its collection that it wasn't aware of. Should we register this as a separate provenance event? Or is this irrelevant because the owner and custodian did not change?
