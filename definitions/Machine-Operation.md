# Machine Operation
This entity contains a harmonised description of a generic machine operation. This entity is primarily associated with the industry segment and related IoT applications. Each MachineOperation instance will be related to a specific Machine instance.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| machine | Relationship | A reference to the associated Machine for this machine operation. | Mandatory |
| operationType | Property | Defines the type of operation conducted/ requested. This will be one of a defined list of operation types specific to the machine/ machineModel.<br/><br/>Including: **process, setup，maintenance, repair，breakdown.**<br/<br/>The list of operation types highly depends on the machine model.  | Mandatory |
| description | Property | A description of the operation conducted or applied. | Recommended |
| result | Property | The result of the operation. One of **ok, success, suspended, aborted, failed.** | Recommended |
| plannedStartAt | TemporalProperty | The planned start date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation starts may be before or after the planned start. | Mandatory |
| plannedEndAt | TemporalProperty | The planned end date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation finishes may be before or after the planned end. | Mandatory |
| status | Property | A choice from an enumerated list describing the status. One of: **planned, ongoing, finished, scheduled, cancelled.** | Recommended |
| operator | Relationship | Reference to the operator conducting the operation | Recommended |
| startedAt | TemporalProperty | Timestamp when the operation actually started to be performed. | Recommended |
| endedAt | TemporalProperty | Timestamp when the operation actually finished. | Recommended |
| commandSequence | Property | The command sequence executed/ requested for the machine in a representation format relevant to the machine. | Optional |
| operationOutput | Property | A custom property describing the output data of the operation. The schema of the output highly depends the machine model. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Machine Operation** entity

[Download context definition.](../examples/Machine-Operation-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "machine": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/machine",
        "operationType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationtype",
        "result": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/result",
        "plannedStartAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/plannedstartat",
        "plannedEndAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/plannedendat",
        "operator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operator",
        "startedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/startedat",
        "endedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/endedat",
        "commandSequence": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/commandsequence",
        "operationOutput": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationoutput"
    }
}
```
## Example of Machine Operation Entity
The following is an example instance of the **Machine Operation** entity

[Download example entity definition.](../examples/Machine-Operation.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Machine-Operation-context.jsonld"
    ],
    "id": "urn:ngsi-ld:MachineOperation:27577638-bd8a-4732-b418-fc8b949a0b0f",
    "type": "MachineOperation",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "machine": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Machine:2033a7c7-d31b-48e7-91c2-014dc426c29e"
    },
    "operationType": {
        "type": "Property",
        "value": [
            "process"
        ]
    },
    "description": {
        "type": "Property",
        "value": "Printing of 1000 T-shirts"
    },
    "result": {
        "type": "Property",
        "value": "ok"
    },
    "plannedStartAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "plannedEndAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "status": {
        "type": "Property",
        "value": "finished"
    },
    "operator": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Person:fd6f0070-47d7-11e8-a26c-0784612b9393"
    },
    "startedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "commandSequence": {
        "type": "Property",
        "value": [
            "Select inks",
            "Prepare print masks",
            "Print shirts",
            "Clean print heads and rollers"
        ]
    },
    "operationOutput": {
        "type": "Property",
        "value": {
            "Units Printed": 1000,
            "Faults": 0
        }
    }
}
```
