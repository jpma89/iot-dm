# Example SPARQL queries for some competency questions

**Competency question 1: Which are the top-level functional areas of IoT device management?**
```sparql
PREFIX  rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT  ?superClassLabel ?directSubClassLabel
WHERE
  { ?superClass  rdfs:label    ?superClassLabel .
    ?directSubClass  rdfs:subClassOf  ?superClass ;
              rdfs:label       ?directSubClassLabel
    FILTER ( ?superClassLabel = "IotDeviceManagementFeature"@en )
  }
```

**Competency question 2: Which are the sub-concepts of a top-level functional area <e.g. DeviceSoftwareManagementFeature>?**
```sparql
PREFIX  rdf:  <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX  rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT  ?targetClassLabel ?entityLabel ?entityType
WHERE
  { ?targetClass  rdfs:label  ?targetClassLabel .
    ?entity   rdf:type    ?entityType ;
              rdfs:label  ?entityLabel
      { ?subClass  rdfs:subClassOf  ?targetClass .
        ?entity (rdfs:subClassOf)* ?subClass
      }
    UNION
      { ?entityType (rdfs:subClassOf)* ?targetClass }
    FILTER ( ?targetClassLabel = "DeviceSoftwareManagementFeature"@en )
  }
```

**Competency question 3a: Which alternative terms do exist for the functial area <e.g. DeviceProvisioningFeature>?**
```sparql
PREFIX  skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX  rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT  ?entityLabel ?alternativeEntityLabel
WHERE
  { ?entity  rdfs:label  ?entityLabel
    OPTIONAL
      { ?entity  skos:altLabel  ?alternativeEntityLabel }
    FILTER ( ?entityLabel = "DeviceProvisioningFeature"@en )
  }
```

**Competency question 3b: Which alternative terms do exist for an actual functional feature <e.g. FirmwareUpdateLocking>?**
```sparql
PREFIX  skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX  rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT  ?entityLabel ?alternativeEntityLabel
WHERE
  { ?entity  rdfs:label  ?entityLabel
    OPTIONAL
      { ?entity  skos:altLabel  ?alternativeEntityLabel }
    FILTER ( ?entityLabel = "F_FirmwareUpdateLocking"@en )
  }
```

**Competency question 4: Which are relevant sources of information for an actual functional feature <e.g. DeviceDiscovery>?**
```sparql
PREFIX  rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT  ?requestedEntityLabel ?referenceLabel ?referenceAuthor ?referencePublisher ?referenceTitle ?referenceYear
WHERE
  { ?providesInformationRegarding
              rdfs:label            ?objectPropertyLabel .
    ?entity   rdfs:label            ?requestedEntityLabel .
    ?authorProperty
              rdfs:label            ?authorLabel .
    ?publisherProperty
              rdfs:label            ?publisherLabel .
    ?titleProperty
              rdfs:label            ?titleLabel .
    ?yearProperty
              rdfs:label            ?yearLabel .
    ?reference  ?providesInformationRegarding  ?entity ;
              rdfs:label            ?referenceLabel
    OPTIONAL
      { ?reference  ?authorProperty  ?referenceAuthor }
    OPTIONAL
      { ?reference  ?publisherProperty  ?referencePublisher }
    OPTIONAL
      { ?reference  ?titleProperty  ?referenceTitle }
    OPTIONAL
      { ?reference  ?yearProperty  ?referenceYear }
    FILTER ( ?objectPropertyLabel = "providesInformationRegarding"@en )
    FILTER ( ?authorLabel = "author"@en )
    FILTER ( ?publisherLabel = "publisher"@en )
    FILTER ( ?titleLabel = "title"@en )
    FILTER ( ?yearLabel = "year"@en )
    FILTER ( ?requestedEntityLabel = "F_DeviceDiscovery"@en )
  }
```