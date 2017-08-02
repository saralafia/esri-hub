# Esri-Hub Vocabulary
**Goal**: Take a tag or search term matching a theme or place and enhance it by returning its synonyms, its translation, its broader and narrower concepts, and its related concepts. For example, a search for "disease" should also return "health" (broader), "patología" (translation), "medicine" (related), etc.

**Motivation**: Data users and contributors often use different terms to describe similar concepts, such as "health" and "wellness". Semantic search allows for exploration and discovery of relationships among concepts that were previously unknown. It also supports both query expansion and refinement. 

**Implementation**: Datasets in ArcGIS Online have contributor-generated keywords. As dataset metadata are harvested, the keywords are looked-up against this service. Matching keywords are added to the item description as "extended keywords". These are used to index items and are hidden from the user. 

## Overview
The Esri-Hub vocabulary models [ArcGIS Hub](<https://hub.arcgis.com/pages/open-data>) **Items**, **Users**, and **Groups**. The vocabulary maps existing ArcGIS Online [entities](<http://resources.arcgis.com/en/help/arcgis-rest-api/#/Working_with_users_groups_and_items/02r3000000mt000000/>) (Content and Community - Users, Groups, Items) to their [qualities](<http://resources.arcgis.com/en/help/arcgis-rest-api%20%20/index.html#//02r3000000m9000000>) (Tags - Place, Theme). The **Category** tags expand the current six Hub category themes (Healthy, Livable, Prosperous, Safe, Sustainable, Well-Run), which are mapped to [Library of Congress Subject Heading](<http://id.loc.gov/>) concepts and [WordNet] (<wordnet-rdf.princeton.edu>) synonyms. The **Place** tags expand a place hierarchy inhereted from [DBPedia](<https://dbpedia.org/ontology/>).
![Model overview](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVVFRmaFhzUVQ2YWs)
The hub:Item associates hub:Users and hub:Groups. hub:Items have a categories:ThemeContext and a places:PlaceContext. These are imported from separate vocabularies also found in this repository. The models are generated in [Protégé](<http://protege.stanford.edu/>) software and exported as vocabularies in [Turtle syntax](<https://www.w3.org/TeamSubmission/turtle/>), which capture relations among modeled concepts as triple-statements. These vocabulary files are then loaded into a [Fuseki](<https://jena.apache.org/download/>) triplestore, which is queried through [SPARQL](<https://www.w3.org/TR/rdf-sparql-query/>) queries hosted at a public endpoint. 

## Getting Started
### Vocabularies
To view or edit the following vocabularies, open them with any text editor or load them into Protégé: 1) **Esri-Hub** base, 2) **Categories** import, 3) **Places** import, 4) [the **USGS** Thesaurus](<https://www2.usgs.gov/science/about/>), and 5) [the **DTIC** Thesaurus](<http://www.dtic.mil/dtic/services/dtic_thesaurus/download.html>). To load a vocabulary in Protégé, File > Open (i.e. "esri-hub.ttl"). Files can be loaded locally or from a URI if the vocabulary is published online.

1. The Esri-Hub base vocabulary uses Classes and Properties to model entities in [OWL/RDF](<https://www.w3.org/TR/owl-ref/>). It imports the Categories and Places vocabularies as well as other standard vocabularies like [SKOS](<https://www.w3.org/TR/skos-reference/>).
![Esri-Hub](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVWlR6RzJWNi00SWM)
2. To import a term from an ontology contained in a document loaded on the web, go to Active Ontology tab > Import and follow the steps to point to the term's URI.
![Import](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVQ1ZOc0pLXzlMYUE)
![LOC](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVN3RxN1duOW1zRHc)
3. Classes are the nodes of the graph in the data model.
![Classes](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVdlNoZ0JmRF9NLWs)
4. Object properties are the edges of the graph in the data model.
![Object Properties](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVNHA5aWVGaXpqX1U)
5. Data properties are the data types that the node value takes.
![Data overview](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVSEo0aUlHM2dSR2s)
6. The Categories and Places vocabularies use Individuals to model concepts in SKOS. The attributes of the concepts are stored as annotations. Esri Hub concepts are asserted to be OWL:sameAS to equivalent concepts in Library of Congress Subject Headings or WordNet.
![Individuals overview](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVYmVpeExsM0tPU0k)
7. To save the vocabulary or export it, go to File > Save As and choose the serialization. Fuseki accepts RDF/XML, TTL, and JSON-LD at present.

### Queries
To query vocabularies using SPARQL, set up a local Fuseki server and upload the vocabulary of your choice or visit the [Fuseki server endpoint] (<http://34.229.180.217:8080/fuseki/dataset.html?tab=upload&ds=/category>) where the vocabularies are hosted in separate graphs. The "queries.txt" and "generic queries.txt" files contain example SPARQL queries to run against the vocabulary. The "categories queries.txt" and "places queries.txt" files contains more specific queries.
![Fuseki SPARQL](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVUkpfeDlpbXlLNmc)

### Demos
To explore the vocabularies by entering a search term, visit the [Term Expander Express App](<http://34.229.180.217:7777/>), created by Pranav Kulkarni. A set of some suggested search terms can be found in "term expander.txt". Additional search terms related to demo site [GIS Nation Geoplatform](<https://gisnation-usnsdi.opendata.arcgis.com/>) are found in "use cases.txt".
![Term Expander](https://drive.google.com/uc?export=view&id=0B4TqO-vz3GvVa2NxNzhKYU9LUkE)

## Next Steps
### Data Discovery
When users are browsing for a topic, they can explore topic clusters instead of page ranked results. Clusters can be defined by any edge relationship in the vocabulary, such as broader/narrower, related, synonymous, etc. Distinguishing search and discovery from retrieval tasks will improve search usability. 
### Tag Generation
When users contribute datasets, the words they use to describe them (i.e. title, description) can recommend tags. Eventually, users (such as agencies) should be able to import their own controlled vocabularies into a graph and use their preferred terms in addition to the provided vocabularies.
### Automated Dereferencing
Vocabulary terms for places can be generated automatically from the following RDF data dumps: [GNIS-LD](<https://datahub.io/dataset/geographic-names-information-system-gnis>), [GeoNames](<http://www.geonames.org/ontology/documentation.html>), and [DBPedia](<http://wiki.dbpedia.org/services-resources/datasets/dbpedia-datasets>). API lookups from the following services can also be used to generate thematic terms programmatically: [Library of Congress](<http://id.loc.gov/techcenter/searching.html>) and [WordNet](<https://wordnet.princeton.edu/wordnet/frequently-asked-questions/for-application-developer/>). 