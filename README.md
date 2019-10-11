# IoT Device Management Ontology (iot-dm)

**Ontology IRI: http://purl.org/net/iot-dm**

## Abstract

**Keywords**: *Internet of Things, IoT, Device Management, Ontology*

To ensure reliable and secure long-term operations of IoT based solutions, manufacturers or operators in most cases need an efficient way to manage and administer their IoT devices on a large scale. Today there are multiple vendors addressing this need with a sort of software products described by the term 'IoT Device Management' or more generic by the term 'IoT Platform'. Looking into this domain a bit closer, it becomes evident that the actual functional scope and specific features of such products differ a lot from each other and that there is no common understanding regarding the set of features an IoT Device Management solution typically offers. Additionally it turns out that, at the present time, there is no common terminology for naming certain functional aspects of the domain.

This lightweight ontology, which I created as part of my business information technology studies, shall serve as a first step towards creating a common understanding of the knowledge domain and its terminology by consolidating functional areas and actual IoT device managment functional features from various sources of information. To verify that this newly developed ontology appropriately addresses the mentioned challenges, its capability of answering defined competency questions is demonstrated using some exemplary SPARQL queries contained in the 'Extras' folder.

## Questions
Please raise any questions / remarks by creating a new issue within this repository.

## Contribute
Your contributions are more than welcome. Please fork the master branch of this repository and submit your changes via pull request. Thanks a lot for contributing.

## ToDo
- Extend ontology by adding clear defintions of the semantics of each device manage feature (e.g. as `rdfs:comment`)
- Extend ontology by adding additional (recent) IoT device managment features from additional sources as individuals
- Extend ontology by adding additional references as individuals, describing existing features more holistically
- Modify ontology to extend an existing IoT ontology (e.g. *FIESTA-IoT Ontology/M3-lite Taxonomy, IoT-Lite Ontology, IoT-O, oneM2M Base Ontology, Semantic Sensor Network Ontology, WoT ontology*)