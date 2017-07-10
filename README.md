#Getting Started
To query the sample data, set up a local Fuseki server instance. Load both "esri-hub.ttl" and "sample-data.ttl" files into the triple store. The "queries.txt" file contains sample SPARQL queries to run against the vocabulary using Fuseki.

## Vocabulary
The Esri-Hub vocabulary models Content (Items) and Community (Users, Groups) in the ArcGIS REST API documentation. The goal of the vocabulary is to formalize mappings between existing ArcGIS Online Entities (Users, Groups, and Items: Applications, Datafiles, Layers, Maps, and Tools) and their Qualities (Tags: Theme, Locality, Temporality). Both Community and Content resources can be tagged with instances of the Tags class. The Theme tags are mapped across existing schema including INSPIRE, FGDC, and ISO19115 standards.

## Triples
The triples are manually annotated descriptions of Items, Groups, and Users from Hub. The descriptions use both the Esri-Hub vocabulary and existing published vocabularies.

## Queries
The queries demonstrate some of the semantic benefits of encoding descriptions of Items, Groups, and Users with vocabularies. The two main benefits are terminological (thematic) and hierarchical (geographic) inference. For example, an Item tagged with an ISO_transportation theme will also be discoverable as an INSPIRE_transportation theme Item, as these classes are equivalent. Also, an Item tagged with a locality of "Washington D.C." wills also be discoverable as part of the Delaware-Maryland-Virginia greater metropolitan area due to inference.

# Case Study (under development)
In the case of the Vision Zero initiative, there is great incentive to normalize schema of collision data discoverable through ArcGIS Online by different municipalities. For example, more than five municipalities such as Los Angeles, Washington D.C., etc. contribute datasets to track Vision Zero initiatives. The datasets share similar attribute fields, such as "Date (Time)", "Fatality (Number)", "Route (Text)", etc. but may be named differently. Each dataset is an instance of the Federal Model Minimum Uniform Crash Criteria (MMUCC) schema, which specifies required fields. By formalizing a model in the Esri-Hub vocabulary, crash datasets used in tracking Vision Zero initiatives can be made interoperable across municipalities.
