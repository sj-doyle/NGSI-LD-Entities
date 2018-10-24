# UAV Event
The UAVEvent records the incursion of a specific UAV into or near protected airspace or locations. It also records the control measure taken. This entity is primarily associated with UAV command and control and related UAV transport applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | TemporalProperty | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | TemporalProperty | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| uav | Relationship | Reference to the UAV entity to which this event relates. | Mandatory |
| originator | Relationship | Refers to a third party UAV instance or other entity (e.g. listening station) that reported the information in the case the event was not directly originated by the UAV. | Optional |
| location | GeoProperty | The geo:json encoded GPS position of the UAV when the event was triggered. | Mandatory |
| elevation | Property | The elevation of the UAV (relative to ground level at the specified location). Specify value and units of measure. | Mandatory |
| startAt | DateTime | Indicates the date/time of when the event started. | Mandatory |
| endAt | DateTime | Indicates the date/time of when the event ended (if it has ended). | Recommended |
| eventType | Property | The type of the UAV event, a choice from: **illegal flight , close to unpermitted airspace, overspeed, over height, illegal work** | Recommended |
| description | Property | A description for this event. | Recommended |
| eventResult | Property | The handling result of the event, a choice from: **logged, notify, alarm, force land, force back, force hover** | Recommended |
| <em>eventStart</em> | <em>DateTime</em> | <em>Indicates the date/time of when the event started.<br/><br/>Note that this is advisory and the actual time the operation starts may be before or after the planned start.<br/><br/>Note this field was defined for use with NGSIv2 and is now deprecated. For new entities and applications replace with **startAt**</em> | <em>Deprecated</em> |
| <em>eventEnd</em> | <em>DateTime</em> | <em>Indicates the date/time of when the event ended (if it has ended).<br/><br/>Note that this is advisory and the actual time the operation finishes may be before or after the planned end.<br/><br/>Note this field was defined for use with NGSIv2 and is now deprecated. For new entities and applications replace with **endAt**</em> | <em>Deprecated</em> |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **UAV Event** entity

[Download context definition.](../examples/UAV-Event-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "uav": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/uav",
        "originator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/originator",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "elevation": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/elevation",
        "startAt": {
            "@type": "DateTime",
            "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/startat"
        },
        "endAt": {
            "@type": "DateTime",
            "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/endat"
        },
        "eventType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/eventtype",
        "description": "https://schema.org/description",
        "eventResult": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/eventresult",
        "eventStart": {
            "@type": "DateTime",
            "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/eventstart"
        },
        "eventEnd": {
            "@type": "DateTime",
            "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/eventend"
        }
    }
}
```
## Example of UAV Event Entity
The following is an example instance of the **UAV Event** entity

[Download example entity definition.](../examples/UAV-Event.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/UAV-Event-context.jsonld"
    ],
    "id": "urn:ngsi-ld:UAVEvent:85df05a8-5922-11e8-ad9c-d7fa968d409d",
    "type": "UAVEvent",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "uav": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAV:23821045-33d4-46ec-b777-98f461bf4856"
    },
    "originator": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAV:23821045-33d4-46ec-b777-98f461bf4856"
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
    "startAt": {
        "type": "Property",
        "value": "2016-08-23T10:18:16Z"
    },
    "endAt": {
        "type": "Property",
        "value": "2016-08-23T10:19:16Z"
    },
    "eventType": {
        "type": "Property",
        "value": "over height"
    },
    "description": {
        "type": "Property",
        "value": "The UAV is flying over a mandatory height limit"
    },
    "eventResult": {
        "type": "Property",
        "value": "force back"
    }
}
```
