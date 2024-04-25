# Communities: conceptual model

Model for describing a community and its members. The model uses [CIDOC-CRM](https://www.cidoc-crm.org/) as foundation.

## Entities

### Group

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the community|`https://example.org/community-1`|
|Data Source ID|1|Identifier of the community in the data source, for traceability|`1234`|
|Type|1|Identifier (from the AAT) of the type of the group|`http://vocab.getty.edu/aat/300435377`|
|Name|1|Name of the community|`Suriname`|
|Member|0 or more|ID of the member|`https://example.org/member-1`|

### Member

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the member|`https://example.org/member-1`|
|Data Source ID|1|Identifier of the member in the data source, for traceability|`1234`|
|Group|0 or more|Identifier of the group of which this actor is a member|`https://example.org/community-1`|

Note: we do not store the name of the members, for privacy reasons.
