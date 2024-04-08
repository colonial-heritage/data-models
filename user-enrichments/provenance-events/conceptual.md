# Provenance events: conceptual model

Model for describing a provenance event contributed by a user.

## Entities

### Provenance event

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the enrichment|`https://example.org/prov-event-4`|
|Type|1|Type of the event|`Acquisition` (for transfer of legal ownership), `Transfer of Custody` (for transfer of physical custody or the legal responsibility for physical custody)|
|Classification|0 or 1|Identifier (from the AAT) of the classification of the type of the event|`http://vocab.getty.edu/aat/300417637`|
|Qualifier|0 or 1|Identifier (from the AAT) of the qualifier of the classification|`http://vocab.getty.edu/aat/300435722`|
|Name|0 or 1|Name of the event|`Acquisition of object from seller`, `Theft of object from owner`|
|Description|0 or 1|Description of the event|-|
|Transferred from|0 or 1|Identifier (from Wikidata or from an authority file of the data provider) of the actor who owned or held the object|See [the model](../actors/conceptual.md)|
|Transferred to|0 or 1|Identifier (from Wikidata or from an authority file of the data provider) of the actor who received the object|See [the model](../actors/conceptual.md)|
|Location|0 or 1|Identifier (from GeoNames) of the location of the event|`https://sws.geonames.org/1642911/`|
|Date|0 or 1|Date of the event|`1887`, `1887-06-05`, `1887-1889`|
|Source|0 or 1|Statement(s) about the source(s) the creator used when creating this enrichment, e.g. URLs of websites or titles of books|`See webpage http://example.org/3`|
|About|1|Identifier of the object the enrichment is about|`https://example.org/object`|
|Creator|1|Identifier (from e.g. LinkedIn, Facebook) of the user who created the enrichment|`https://www.linkedin.com/in/person/`|
|Date created|1|Date on which the enrichment was created, in UTC|`2024-04-08T12:17:28`|
|License|1|Identifier (from Creative Commons) of the license of the enrichment|`https://creativecommons.org/licenses/by/4.0/`|
