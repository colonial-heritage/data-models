# Cultural heritage objects: conceptual model

Model for describing an enrichment of a piece of information of a cultural heritage object, contributed by a user. For example: a comment about the description or the translation of the title.

## Enrichment types

#### Text

An enrichment in the form of a text, e.g. a comment about existing information or a new text, such as a missing description.

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the enrichment|`https://example.org/enrichment-1`|
|Value|1|Content of the enrichment: a text|`A comment about the title`|
|Text direction|1|Direction of the text|`ltr`, `rtl`|
|Format|1|Format code of the text, according to the IANA media types|`text/plain`|
|Language|0 or 1|Language code of the text, according to ISO 639-1|`en-gb`|
|Source|0 or 1|Statement(s) about the source(s) the creator used when creating this enrichment, e.g. URLs of websites, book titles|`See webpage http://example.org/1`|
|About|1|Identifier of the information the enrichment is about|`https://example.org/object#title`|
|Creator|1|Identifier of the user who created the enrichment|`https://www.linkedin.com/in/person/`|
|Date created|1|Date on which the enrichment was created, in UTC|`2023-08-10T12:17:28`|
|License|1|Identifier (from Creative Commons) of the license of the enrichment|`https://creativecommons.org/licenses/by/4.0/`|

#### Reference

An enrichment in the form of a new reference. A reference can be e.g. a term from a terminology source or any other 'thing' that has an IRI.

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the enrichment|`https://example.org/enrichment-2`|
|Value|1|Content of the enrichment: the identifier of the reference|`http://vocab.getty.edu/aat/300011176`|
|Source|0 or more|Statement(s) about the source(s) the creator used when creating this enrichment, e.g. URLs of websites or titles of books|`See webpage http://example.org/2`|
|About|1|Identifier of the information the enrichment is about|`https://example.org/object#materials`|
|Creator|1|Identifier of the user who created the enrichment|`https://www.linkedin.com/in/person/`|
|Date created|1|Date on which the enrichment was created, in UTC|`2023-08-10T12:17:28`|
|License|1|Identifier (from Creative Commons) of the license of the enrichment|`https://creativecommons.org/licenses/by/4.0/`|

#### Date

An enrichment in the form of a new date.

|Name|Cardinality|Description|Example|
|-|-|-|-|
|ID|1|Identifier of the enrichment|`https://example.org/enrichment-3`|
|Value|1|Content of the enrichment: a date according to [EDTF](https://www.loc.gov/standards/datetime/)|`1901`, `1901?`, `1900/1905`|
|Source|0 or more|Statement(s) about the source(s) the creator used when creating this enrichment, e.g. URLs of websites or titles of books|`See webpage http://example.org/3`|
|About|1|Identifier of the information the enrichment is about|`https://example.org/object#date-created`|
|Creator|1|Identifier of the user who created the enrichment|`https://www.linkedin.com/in/person/`|
|Date created|1|Date on which the enrichment was created, in UTC|`2023-08-10T12:17:28`|
|License|1|Identifier (from Creative Commons) of the license of the enrichment|`https://creativecommons.org/licenses/by/4.0/`|

## TBD

1. Do we need more enrichment types? For example: is there a need to have a separate type for 'Dimensions'? Or are these of type 'text'?
