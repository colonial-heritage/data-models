# Research Guides: RDF model

RDF model for describing research guides. This is a draft version.

Explanation: https://github.com/colonial-heritage/research-guides-dev/tree/main?tab=readme-ov-file
Design: https://xd.adobe.com/view/0b89f99f-6624-494c-b10e-55001de41bf8-5eda/screen/79a31724-cf7e-45a5-98e9-a17de47cf892

## To discuss

1. Should we model a 'top level' guide, to make clear how the various tiers belong together? For example: they're all part of this top level?
1. What is the meaning of the hierarchy/the tiers, also looking at the nature/type of the guides ('documents'/'publications')? For example: is a 'tier 3' guide a 'part of' a 'tier 2' guide?
1. How should we model the Dutch and English versions of a guide? For example: are these distinct documents (e.g. with their own IRIs)? Or these direct translations that can be combined into one document?
1. How should we model (the distinction between) primary and secondary sources? For example using `schema:additionalType`?

## A 'tier 2' guide

"The second tier of the hierarchy is made up of descriptions of broad topics, major actors and concepts in the colonial context, such as the Dutch colonial army". Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau2/English/MilitaryAndNavy_20240417.yml

```turtle
@prefix schema: <https://schema.org/> .

<https://example.org/guide-tier-2>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Military and navy" ;
  schema:inLanguage "en" ;
  schema:creator <https://www.niod.nl/> ;
  schema:publisher <https://www.niod.nl/> ;
  schema:dateCreated "2024-05-28" ;
  schema:abstract "Army and Navy personnel who operated in colonized territories collected objects in various ways during the colonial era." ;
  schema:text "Dutch authority in the [Dutch East Indies](https://www.geonames.org/1643084/republic-of-indonesia.html), [Suriname](https://www.geonames.org/3382998/republic-of-suriname.html) and on the [Caribbean Islands](https://www.geonames.org/8505032/netherlands-antilles.html) relied heavily on the use of the military..." ;
  schema:encodingFormat "text/markdown" ; # TBD: correct? Can we use this predicate to make clear this is the encoding format of the information in `schema:text`?
  schema:contentLocation <https://sws.geonames.org/8505032/> ;
  schema:keywords <http://www.wikidata.org/entity/Q11141137> ;
  schema:citation [
    a schema:CreativeWork ;
    schema:name "Regeeringsalmanak voor Nederlandsch-Indië" ;
    schema:description "Via Delpher, the editions can be found by selecting the title" ;
    schema:url <https://www.delpher.nl/>
  ] ;
  schema:isPartOf <https://example.org/guide-tier-1> ;
  schema:hasPart <https://example.org/guide-tier-3a>, <https://example.org/guide-tier-3b> .
```

## A 'tier 3' guide

"On the third level, there is additional information about specific entities, actors and concepts related to and active in the colonial context". Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau3/English/KunsthandelVanLier_20240507.yml

### To discuss

1. 'Name variations': how should we model this? These are variations of the name of the person, not the document
1. 'Period of activity': how should we model this? For example, as `schema:Event`? Or can we include this information in the `schema:text`?
1. 'Type of objects': how should we model this?

```turtle
@prefix schema: <https://schema.org/> .

<https://example.org/guide-tier-3a>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029>, # Guideline
    <http://vocab.getty.edu/aat/300080102> ; # Biography
  schema:name "Kunsthandel Van Lier" ;
  schema:inLanguage "en" ;
  schema:creator <https://www.niod.nl/> ;
  schema:publisher <https://www.niod.nl/> ;
  schema:dateCreated "2024-05-28" ;
  schema:abstract "Kunsthandel Van Lier dealt in artifacts and ethnographic objects from, among other regions, Africa, Asia and North America." ;
  schema:text "[Carel van Lier]](https://www.wikidata.org/wiki/Q2531642) (1897-1945) started a gallery in [Laren](https://www.geonames.org/2751874/laren.html) in 1924..." ;
  schema:encodingFormat "text/markdown" ; # TBD: correct? Can we use this predicate to make clear this is the encoding format of the information in `schema:text`?
  schema:contentLocation <https://sws.geonames.org/8505032/> ;
  schema:keywords <http://www.wikidata.org/entity/Q11141137> ;
  schema:about <http://www.wikidata.org/entity/Q87665942>, <https://hdl.handle.net/20.500.11840/pi57937> ;
  schema:citation [
    a schema:CreativeWork ;
    schema:name "RKD – Nederlands Instituut voor Kunstgeschiedenis / Carel van Lier NL-HaRKD.0108" ;
    schema:description "Letters and postcards, mainly from artists, and other papers covering the period 1927-1948" ;
    schema:url <https://rkd.nl/nl/explore/collections/108>
  ] ;
  schema:isPartOf <https://example.org/guide-tier-2> .
```