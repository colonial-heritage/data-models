# Actors: conceptual model

## Status

Draft

## Entities

### Person

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the actor|-|
|Type|1|Type of the actor|`Person`|
|Name|0 or 1|Name of the actor|`John Doe`|
|First name|0 or 1|First name of the actor|`John`|
|Last name|0 or 1|Last name of the actor|`Doe`|
|Birth date|0 or 1|Date when the actor was born. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Birth place|0 or 1|Location where the actor was born. Could be a specific or generic place|`Jakarta`, `Indonesia`, `Asia`|
|Death date|0 or 1|Date when the actor died. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Death place|0 or 1|Location where the actor died. Could be a specific or generic place|`Jakarta`, `Indonesia`, `Asia`|
|Part of dataset|1|Reference to the dataset to which the (information about the) actor belongs|-|

### Organization

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the actor|-|
|Type|1|Type of the actor|`Organization`|
|Name|0 or 1|Name of the actor|`Museum`|
|Part of dataset|1|Reference to the dataset to which the (information about the) actor belongs|-|
