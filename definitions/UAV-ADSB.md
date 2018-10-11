# UAV ADSB
This entity contains a harmonised description of a generic UAV Automatic Dependent Surveillance–Broadcast. This entity is primarily associated with the control and management of Unmanned Aerial Vehicles. Each UAVADSB instance will be related to a specific UAV instance.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| uav | Relationship | Reference to the UAV entity to which this broadcast message relates. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time of the DBS broadcast. | Mandatory |
| originatedByUAV | Property | A logical indicator of source of the message. True indicates it is the UAV itself, false indicates that it is a different source, a listening station software application or a different UAV. | Mandatory |
| originator | Relationship | Refers to a third party UAV instance or other entity (e.g. listening station) that reported the information in the case the message was not directly originated by the UAV. | Optional |
| UAVADSBroadcast | Property | A flight message describing the current flight status as a DBSB Message stored as a string of hexadecimal digits.

See http://mode-s.org/decode/adsb.html | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **UAV ADSB** entity

[Download context definition.](../examples/UAV-ADSB-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "uav": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/uav",
        "originatedByUAV": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/originatedbyuav",
        "originator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/originator",
        "UAVADSBroadcast": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/uavadsbroadcast"
    }
}
```
## Example of UAV ADSB Entity
The following is an example instance of the **UAV ADSB** entity

[Download example entity definition.](../examples/UAV-ADSB.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/UAV-ADSB-context.jsonld"
    ],
    "id": "urn:ngsi-ld:UAVADSB:1fa179a6-b507-4857-ad72-eb5513ef05c8",
    "type": "UAVADSB",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "uav": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAV:23821045-33d4-46ec-b777-98f461bf4856"
    },
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2016-08-23T10:18:16Z"
    },
    "originatedByUAV": {
        "type": "Property",
        "value": false
    },
    "originator": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAV:29935bbe-5922-11e8-9742-93bfb84686ec"
    },
    "UAVADSBroadcast": {
        "type": "Property",
        "value": "8D4840D6202CC371C32CE0576098"
    }
}
```
