# UAV Model
This entity contains a harmonised description of a generic Unmanned Ariel Vehicle (UAV) model and is applicable to UAV command and control and related UAV transport applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| model | Property | The UAV model's identifier, which may be a UAVModel name. | Mandatory |
| doc | Property | URI reference (URL/URN) to Product Data Sheet or other manufacturer's documentation about this UAVModel. | Recommended |
| description | Property | A description of this UAVModel. | Recommended |
| manufacturerName | Property | The name of the manufacturer of this UAVModel. | Recommended |
| brandName | Property | A description of the brand name of this UAVModel. | Recommended |
| category | Property | The work category of the UAVModel. A choice from the following list: **Aerial_photography, Plant_protection, Industry, Routing_inspection, Mailing, Transportation** | Recommended |
| rotors | Property | The number of the rotors of the UAVModel. | Recommended |
| fuelType | Property | The fuel type powering the UAVModel. A choice from an enumerated list describing the power source. One of: **gasoline, petrol(unleaded), petrol(leaded), petrol, diesel, electric, hydrogen, lpg autogas, cng, biodiesel, ethanol, hybrid electric/petrol, hybrid electric/diesel, other** | Recommended |
| maxFlightTime | Property | The maximum duration of flight of the UAVModel with full fuel and no load. Specify value and units of measure. | Optional |
| maxFlightAltitude | Property | The maximum flight altitude of the UAVModel above ground. Specify value and units of measure. | Optional |
| maxGroundVelocity | Property | The maximum ground velocity of the UAVModel (under still wind conditions). Specify value and units of measure. | Optional |
| minWeight | Property | The weight of the UAV without fuel or load. Specify value and units of measure. | Optional |
| minUnladenWeight | Property | The weight of the UAV with full fuel but no load. Specify value and units of measure. | Optional |
| maxLoad | Property | The maximum load that the UAV is permitted to transport. Specify value and units of measure. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **UAV Model** entity

[Download context definition.](../examples/UAV-Model-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "model": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/model",
        "doc": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/doc",
        "manufacturerName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/manufacturername",
        "brandName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/brandname",
        "category": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/category",
        "rotors": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/rotors",
        "fuelType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fueltype",
        "maxFlightTime": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/maxflighttime",
        "maxFlightAltitude": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/maxflightaltitude",
        "maxGroundVelocity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/maxgroundvelocity",
        "minWeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/minweight",
        "minUnladenWeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/minunladenweight",
        "maxLoad": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/maxload"
    }
}
```
## Example of UAV Model Entity
The following is an example instance of the **UAV Model** entity

[Download example entity definition.](../examples/UAV-Model.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/UAV-Model-context.jsonld"
    ],
    "id": "urn:ngsi-ld:UAVModel:6f4439d2-5925-11e8-a0ef-53719253dbbd",
    "type": "UAVModel",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "model": {
        "type": "Property",
        "value": "ACME Recon"
    },
    "doc": {
        "type": "Property",
        "value": {
            "@value": "http://example.com/products-services/aircraft/the-recon.html",
            "@type": "https://schema.org/url"
        }
    },
    "description": {
        "type": "Property",
        "value": "The Recon was constructed and designed to offer a clear payload view, with the motor and propeller system aft of the payload. It is smaller and more versatile than many drones, yet robust enough for harsh environment operations. The wingspan is 2.3 meters. An affordable, versatile, and flexible drone for a multitude of uses."
    },
    "manufacturerName": {
        "type": "Property",
        "value": "ACME UAVs"
    },
    "brandName": {
        "type": "Property",
        "value": "Airv"
    },
    "category": {
        "type": "Property",
        "value": "Aerial_photography"
    },
    "rotors": {
        "type": "Property",
        "value": 4
    },
    "fuelType": {
        "type": "Property",
        "value": "gasoline"
    },
    "maxFlightTime": {
        "type": "Property",
        "value": 100,
        "unitCode": "HUR"
    },
    "maxFlightAltitude": {
        "type": "Property",
        "value": 1000,
        "unitCode": "MTR"
    },
    "maxGroundVelocity": {
        "type": "Property",
        "value": 100,
        "unitCode": "MTS"
    },
    "minWeight": {
        "type": "Property",
        "value": 1,
        "unitCode": "KGM"
    },
    "minUnladenWeight": {
        "type": "Property",
        "value": 1.5,
        "unitCode": "KGM"
    },
    "maxLoad": {
        "type": "Property",
        "value": 0.8,
        "unitCode": "KGM"
    }
}
```
