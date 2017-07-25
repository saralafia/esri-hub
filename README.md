## Vocabulary
The Esri-Hub vocabulary models Items, Users, and Groups (Content and Community) from the ArcGIS REST API documentation. The vocabulary maps existing ArcGIS Online Entities (Users, Groups, and Items -  Applications, Datafiles, Layers, Maps, and Tools) to their Qualities (Tags - Time, Place, Theme). The Category tags are mapped across existing standards including INSPIRE, FGDC, and ISO19115. The Theme tags represent the current six Hub categories (Healthy, Livable, Prosperous, Safe, Sustainable, Well-Run) mapped to Library of Congress Subject Headings concepts and WordNet synsets.

## Model
The Hub:Item is the central object in the RDF model. Hub:Users and Hub:Groups are associated through Items. The RDF model of the Item is constructed from from this set of a Title, a Description, Tag(s), an Extent, and a Source. In the case that the Item has associated metadata such as ISO 19115 metadata, fields from the metadata, such as controlled keywords for time, place, and theme, are also referenced.

### Time
- transaction time (time of Item publication, time of Item last update); time:hasDateTimeDescription
- interval time (time of Item description); time:hasTemporalDuration

### Place
- extent (bounding box coordinates in WGS84 of Item); geosparql:hasGeometry
- place keyword (place of description of Item from keywords); dbo:location

### Theme
- category keyword (category of Item description from ISO 19115); skos:hasTopConcept
- concept keyword (category of Item description from keywords); skos:isInScheme

## Queries
The queries demonstrate some of the benefits of encoding existing Item, Group, and User descriptions in a RDF model. Semantic benefits include hierarchical and terminological inference for hub:Item time, place, and theme. This includes both hierarchical reasoning on parent/child class relationships for hub:Items and terminological expansion for themes across synonymous concepts. For example, an Item tagged with the top concept "ISO_transportation" will also be discoverable from an "INSPIRE_transportation" tag, as these classes are conceptually equivalent. Also, an Item tagged with a location of "city" will be discoverable as part of its greater "metropolitan area", due to hierarchical inference.

## Getting Started
To query the sample data, set up a local Fuseki server (<https://jena.apache.org/download/>). Load both "esri-hub.ttl" (the working ontology generated in Protégé) and "sample-data.ttl" (manually annotated descriptions for Items, Users, and Groups) into Fuseki. The "queries.txt" file contains sample SPARQL queries to run against the vocabulary.
