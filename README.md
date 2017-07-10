## Getting Started
To query the sample data, set up a local Fuseki server instance. Load both "esri-hub.ttl" (draft ontology generated in Protégé) and "sample-data.ttl" (annotated dataset descriptions) into Fuseki. The "queries.txt" file contains sample SPARQL queries to run against the vocabulary using Fuseki.

## Vocabulary
The Esri-Hub vocabulary models Items, Users, and Groups (Content and Community) from the ArcGIS REST API documentation. The goal of the vocabulary is to formalize mappings between existing ArcGIS Online Entities (Users, Groups, and Items -  Applications, Datafiles, Layers, Maps, and Tools) and their Qualities (Tags - Category, Theme, Locality, etc). Both Community and Content resources can be tagged with instances of the Tags class. The Category tags are mapped across existing schema including INSPIRE, FGDC, and ISO19115 standards. The Theme tags are derived from the existing Hub categories.

## Queries
The queries demonstrate some of the semantic benefits of encoding descriptions of Items, Groups, and Users with the Esri-Hub and other existing vocabularies. Two main benefits are terminological (thematic) and hierarchical (geographic) inference. For example, an Item tagged with an ISO_transportation theme will also be discoverable from an INSPIRE_transportation theme Item tag, as these classes are equivalent. Also, an Item tagged with a locality of "Washington D.C." will also be discoverable as part of the Delaware-Maryland-Virginia greater metropolitan area, due to inference.
