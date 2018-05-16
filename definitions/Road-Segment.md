# Road Segment
This entity contains a harmonised geographic and contextual description of a RoadSegment. A collection of RoadSegments are used to describe a Road. This entity is primarily associated with the Automotive and Smart City vertical segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| road | Relationship | Refers to the Road entity that this RoadSegment relates to. | Recommended |
| startPoint | GeoProperty | The geo:json encoded start point for this RoadSegment. | Mandatory |
| endPoint | GeoProperty | The geo:json encoded end point for this RoadSegment. | Mandatory |
| roadSegments | Relationship | Refers to related RoadSegment entities e.g. adjoining, junctions, opposite carriageway. | Recommended |
| roadClass | Property | The official classification of this road (relevant to the local country). | Recommended |
| name | Property | The name for this road segment. | Recommended |
| path | GeoProperty | The geo:json sequence of points that make up this RoadSegment (as a LineString). | Recommended |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Road Segment** entity

[Download context definition.](../examples/Road-Segment-context.jsonld)

```JavaScript
{
    "id": "@id",
    "type": "@type",
    "DateTime": "http://uri.etsi.org/ngsi-ld/DateTime",
    "createdAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/createdAt",
        "@type": "DateTime"
    },
    "modifiedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/modifiedAt",
        "@type": "DateTime"
    },
    "Property": "http://etsi.org/nsgi-ld/Property",
    "Relationship": "http://uri.etsi.org/ngsi-ld/Relationship",
    "GeoProperty": "http://uri.etsi.org/ngsi-ld/GeoProperty"
}
```
## Example of Road Segment Entity
The following is an example instance of the **Road Segment** entity

[Download example entity definition.](../examples/Road-Segment.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Road-Segment-context.jsonld"
    ],
    "id": "urn:ngsi-ld:RoadSegment:27109fe0-0c60-4302-a9eb-e7065eca876e",
    "type": "RoadSegment",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "road": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Road:19b6f4b7-a9b4-4114-8391-3133bf96aedc"
    },
    "startPoint": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                52.026536,
                0.603404
            ]
        }
    },
    "endPoint": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                52.058727,
                0.700214
            ]
        }
    },
    "roadSegments": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:RoadSegment:75460f68-5911-11e8-abc1-2f5262349650",
            "urn:ngsi-ld:RoadSegment:7b2c9d70-5911-11e8-8484-7704bd54bf6b"
        ]
    },
    "roadClass": {
        "type": "Property",
        "value": "Motorway"
    },
    "name": {
        "type": "Property",
        "value": "M1 J13 to J14"
    },
    "path": {
        "type": "GeoProperty",
        "value": {
            "type": "LineString",
            "coordinates": [
                [
                    52.026536,
                    0.603404
                ],
                [
                    52.034828,
                    0.637166
                ],
                [
                    52.037105,
                    0.643839
                ],
                [
                    52.048449,
                    0.669202
                ],
                [
                    52.058727,
                    0.700214
                ]
            ]
        }
    }
}
```
