# Guides: RDF model

RDF model for describing a guide. This is a draft version.

Explanation: https://github.com/colonial-heritage/research-guides-dev/tree/main?tab=readme-ov-file
Design: https://xd.adobe.com/view/0b89f99f-6624-494c-b10e-55001de41bf8-5eda/screen/79a31724-cf7e-45a5-98e9-a17de47cf892

## A 'Level 2' guide

Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau2/English/MilitaryAndNavy_20240417.yml

```turtle
@prefix schema: <https://schema.org/> .

<https://example.org/guide-level-2>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Military and navy" ;
  schema:inLanguage "en" ;
  schema:creator <https://www.niod.nl/> ;
  schema:text "Dutch authority in the [Dutch East Indies](https://www.geonames.org/1643084/republic-of-indonesia.html), [Suriname](https://www.geonames.org/3382998/republic-of-suriname.html) and on the [Caribbean Islands](https://www.geonames.org/8505032/netherlands-antilles.html) relied heavily on the use of the military" ;
  schema:encodingFormat "text/markdown" ;
  schema:contentLocation <https://sws.geonames.org/8505032/> ;
  schema:keywords <http://www.wikidata.org/entity/Q11141137> ;
  schema:citation [
    # TBD: how to model primary versus secondary sources?
    a schema:CreativeWork ;
    schema:name "Regeeringsalmanak voor Nederlandsch-Indië" ;
    schema:description "Via Delpher, the editions can be found by selecting the title" ;
    schema:url <https://www.delpher.nl/>
  ] ;
  schema:isPartOf <https://example.org/guide-level-1> ;
  schema:hasPart <https://example.org/guide-level-3a>, <https://example.org/guide-level-3b> .
```
