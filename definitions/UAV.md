# UAV
This entity contains a harmonised description of a specific Unmanned Aerial Vehicle (UAV). This entity is primarily associated with UAV command and control and related UAV transport applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| uavModel | Relationship | Reference to the UAV Model definition which describes the UAV in more detail. | Mandatory |
| name | Property | A name given to this UAV. | Recommended |
| owner | Property | A list detailing the owner or owners of the UAV.<br/><br/>Refers to one or more Schema.org person or organization.<br/><br/>https://schema.org/Person<br/><br/>https://schema.org/Organization | Recommended |
| operator | Relationship | A list detailing the operator or operators of the UAV.<br/><br/>Refers to one or more Schema.org person or organization.<br/><br/>https://schema.org/Person<br/><br/>https://schema.org/Organization | Recommended |
| operationMode | Property | Text describing the choice from "vlos", "evlos", "bvlos", "automated"<br/><br/>Note: descriptions align with UTM Flight message. | Recommended |
| location | GeoProperty | The geo:json encoded current (/last known) GPS position of the UAV. | Mandatory |
| elevation | Property | The elevation of the UAV (relative to ground level at the specified location). Specify value and units of measure. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time of the latest monitoring report or update. | Mandatory |
| flightStatus | Property | The flight status of the UAV, including: **stop, takeoff, flight, hover, land** | Mandatory |
| workStatus | Property | The work status of the UAV, including: **stop, prepare, work, finish** | Optional |
| groundSpeed | Property | The latest reported ground speed of the UAV. Specify value and units of measure | Optional |
| fuel | Property | Current fuel load of the UAV. Specify value and units of measure | Optional |
| <em>dateObserved</em> | <em>TemporalProperty</em> | <em>Indicates the date/time the observation was recorded.<br/><br/>Note this field was defined for use with NGSIv2 and is now deprecated. For new entities and applications replace with **observedAt**</em> | <em>Deprecated</em> |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **UAV** entity

[Download context definition.](../examples/UAV-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "uavModel": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/uavmodel",
        "name": "https://schema.org/name",
        "owner": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/owner",
        "operator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operator",
        "operationMode": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationmode",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "elevation": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/elevation",
        "flightStatus": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/flightstatus",
        "workStatus": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/workstatus",
        "groundSpeed": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/groundspeed",
        "fuel": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fuel",
        "dateObserved": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dateobserved"
    }
}
```
## Example of UAV Entity
The following is an example instance of the **UAV** entity

[Download example entity definition.](../examples/UAV.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/UAV-context.jsonld"
    ],
    "id": "urn:ngsi-ld:UAV:1fa179a6-b507-4857-ad72-eb5513ef05c6",
    "type": "UAV",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "uavModel": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAVModel:23821045-33d4-46ec-b777-98f461bf4856"
    },
    "name": {
        "type": "Property",
        "value": "Yellow1"
    },
    "owner": {
        "type": "Property",
        "value": [
            "urn:ngsi-ld:Person:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84",
            "urn:ngsi-ld:Organization:1be9cd61-ef59-421f-a326-4b6c84411ad4"
        ]
    },
    "operator": {
        "type": "Relationship",
        "value": [
            "urn:ngsi-ld:Person:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84",
            "urn:ngsi-ld:Person:3d5f533e-5920-11e8-871b-534f1ae5f35d"
        ]
    },
    "operationMode": {
        "type": "Property",
        "value": "vlos"
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -103.9904,
                39.7564
            ]
        }
    },
    "elevation": {
        "type": "Property",
        "value": 1000,
        "unitCode": "MTR"
    },
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-23T10:18:16Z"
    },
    "flightStatus": {
        "type": "Property",
        "value": "takeoff"
    },
    "workStatus": {
        "type": "Property",
        "value": "finish"
    },
    "groundSpeed": {
        "type": "Property",
        "value": 50,
        "unitText": "MTS"
    },
    "fuel": {
        "type": "Property",
        "value": 50,
        "unitCode": "GLI"
    }
}
```
