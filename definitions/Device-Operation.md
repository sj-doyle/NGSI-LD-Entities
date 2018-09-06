# Device Operation
This entity contains a harmonised description of a generic device operation entity. The device operation entity contains dynamic data reported by a device and is therefore applicable to all IoT segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| device | Relationship | A reference to the associated Device for this device operation. | Mandatory |
| operationType | Property | A choice from an enumerated list including: **event, maintenance, fault, installation, upgrade, other.** | Recommended |
| description | Property | A description of the operation. | Recommended |
| result | Property | The result of the operation. One of **ok, aborted, failed.** | Recommended |
| plannedStartAt | TemporalProperty | The planned start date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation starts may be before or after the planned start. | Mandatory |
| plannedEndAt | TemporalProperty | The planned end date/timestamp for the operation. <br/><br/>Note that this is advisory and the actual time the operation finishes may be before or after the planned end. | Mandatory |
| status | Property | A choice from an enumerated list describing the status. One of: **planned, ongoing, finished, scheduled, cancelled.** | Recommended |
| operator | Relationship | Reference to the operator conducting the operation | Recommended |
| startedAt | TemporalProperty | Timestamp when the operation actually started to be performed. | Recommended |
| endedAt | TemporalProperty | Timestamp when the operation actually finished. | Recommended |
| reportedAt | TemporalProperty | Timestamp when the event/ fault was reported. | Optional |
| addressedAt | TemporalProperty | The timestamp when an event or fault was addressed or cleared. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Device Operation** entity

[Download context definition.](../examples/Device-Operation-context.jsonld)

```JavaScript
{
    "source": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "dataProvider": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "entityVersion": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "device": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "operationType": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "result": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "plannedStartAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "plannedEndAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "operator": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "startedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "endedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "reportedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "addressedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    }
}
```
## Example of Device Operation Entity
The following is an example instance of the **Device Operation** entity

[Download example entity definition.](../examples/Device-Operation.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Device-Operation-context.jsonld"
    ],
    "id": "urn:ngsi-ld:DeviceOperation:27577638-bd8a-4732-b418-fc8b949a0b0f",
    "type": "DeviceOperation",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "device": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Device:2033a7c7-d31b-48e7-91c2-014dc426c29e"
    },
    "operationType": {
        "type": "Property",
        "value": [
            "fault"
        ]
    },
    "description": {
        "type": "Property",
        "value": "Backup battery needs replacement"
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
        "value": "ongoing"
    },
    "operator": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Person:fe018d4e-46f8-11e8-ae6b-df5577f85836"
    },
    "startedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "reportedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    },
    "addressedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-28T10:18:16Z"
    }
}
```
