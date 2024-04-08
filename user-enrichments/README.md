# User enrichments

The Datahub of Colonial Collections enables users to add their own enrichments to the information from data providers. An enrichment (also known as an 'annotation') is additional information about an entity, e.g. (the metadata of) a cultural heritage object or an actor.

## Design principles

1. An enrichment can be anything. For example: it could be a comment about a heritage object as a whole or a translation of a specific attribute (e.g. the title)
1. The content of an enrichment is intentionally undefined/uncategorized. For example: it could be a question or a truth claim
1. An enrichment is created by a specific user. This user is the owner of and responsible for the enrichment
1. An enrichment has a specific license, to make clear what others are allowed to do with it
1. An enrichment is never a deletion of original information, but it can be a correction; the provider of the original information can then decide what to do with it

## Contents

1. Cultural heritage objects
    1. [Conceptual model](./objects/conceptual.md)
    1. [RDF model](./objects/rdf.md)
1. Provenance events
    1. [Conceptual model](./provenance-events/conceptual.md)
    1. [RDF model](./provenance-events/rdf.md)
