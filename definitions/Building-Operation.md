# Building Operation
This entity contains a harmonised description of a generic operation (related to smart buildings) applied to the referenced building. The building operation contains dynamic data reported by, or associated with a building or operations applicable to the building. This entity is associated with the vertical segments of smart homes, smart cities, industry and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| building | Relationship | A reference to the associated Building entity for this Building Operation. | Mandatory |
| operationType | Property | Defines the type of operation conducted/ requested. This will be one of a defined list of operation types specific to the building. | Recommended |
| description | Property | A description of the operation. | Recommended |
| result | Property | The result of the operation. One of **ok, aborted, failed.** | Recommended |
| plannedStartAt | TemporalProperty | The planned start date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation starts may be before or after the planned start. | Mandatory |
| plannedEndAt | TemporalProperty | The planned end date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation finishes may be before or after the planned end. | Mandatory |
| status | Property | A choice from an enumerated list describing the status. One of: **planned, ongoing, finished, scheduled, cancelled.** | Recommended |
| operator | Relationship | Reference to the operator conducting the operation | Recommended |
| startedAt | TemporalProperty | Timestamp when the operation actually started to be performed. | Recommended |
| endedAt | TemporalProperty | Timestamp when the operation actually finished. | Recommended |
| operationSequence | Property | The sequence of operations executed/ requested for the building in a representation format relevant to the building. | Optional |
| relatedBuildingOperations | Relationship | Optional references to any related building operations. | Optional |
| relatedOperations | Relationship | Optional references to any related operations (on devices, machines etc). | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Building Operation** entity

[Download context definition.](../examples/Building-Operation-context.jsonld)

```JavaScript
{
    "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
    "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
    "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
    "building": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/building",
    "operationType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationtype",
    "result": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/result",
    "plannedStartAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/plannedstartat",
    "plannedEndAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/plannedendat",
    "operator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operator",
    "startedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/startedat",
    "endedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/endedat",
    "operationSequence": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operationsequence",
    "relatedBuildingOperations": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/relatedbuildingoperations",
    "relatedOperations": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/relatedoperations"
}
```
## Example of Building Operation Entity
The following is an example instance of the **Building Operation** entity

[Download example entity definition.](../examples/Building-Operation.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Building-Operation-context.jsonld"
    ],
    "id": "urn:ngsi-ld:BuildingOperation:57b912ab-eb47-4cd5-bc9d-73abece1f1b3",
    "type": "BuildingOperation",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "building": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Building:f59e2074-0032-4ccd-b0dd-f06370ffb6af"
    },
    "operationType": {
        "type": "Property",
        "value": "Air Conditioning Switch To Low Power"
    },
    "description": {
        "type": "Property",
        "value": "Air conditioning levels reduced due to out of hours"
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
        "object": "urn:ngsi-ld:Person:3ac33d78-4716-11e8-b332-3bfc33a871b7"
    },
    "startedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "operationSequence": {
        "type": "Property",
        "value": [
            "Fan levels reduced to minimum",
            "Target temperature set to 24 degrees Celsius"
        ]
    },
    "relatedBuildingOperations": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:BuildingOperation:b4fb8bff-1a8f-455f-8cc0-ca43c069f865",
            "urn:ngsi-ld:BuildingOperation:55c24793-3437-4157-9bda-667c9e1531fc",
            "urn:ngsi-ld:BuildingOperation:714b95f2-4716-11e8-b488-7f92794ea9de"
        ]
    },
    "relatedOperations": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:DeviceOperation:7a464b84-4716-11e8-8b3f-bbe95bc73eb2",
            "urn:ngsi-ld:MachineOperation:8304a16c-4716-11e8-86c5-2b1c5e248f62"
        ]
    }
}
```
