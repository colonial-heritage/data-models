# Research Guides: RDF model

RDF model for describing research guides. This is a draft version.

Explanation: https://github.com/colonial-heritage/research-guides-dev/tree/main?tab=readme-ov-file
Design: https://xd.adobe.com/view/0b89f99f-6624-494c-b10e-55001de41bf8-5eda/screen/79a31724-cf7e-45a5-98e9-a17de47cf892

## To discuss

1. What is the meaning of the hierarchy/the tiers, also looking at the nature/type of the guides ('documents'/'publications')? For example: is a 'tier 3' guide a 'part of' a 'tier 2' guide?
1. How should we model (the distinction between) primary and secondary sources? For example using `schema:additionalType`?

## A 'tier 2' guide

"The second tier of the hierarchy is made up of descriptions of broad topics, major actors and concepts in the colonial context, such as the Dutch colonial army". Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau2/English/MilitaryAndNavy_20240417.yml

```turtle
@prefix schema: <https://schema.org/> .

<https://example.org/guide-level-2>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Military and navy" ;
  schema:inLanguage "en" ;
  schema:creator <https://www.niod.nl/> ;
  schema:publisher <https://www.niod.nl/> ;
  schema:dateCreated "2024-05-28" ;
  schema:text "Dutch authority in the [Dutch East Indies](https://www.geonames.org/1643084/republic-of-indonesia.html), [Suriname](https://www.geonames.org/3382998/republic-of-suriname.html) and on the [Caribbean Islands](https://www.geonames.org/8505032/netherlands-antilles.html) relied heavily on the use of the military" ;
  schema:encodingFormat "text/markdown" ; # TBD: correct? Can we use this predicate to make clear this is the encoding format of the information in `schema:text`?
  schema:contentLocation <https://sws.geonames.org/8505032/> ;
  schema:keywords <http://www.wikidata.org/entity/Q11141137> ;
  schema:citation [
    a schema:CreativeWork ;
    schema:name "Regeeringsalmanak voor Nederlandsch-Indië" ;
    schema:description "Via Delpher, the editions can be found by selecting the title" ;
    schema:url <https://www.delpher.nl/>
  ] ;
  schema:isPartOf <https://example.org/guide-level-1> ;
  schema:hasPart <https://example.org/guide-level-3a>, <https://example.org/guide-level-3b> .
```
