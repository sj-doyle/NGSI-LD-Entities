# Product Record
This entity contains a harmonised description of the conditions recorded as a product (generally a physical instance of a product) moves through the supply chain. This entity is primarily associated with the retail supply vertical and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| product | Relationship | Reference to the Product to which this record relates. | Mandatory |
| location | GeoProperty | The geo:json encoded point / polygon / multi-polygon describing the location this record relates to. | Mandatory |
| temperature | Property | The observed local air temperature nominally in degrees centigrade. | Optional |
| relativeHumidity | Property | Relative Humidity a number between 0 and 1 representing the range of 0% to 100%<br/><br/>0 ≤ relativeHumidity ≤ 1  | Optional |
| atmosphericPressure | Property | Atmospheric Pressure nominally in units of hecto Pascals  | Optional |
| description | Property | Description of this ProductRecord. | Recommended |
| weight | Property | Current (i.e. measured) weight of the product including packaging. This may differ from the original weight due to additional packaging or losses during shipment e.g. evaporation | Optional |
| netWeight | Property | Weight of the Agri-Product itself in a package with GS1 code

Used to identify the net weight of the product. Net Weight excludes all packaging material, including the packaging material of all lower-level GTINs. Example:11.5 kg | Optional |
| volume | Property | The current volume of the product including packaging. | Optional |
| observedAt | TemporalProperty | Indicates the date/time the record was observed/ last observed. | Recommended |
| O2 | Property | The level of gaseous oxygen (O2) present in the atmosphere as measured around the product. | Optional |
| <em>dateObserved</em> | <em>TemporalProperty</em> | <em>Indicates the date/time the observation was recorded.<br/><br/>Note this field was defined for use with NGSIv2 and is now deprecated. For new entities and applications replace with **observedAt**</em> | <em>Deprecated</em> |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Product Record** entity

[Download context definition.](../examples/Product-Record-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "product": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/product",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "temperature": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/temperature",
        "relativeHumidity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/relativehumidity",
        "atmosphericPressure": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/atmosphericpressure",
        "description": "https://schema.org/description",
        "weight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/weight",
        "netWeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/netweight",
        "volume": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/volume",
        "O2": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/o2",
        "dateObserved": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dateobserved"
    }
}
```
## Example of Product Record Entity
The following is an example instance of the **Product Record** entity

[Download example entity definition.](../examples/Product-Record.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Product-Record-context.jsonld"
    ],
    "id": "urn:ngsi-ld:ProductRecord:85d05a21-6907-44b3-83d8-85d8a713d003",
    "type": "ProductRecord",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "product": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Product:d3676010-d815-468c-9e01-25739c5a25ed"
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -104.99404,
                39.75621
            ]
        }
    },
    "temperature": {
        "type": "Property",
        "value": 3.823,
        "unitCode": "CEL",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "relativeHumidity": {
        "type": "Property",
        "value": 0.7,
        "unitCode": "C62",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "atmosphericPressure": {
        "type": "Property",
        "value": 1006.19,
        "unitCode": "A97",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "description": {
        "type": "Property",
        "value": "Palm oil consignment arrived at port for shipment"
    },
    "weight": {
        "type": "Property",
        "value": {
            "value": 2550,
            "unitText": "grammes"
        },
        "unitCode": "GRM",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "netWeight": {
        "type": "Property",
        "value": {
            "value": 2500,
            "unitText": "grammes"
        },
        "unitCode": "GRM",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "volume": {
        "type": "Property",
        "unitCode": "MTQ",
        "value": 1.7,
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2017-05-04T10:18:16Z"
    },
    "O2": {
        "type": "Property",
        "value": {
            "value": 300,
            "unitText": "microgramme per cubic metre"
        },
        "unitCode": "GQ",
        "observedAt": "2017-05-04T12:30:00Z"
    }
}
```
