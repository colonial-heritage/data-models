# Cultural heritage objects: conceptual model

Model for describing a cultural heritage object (CHO). The model uses the [Object ID standard](https://icom.museum/en/resources/standards-guidelines/objectid/) as foundation.

## Entities

### Cultural Heritage Object

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the object|`https://example.org/object`|
|Type|0 or more|Identifier (from the Wereldmuseum Thesaurus) of the type of the object|`https://hdl.handle.net/20.500.11840/termmaster1397`|
|Subject|0 or more|Identifier (from the AAT) of the subject of the object|`http://vocab.getty.edu/aat/300152441`|
|Name|0 or 1|Name or title of the object|`Fragment of a figure`|
|Description|0 or 1|Name of the object|-|
|Inscription or marking|0 or more|Inscription or marking on the object|-|
|Creator/maker|0 or more|Identifier (from Wikidata or from an authority file of the data provider) of the actor who created the object|See [the model](../actors/conceptual.md)|
|Date created|0 or more|Date when the object was made. Could be an exact date or a range|`1708-01-02`, `1708`, `1700-1800`|
|Location of creation|0 or more|Identifier (from GeoNames) of the location where the object was made. Could be a specific or generic place|`https://sws.geonames.org/1642911/`|
|Material|0 or more|Identifier (from the Wereldmuseum Thesaurus) of the material of the object|`https://hdl.handle.net/20.500.11840/termmaster26637`|
|Technique|0 or more|Identifier (from the Wereldmuseum Thesaurus) of the technique used when creating the object|`https://hdl.handle.net/20.500.11840/termmaster26171`|
|Dimension|0 or 1|Width, height, depth of the object|-|
|Digital object|0 or more|Identifier of a digital object|`https://example.org/image`|
|Transfer of ownership or custody|0 or more|Identifier of a provenance event|See [the model](../provenance-events/conceptual.md)|
|Part of dataset|1|Identifier of the dataset to which the (information about the) object belongs|`https://example.org/dataset`|

### Digital Object

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the digital object|`https://example.org/image`|
|Type|1 or more|Type of the object|`Digital image`|
|Name|0 or 1|Name or title of the object|`Fragment of a figure`|
|URL|1|URL of the digital object|`https://example.org/123.jpg`|
|Right|0 or 1|Reference to the right of the digital object|`https://example.org/right`|
|Copyright statement|0 or 1|Copyright statement about the digital object|-|

### Right

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the right|`https://example.org/right`|
|Type|1|Type of the right|`https://creativecommons.org/public-domain/cc0/`|
|Name|0 or 1|Name of the right|`Public Domain`|
