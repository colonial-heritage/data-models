# Actors: conceptual model

Model for describing an actor, e.g. a person or an organization.

## Entities

### Person

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the actor|`https://example.org/person`|
|Type|1|Type of the actor|`Person`|
|Name|0 or 1|Name of the actor|`John Doe`|
|First name|0 or 1|First name of the actor|`John`|
|Last name|0 or 1|Last name of the actor|`Doe`|
|Birth date|0 or 1|Date when the actor was born. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Birth place|0 or 1|Identifier (from GeoNames or from an authority file of the data provider) of the location where the actor was born. Could be a specific or generic place|`https://sws.geonames.org/1642911/`|
|Death date|0 or 1|Date when the actor died. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Death place|0 or 1|Identifier (from GeoNames or from an authority file of the data provider) of the location where the actor died. Could be a specific or generic place|`https://sws.geonames.org/1642911/`|
|Part of dataset|1|Identifier of the dataset to which the (information about the) actor belongs|-|

### Organization

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the actor|`https://example.org/organization`|
|Type|1|Type of the actor|`Organization`|
|Name|0 or 1|Name of the actor|`Museum`|
|Part of dataset|1|Identifier of the dataset to which the (information about the) actor belongs|-|
