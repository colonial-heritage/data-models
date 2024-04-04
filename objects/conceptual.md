# Cultural heritage objects: conceptual model

The model uses the [Object ID standard](https://icom.museum/en/resources/standards-guidelines/objectid/) as foundation.

## Status

Draft

## Entities

### Cultural Heritage Object (CHO)

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the object|-|
|Type|1 or more|Type of the object|`Photograph`|
|Subject|0 or more|Subject of the object|`Feast`|
|Name|0 or 1|Name or title of the object|`Fragment van een figuur`|
|Description|0 or 1|Name of the object|`Staande figuur, mogelijk een figuur met dwerggroei voorstellend. Fragment afkomstig van kleine figurines uit graven.`|
|Inscription or marking|0 or more|Inscription or marking on the object|-|
|Creator/maker|0 or more|Reference to an actor (e.g. a person or group) who created the object|See [the model](../actors/conceptual.md)|
|Date created|0 or more|Date when the object was made. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Location of creation|0 or more|Location where the object was made. Could be a specific or generic place|`Jakarta`, `Indonesia`, `Asia`|
|Material|0 or more|Material of the object|`Wood`|
|Technique|0 or more|Technique used when creating the object|`Albumen process`|
|Dimension|0 or 1|Width, height, depth of the object|-|
|Digital object|0 or more|Reference to a digital object|-|
|Transfer of ownership or custody|0 or more|Reference to a provenance event|See [the model](../provenance/conceptual.md)|
|Part of dataset|1|Reference to the dataset to which the (information about the) object belongs|-|

### Digital Object

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the digital object|-|
|Type|1 or more|Type of the object|`Digital image`|
|Name|0 or 1|Name or title of the object|`Fragment van een figuur`|
|URL|1|URL of the digital object|`https://example.org/123.jpg`|
|Right|0 or 1|Reference to the right of the digital object|-|
|Copyright statement|0 or 1|Copyright statement about the digital object|-|

### Right

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the right|-|
|Type|1|Type of the right|`https://creativecommons.org/public-domain/cc0/`|
|Name|0 or 1|Name of the right|`Public Domain`|
