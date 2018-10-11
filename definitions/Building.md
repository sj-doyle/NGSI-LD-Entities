# Building
This entity contains a harmonised description of a building. This entity is associated with the vertical segments of smart homes, smart cities, industry and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| buildingType | Relationship | Refers to the Building Type that this building is an instance of. | Mandatory |
| category | Property | One or more categories relevant to the building with choices based on for example<br/><br/> http://wiki.openstreetmap.org/wiki/Map_Features#Building | Recommended |
| containedInPlace | GeoProperty | The geo:json encoded polygon/ multi-polygon of the building plot in which this building sits. | Recommended |
| location | GeoProperty | The geo:json encoded polygon/ multi-polygon of this building. | Mandatory |
| address | Property | One or more categories relevant to the building with choices based on for example<br/><br/> http://wiki.openstreetmap.org/wiki/Map_Features#Building | Recommended |
| owner | Relationship | Reference to the owner or owners of the building as either a Schema.org person or organization.<br/><br/>https://schema.org/Person<br/><br/>https://schema.org/Organization | Recommended |
| occupier | Relationship | Reference to the occupier or occupiers of the building as either a Schema.org person or organization.<br/><br/>https://schema.org/Person<br/><br/>https://schema.org/Organization | Recommended |
| subscriptionServices | Relationship | Reference to service subscriptions related to this building e.g. energy supplies, Internet Service Providers etc | Optional |
| floorsAboveGround | Property | The number of floors above ground level in this building. | Optional |
| floorsBelowGround | Property | The number of floors above ground level in this building. | Optional |
| description | Property | An optional description of this building. | Recommended |
| mapUri | uri | A URI (URL/URN) to a mapping service which shows the location of the building. | Optional |
| notes | Property | Free format notes relating to the building e.g. published occupants, opening hours etc. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Building** entity

[Download context definition.](../examples/Building-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "buildingType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/buildingtype",
        "category": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/category",
        "containedInPlace": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/containedinplace",
        "address": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/address",
        "owner": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/owner",
        "occupier": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/occupier",
        "subscriptionServices": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/subscriptionservices",
        "floorsAboveGround": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/floorsaboveground",
        "floorsBelowGround": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/floorsbelowground",
        "mapUri": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/mapuri",
        "notes": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/notes"
    }
}
```
## Example of Building Entity
The following is an example instance of the **Building** entity

[Download example entity definition.](../examples/Building.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Building-context.jsonld"
    ],
    "id": "urn:ngsi-ld:Building:ba2d4fd9-f57f-4610-a589-2d52670d14f3",
    "type": "Building",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "buildingType": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:BuildingType:8b1f2bf0-5093-4182-ad4b-224182bb3b9f"
    },
    "category": {
        "type": "Property",
        "value": [
            "house"
        ]
    },
    "containedInPlace": {
        "type": "GeoProperty",
        "value": {
            "type": "Polygon",
            "coordinates": [
                [
                    100,
                    0
                ],
                [
                    101,
                    0
                ],
                [
                    101,
                    1
                ],
                [
                    100,
                    1
                ],
                [
                    100,
                    0
                ]
            ]
        }
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Polygon",
            "coordinates": [
                [
                    100,
                    0
                ],
                [
                    101,
                    0
                ],
                [
                    101,
                    1
                ],
                [
                    100,
                    1
                ],
                [
                    100,
                    0
                ]
            ]
        }
    },
    "address": {
        "type": "Property",
        "addressLocality": "London",
        "postalCode": "EC4N 8AF",
        "streetAddress": "25 Walbrook"
    },
    "owner": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Person:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84",
            "urn:ngsi-ld:Organization:1be9cd61-ef59-421f-a326-4b6c84411ad4"
        ]
    },
    "occupier": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Person:9830f692-7677-11e6-838b-4f9fb3dc5a4f",
            "urn:ngsi-ld:Organization:837e7a18-4712-11e8-b005-d7042eb57989"
        ]
    },
    "subscriptionServices": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:SubscriptionService:8ecc19fc-4712-11e8-a717-0be3ca52406e",
            "urn:ngsi-ld:SubscriptionService:a3adbfa6-4712-11e8-a80e-2bf67e7617bf"
        ]
    },
    "floorsAboveGround": {
        "type": "Property",
        "value": 14
    },
    "floorsBelowGround": {
        "type": "Property",
        "value": 2
    },
    "description": {
        "type": "Property",
        "value": "Multi-tenant office block"
    },
    "mapUri": {
        "type": "uri",
        "value": "https://www.google.co.uk/maps/place/The+Walbrook,+Walbrook,+London+EC4N+8AF/@51.5120758,-0.0920769"
    },
    "notes": {
        "type": "Property",
        "value": [
            "Intelligent entry barrier system",
            "Intelligent air conditioning units",
            "Normal opening 07:00 – 20:00"
        ]
    }
}
```
