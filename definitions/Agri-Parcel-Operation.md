# Agri Parcel Operation
This entity contains a harmonised description of a generic operations performed on a parcel of land. This entity is primarily associated with the agricultural vertical and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| agriParcel | Relationship | Reference to the AgriParcel to which this entity relates. | Mandatory |
| operationType | Property | A choice from an enumerated list describing the operation performed on the parcel. One of: **fertiliser, inspection, pesticide, water, other.** | Recommended |
| description | Property | A description of the operation. | Recommended |
| result | Property | A description of the results of the operation. One of: **ok, aborted, failed.** | Recommended |
| plannedStartAt | TemporalProperty | The planned start date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation starts may be before or after the planned start. | Recommended |
| plannedEndAt | TemporalProperty | The planned end date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation finishes may be before or after the planned end. | Recommended |
| status | Property | A choice from an enumerated list describing the status. One of: **planned, ongoing, finished, scheduled, cancelled.** | Recommended |
| operator | Relationship | Reference to the operator conducting the operation | Recommended |
| startedAt | TemporalProperty | Timestamp when the operation actually started to be performed. | Recommended |
| endedAt | TemporalProperty | Timestamp when the operation actually finished. | Recommended |
| agriProduct | Relationship | Reference to the AgriProduct used/ applied. | Optional |
| quantity | Property | The total quantity of water or product used/ applied. It is recommended this is measured in litres for liquids or kilogrammes for solids. | Optional |
| waterSource | Property | If water was applied/ use this specifies the source. One of: **borehole, rainfall, river, rainwater capture, water dam, commercial supply.** | Recommended |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Agri Parcel Operation** entity

[Download context definition.](../examples/Agri-Parcel-Operation-context.jsonld)

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
    "TemporalProperty": "http://uri.etsi.org/ngsi-ld/TemporalProperty"
}
```
## Example of Agri Parcel Operation Entity
The following is an example instance of the **Agri Parcel Operation** entity

[Download example entity definition.](../examples/Agri-Parcel-Operation.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Agri-Parcel-Operation.jsonld"
    ],
    "id": "urn:ngsi-ld:AgriParcelOperation:e1e9d3a3-074f-46f1-9375-52000d05a62b",
    "type": "AgriParcelOperation",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "agriParcel": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:AgriParcel:318366a9-7643-4d8e-9a11-c76a8c29d8eb"
    },
    "operationType": {
        "type": "Property",
        "value": "fertiliser"
    },
    "description": {
        "type": "Property",
        "value": "Monthly fertiliser application"
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
        "object": "urn:ngsi-ld:Person:fce9dcbc-4479-11e8-9de1-cb228de7a15c"
    },
    "startedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "agriProduct": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:AgriProduct:a8f616b8-13fb-473a-8e61-b7a80c6c93ec"
    },
    "quantity": {
        "type": "Property",
        "value": 40,
        "unitCode": "KGM"
    },
    "waterSource": {
        "type": "Property",
        "value": "arable"
    }
}
```
