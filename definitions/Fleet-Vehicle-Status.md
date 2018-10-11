# Fleet Vehicle Status
This entity contains a harmonised description of the status of a generic fleet vehicle. This entity is primarily associated with the vertical segment of the transport and logistics but may also be used many other related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| fleetVehicle | Relationship | Reference to the FleetVehicle entity to which this status entity relates. | Mandatory |
| fleetVehicleOperation | Relationship | Reference to the FleetVehicleOperation entity to which this status entity relates. | Mandatory |
| restFuelAmount | Property | The level of fuel recorded when the vehicle was last at rest (i.e. stopped). The timestamp element of the attribute should indicate when the vehicle was last at rest. Data to be recorded in Litres. | Mandatory |
| lastFuellingAmount | Property | The level of fuel added to the vehicle at the last fuelling. The timestamp element of the attribute should indicate when the vehicle was fuelled. Data tobe recorded in Litres. | Mandatory |
| currentStatus | Property | A description of the current status of the vehicle e.g. deployed, finished, terminated, servicing, starting | Recommended |
| currentOperative | Property | The current operative (e.g. driver) of the vehicle described as a Schema.org 'person'. https://schema.org/Person | Recommended |
| speed | Property | The current speed of the fleet vehicle (km/h). The timestamp element of the attribute should indicate when the reading was obtained. | Optional |
| bearing | Property | The current bearing of the fleet vehicle in degrees relative to North. The timestamp element of the attribute should indicate when the reading was obtained. | Optional |
| lastKnownPosition | GeoProperty | The last known geo location (point/ polygon) of the fleet vehicle. | Mandatory |
| lastKnownPositionUpdatedAt | TemporalProperty | The timestamp of the last known position update for the fleet vehicle. | Mandatory |
| inRestrictedArea | Property | Indicates if the vehicle is known to be in a restricted area at the time of the status update. | Recommended |
| mileageFromOdometer | Property | The total distance the fleet vehicle has travelled according to the on-board odometer in kilometres (unitCode KMT) or miles (unitCode SMI). See also Schema.org Vehicle/ mileageFromOdometer. The timestamp element records when the odometer reading was taken. | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Fleet Vehicle Status** entity

[Download context definition.](../examples/Fleet-Vehicle-Status-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "fleetVehicle": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fleetvehicle",
        "fleetVehicleOperation": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fleetvehicleoperation",
        "restFuelAmount": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/restfuelamount",
        "lastFuellingAmount": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/lastfuellingamount",
        "currentStatus": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/currentstatus",
        "currentOperative": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/currentoperative",
        "speed": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/speed",
        "bearing": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/bearing",
        "lastKnownPosition": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/lastknownposition",
        "lastKnownPositionUpdatedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/lastknownpositionupdatedat",
        "inRestrictedArea": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/inrestrictedarea",
        "mileageFromOdometer": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/mileagefromodometer"
    }
}
```
## Example of Fleet Vehicle Status Entity
The following is an example instance of the **Fleet Vehicle Status** entity

[Download example entity definition.](../examples/Fleet-Vehicle-Status.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Fleet-Vehicle-Status-context.jsonld"
    ],
    "id": "urn:ngsi-ld:FleetVehicleStatus:16ea1c5c-5aa6-11e8-8144-4b82063ca31c",
    "type": "FleetVehicleStatus",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "fleetVehicle": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:FleetVehicle:84c6a3a8-5aa6-11e8-bedc-27e105edd16f"
    },
    "fleetVehicleOperation": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:FleetVehicleOperation:a4f0a07a-5aa6-11e8-b70f-4b9d36e53d7b"
    },
    "restFuelAmount": {
        "type": "Property",
        "value": 28,
        "unitCode": "LTR",
        "observedAt": "2016-08-22T10:18:16Z"
    },
    "lastFuellingAmount": {
        "type": "Property",
        "value": 95,
        "unitCode": "LTR",
        "observedAt": "2016-08-22T10:18:16Z"
    },
    "currentStatus": {
        "type": "Property",
        "value": "finished"
    },
    "currentOperative": {
        "type": "Property",
        "givenName": "John Smith",
        "jobTitle": "Ambulance Operator"
    },
    "speed": {
        "type": "Property",
        "value": 60,
        "unitCode": "KMH",
        "observedAt": "2016-08-22T10:18:16Z"
    },
    "bearing": {
        "type": "Property",
        "value": 80,
        "unitCode": "DD",
        "observedAt": "2016-08-22T10:18:16Z"
    },
    "lastKnownPosition": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -104.99404,
                39.75621
            ]
        }
    },
    "lastKnownPositionUpdatedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "inRestrictedArea": {
        "type": "Property",
        "value": true
    },
    "mileageFromOdometer": {
        "type": "Property",
        "value": 18756,
        "unitCode": "SMI",
        "observedAt": "2016-08-22T10:18:16Z"
    }
}
```
