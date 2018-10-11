# Fleet Vehicle Operation
This entity contains a harmonised description of a generic fleet vehicle operation such as a delivery, or a postal collection. This entity is primarily associated with the vertical segment of the transport and logistics but may also be used many other related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| fleetVehicle | Relationship | Reference to the FleetVehicle entity to which this operation relates. | Mandatory |
| fleetVehicleStatus | Relationship | Reference to the FleetVehicleStatus entity to which this operation relates - this contains the real-time status information | Recommended |
| initiatingLocation | GeoProperty | The geo location (point/ polygon) of the point from where the service was requested e.g. the location of the person who called for an ambulance. | Mandatory |
| startedAt | TemporalProperty | The start date and time when the event or operation was triggered. | Recommended |
| endedAt | TemporalProperty | The end date and time of the event when the event or operation is known to be over/ complete. Null/ omitted if not yet ended. | Recommended |
| operationType | Property | The free text type of the event or operation e.g. e.g. Call for a patient transportation, postal collection, delivery, close to a restricted area, overspeed. | Mandatory |
| description | Property | The description of the event or operation. | Recommended |
| result | Property | The final result of the event or operation. | Recommended |
| responseTime | Property | Indicates the time to respond to an event, in seconds. The associated observedAt timestamp indicates when the last update was recorded. E.g. records the response time for an ambulance to reach to a patient. | Mandatory |
| transportTime | Property | Indicates the time that the fleet vehicle has spent transporting people or supplies for the current operation. E.g. indicates the time an ambulance spent transporting a patient to a hospital emergency department. | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Fleet Vehicle Operation** entity

[Download context definition.](../examples/Fleet-Vehicle-Operation-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "fleetVehicle": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fleetvehicle",
        "fleetVehicleStatus": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fleetvehiclestatus",
        "initiatingLocation": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/initiatinglocation",
        "startedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/startedat",
        "endedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/endedat",
        "operationType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationtype",
        "result": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/result",
        "responseTime": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/responsetime",
        "transportTime": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/transporttime"
    }
}
```
## Example of Fleet Vehicle Operation Entity
The following is an example instance of the **Fleet Vehicle Operation** entity

[Download example entity definition.](../examples/Fleet-Vehicle-Operation.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Fleet-Vehicle-Operation-context.jsonld"
    ],
    "id": "urn:ngsi-ld:FleetVehicleOperation:8e876a60-5aa3-11e8-b350-d7b51a09fb6c",
    "type": "FleetVehicleOperation",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "fleetVehicle": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:FleetVehicle:84c6a3a8-5aa6-11e8-bedc-27e105edd16f"
    },
    "fleetVehicleStatus": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:FleetVehicleStatus:0284e0dc-5aa4-11e8-97e6-2351fc70c286"
    },
    "initiatingLocation": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -104.99404,
                39.75621
            ]
        }
    },
    "startedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "operationType": {
        "type": "Property",
        "value": "Patient transportation"
    },
    "description": {
        "type": "Property",
        "value": "An emergency tranportation of a 3 year old boy"
    },
    "result": {
        "type": "Property",
        "value": "Completed"
    },
    "responseTime": {
        "type": "Property",
        "value": 2500,
        "unitCode": "SEC",
        "observedAt": "2016-08-28T10:18:16Z"
    },
    "transportTime": {
        "type": "Property",
        "value": 1220,
        "unitCode": "SEC",
        "observedAt": "2016-08-28T10:18:16Z"
    }
}
```
