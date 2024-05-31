# Research Guides: RDF model

RDF model for describing research guides. This is a draft version.

1. Explanation: https://github.com/colonial-heritage/research-guides-dev/tree/main?tab=readme-ov-file
1. Design: https://xd.adobe.com/view/0b89f99f-6624-494c-b10e-55001de41bf8-5eda/screen/79a31724-cf7e-45a5-98e9-a17de47cf892

## To discuss

1. In the Datahub we mostly model the metadata of/information about heritage objects and actors, such as persons. The research guides, however, seem to be of a different kind: we have to model the 'thing itself', not just its metadata. Correct?
1. What is the meaning of the hierarchy/the levels, also looking at the nature/type of the guides ('articles'/'documents'/'publications')? For example: is a 'level 3' guide a 'part of' a 'level 2' guide?
1. Should we model a 'top level' guide, to make clear how the various levels belong together? For example: they're all part of this top level?
1. How should we model the Dutch and English versions of a guide? For example: are these distinct documents (e.g. with their own IRIs)? Or these direct translations that can be combined into one document?
1. The IRIs in the source data (e.g. Wikidata, GeoNames, AAT) point to the human-readable pages, not to linked data resources. Intentionally?

### A 'top level' guide

If required!

```turtle
<https://guides.example.org/top-level>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Research Guides"@en, "Onderzoeksgidsen"@nl ;
  schema:description "Introduction"@en, "Introductie"@nl ;
  schema:text "What are the Research Guides?"@en, "Wat zijn de onderzoeksgidsen?"@nl ;
  schema:encodingFormat "text/markdown" ;
  schema:hasPart <https://guides.example.org/level-1a>, <https://guides.example.org/level-1b>, <https://guides.example.org/level-1c> .
```

## A 'level 1' guide

"The top level of the hierarchy, level 1, consists of general texts about writing provenance reports, the landscape of heritage institutions and other introductory materials".

Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau1/English/DoingResearch_20240425.yml

### To discuss

1. For simplicity, is it possible to add all questions and answers in this guide to one text field?
1. 'RelatedAides': how to model these?
1. 'content-type': can we use `schema:encodingFormat`? Can we use this predicate to make clear this is the encoding format of the information in `schema:text`?

### Example

```turtle
@prefix schema: <https://schema.org/> .

<https://guides.example.org/level-1a>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Doing research"@en, "Onderzoeken"@nl ;
  schema:abstract "What roadmap should you follow for doing (provenance) research and how do you get more information?"@en,
    "Welk stappenplan moet je volgen voor het doen van (herkomst)onderzoek en hoe kom je aan meer informatie?"@nl ;
  schema:text "Provenance research goes through several stages. Depending on the purpose of your research, you go through one or more steps. In practice, the research steps intertwine and can often be carried out simultaneously."@en,
    "Herkomstonderzoek verloopt in verschillende fasen. Afhankelijk van het doel van je onderzoek doorloop je één of meerdere stappen. In de praktijk lopen de onderzoeksstappen in elkaar over en kunnen ze vaak gelijktijdig worden uitgevoerd."@nl ;
  schema:encodingFormat "text/markdown" ;
  schema:isPartOf <https://guides.example.org/top-level> ;
  schema:hasPart <https://guides.example.org/level-2a> .
```

## A 'level 2' guide

"The second level of the hierarchy is made up of descriptions of broad topics, major actors and concepts in the colonial context, such as the Dutch colonial army".

Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau2/English/MilitaryAndNavy_20240417.yml

### To discuss

1. How should we model (the distinction between) primary and secondary sources? For example using `schema:additionalType`?

### Example

```turtle
@prefix schema: <https://schema.org/> .

<https://guides.example.org/level-2a>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Military and navy"@en, "Leger en Marine"@nl ;
  schema:abstract "Army and Navy personnel who operated in colonized territories collected objects in various ways during the colonial era."@en,
    "Leger- en marinepersoneel dat actief was in gekoloniseerde gebieden, verzamelde op verschillende manieren objecten tijdens het koloniale tijdperk."@nl ;
  schema:text "Dutch authority in the [Dutch East Indies](https://www.geonames.org/1643084/republic-of-indonesia.html), [Suriname](https://www.geonames.org/3382998/republic-of-suriname.html) and on the [Caribbean Islands](https://www.geonames.org/8505032/netherlands-antilles.html) relied heavily on the use of the military..."@en,
    "Het Nederlandse gezag in [Nederlands-Indië](https://www.geonames.org/1643084/republic-of-indonesia.html), [Suriname](https://www.geonames.org/3382998/republic-of-suriname.html) en op de [Caribische eilanden](https://www.geonames.org/8505032/netherlands-antilles.html) steunde in belangrijke mate op de inzet van het leger."@nl ;
  schema:encodingFormat "text/markdown" ;
  schema:contentLocation [
    a schema:Place ;
    schema:name "Netherlands Antilles"@en, "Antillen"@nl ;
    schema:sameAs <https://www.geonames.org/8505032/netherlands-antilles.html>
  ] ;
  schema:keywords [
    a schema:DefinedTerm ;
    schema:name "Midshipman"@en, "Adelborst"@nl ;
    schema:sameAs <https://www.wikidata.org/wiki/Q11141137>
  ] ;
  schema:isPartOf <https://guides.example.org/level-1a> ;
  schema:hasPart <https://guides.example.org/level-3a> ;
  schema:citation [
    a schema:CreativeWork ;
    schema:name "Regeeringsalmanak voor Nederlandsch-Indië"@en, "Regeeringsalmanak voor Nederlandsch-Indië"@nl ;
    schema:description "Via Delpher, the editions can be found by selecting the title"@en,
      "Edities van 1865 tot en met 1942 beschikbaar via Delpher en edities van 1865 tot en met 1912 beschikbaar via de digitale collecties van de Staatsbibliothek zu Berlin."@nl ;
    schema:url <https://www.delpher.nl/>
  ] .
```

## A 'level 3' guide

"On the third level, there is additional information about specific entities, actors and concepts related to and active in the colonial context".

Example: https://github.com/colonial-heritage/research-guides-dev/blob/main/niveau3/English/KunsthandelVanLier_20240507.yml

### To discuss

1. 'Name variations': how should we model this? These are variations of the name of the person, not the document
1. 'Period of activity': how should we model this? For example, as `schema:Event`? Or can we include this information in the `schema:text`?
1. 'Type of objects': how should we model this? As `schema:keywords`?

### Example

```turtle
@prefix schema: <https://schema.org/> .

<https://guides.example.org/level-3a>
  a schema:TextDigitalDocument ;
  schema:additionalType <http://vocab.getty.edu/aat/300027029> ; # Guideline
  schema:name "Royal Cabinet of Curiosities"@en, "Koninklijk Kabinet van Zeldzaamheden"@nl ;
  schema:abstract "The Royal Cabinet of Curiosities was established in 1816 by King William I. The collection consisted of a variety of objects, including many from colonized regions."@en,
    "Het Koninklijk Kabinet van Zeldzaamheden werd in 1816 opgericht door Koning Willem I. De collectie bestond uit allerlei voorwerpen, waaronder ook vele uit gekoloniseerde gebieden."@nl ;
  schema:text "Objects originating from the [Royal Cabinet of Curiosities](https://www.wikidata.org/wiki/Q34076860) are found, among others, at the [Wereldmuseum Leiden](https://www.wikidata.org/wiki/Q17339437)..."@en,
    "Voorwerpen die afkomstig zijn het [Koninklijk Kabinet van Zeldzaamheden](https://www.wikidata.org/wiki/Q34076860) bevinden in zich onder andere in het [Wereldmuseum Leiden](https://www.wikidata.org/wiki/Q17339437)..."@nl ;
  schema:encodingFormat "text/markdown" ;
  schema:contentLocation [
    a schema:Place ;
    schema:name "China"@en, "China"@nl ;
    schema:sameAs <https://www.geonames.org/1814991/people-s-republic-of-china.html>
  ] ;
  schema:keywords [
    a schema:DefinedTerm ;
    schema:name "Collection"@en, "Collectie"@nl ;
    schema:sameAs <http://vocab.getty.edu/aat/300025976>
  ] ;
  schema:isPartOf <https://guides.example.org/level-2a> ;
  schema:citation [
    a schema:CreativeWork ;
    schema:name "NL-HlmNHA 476 5"@en, "NL-HlmNHA 476 5"@nl ;
    schema:description "Concerns the inventory of the archive of the Royal Cabinet of Curiosities within the archive of the Rijksmuseum and its legal predecessors."@en,
      "Betreft de inventaris toegang van het archief van het Koninklijk Kabinet van Zeldzaamheden binnen het archief van het Rijksmuseum en rechtsvoorgangers."@nl ;
    schema:url <https://hdl.handle.net/21.12102/2422AD00C789442FAE99779C81E66552>
  ] .
```
