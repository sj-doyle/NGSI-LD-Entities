# UAV State Vector
This entity contains a harmonised description of a generic UAV State Vector, which is an Interpretation and aggregation of Automatic Dependent Surveillance–Broadcast messages. This entity is primarily associated with the control and management of Unmanned Aerial Vehicles. Each UAVStateVector instance is related to a specific UAV instance.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| uav | Relationship | Reference to the UAV entity to which this state vector relates. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time of the state vector record. | Mandatory |
| originator | Relationship | Refers to a third party UAV instance or other entity (e.g. listening station) that reported the information in the case the message was not directly originated by the UAV. | Mandatory |
| stateVector | Property | A state vector describing the current flight status based on the definition of opensky-network.org StateVector and encoded in JSON.

See https://opensky-network.org/apidoc/javadoc/org/opensky/model/StateVector.html and https://opensky-network.org/apidoc/rest.html#response | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **UAV State Vector** entity

[Download context definition.](../examples/UAV-State-Vector-context.jsonld)

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
    "uav": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "originator": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "stateVector": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    }
}
```
## Example of UAV State Vector Entity
The following is an example instance of the **UAV State Vector** entity

[Download example entity definition.](../examples/UAV-State-Vector.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/UAV-State-Vector-context.jsonld"
    ],
    "id": "urn:ngsi-ld:UAVStateVector:920c304c-5929-11e8-a3c5-9bf25506b64a",
    "type": "UAVStateVector",
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
    "originator": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:UAV:29935bbe-5922-11e8-9742-93bfb84686ec"
    },
    "stateVector": {
        "type": "Property",
        "value": [
            [
                "ac90e7",
                "DAL2136",
                "United States",
                1526489909,
                1526489909,
                -92.1652,
                32.0335,
                9144,
                false,
                224.88,
                262.11,
                0,
                null,
                9525,
                "2272",
                false,
                0
            ],
            [
                "8000fd",
                "JAI384",
                "India",
                1526489893,
                1526489905,
                76.993,
                28.4104,
                1882.14,
                false,
                149.13,
                190.53,
                5.2,
                null,
                1821.18,
                "0504",
                false,
                0
            ],
            [
                "4caa1c",
                "AZA1291",
                "Ireland",
                1526489909,
                1526489909,
                11.1718,
                43.9226,
                10668,
                false,
                242.45,
                137.24,
                0.33,
                null,
                10713.72,
                "7454",
                false,
                0
            ]
        ]
    }
}
```
