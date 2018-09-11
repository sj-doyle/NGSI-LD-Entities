# Road
This entity contains a harmonised geographic and contextual description of a Road. Roads are made up of one or more RoadSegment entities. This entity is primarily associated with the Automotive and Smart City vertical segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| country | Property | The country which this road is in | Mandatory |
| roadSegments | Relationship | Refers to the set of RoadSegment entities that define this road. | Recommended |
| roadClass | Property | The official classification of this road (relevant to the local country). | Recommended |
| name | Property | The official designation of this road. | Recommended |
| alternateName | Property | An alternative name for this road. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Road** entity

[Download context definition.](../examples/Road-context.jsonld)

```JavaScript
{
    "source": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "@type": "Property"
    },
    "dataProvider": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "@type": "Property"
    },
    "entityVersion": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "@type": "Property"
    },
    "country": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/country",
        "@type": "Property"
    },
    "roadSegments": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/roadsegments",
        "@type": "Relationship"
    },
    "roadClass": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/roadclass",
        "@type": "Property"
    },
    "alternateName": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/alternatename",
        "@type": "Property"
    }
}
```
## Example of Road Entity
The following is an example instance of the **Road** entity

[Download example entity definition.](../examples/Road.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Road-context.jsonld"
    ],
    "id": "urn:ngsi-ld:Road:19b6f4b7-a9b4-4114-8391-3133bf96aedc",
    "type": "Road",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "country": {
        "type": "Property",
        "value": "United Kingdom"
    },
    "roadSegments": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:RoadSegment:2a982120-4d98-425b-a8db-1de5563db6a8",
            "urn:ngsi-ld:RoadSegment:43e255c7-262e-4d6d-95a1-69a53e37dcc0"
        ]
    },
    "roadClass": {
        "type": "Property",
        "value": "Motorway"
    },
    "name": {
        "type": "Property",
        "value": "M1"
    },
    "alternateName": {
        "type": "Property",
        "value": "M1 Motorway"
    }
}
```
