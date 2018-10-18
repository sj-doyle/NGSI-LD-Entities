# Recogniser Simple Result
This entity contains a generic model for a simple result output from an AI/ Machine Learning based image/audio recogniser

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| recogniserInput | Relationship | Reference to the Recogniser Input that this result is related to. | Mandatory |
| processedAt | TemporalProperty | Indicates the date/time when the processing completed. | Mandatory |
| processedDuration | TemporalProperty | Indicates the elapsed time required to process the input (in hours, minutes and seconds). | Optional |
| result | Property | The output from the recogniser process. This can be application specific and is expected to be either text (such as the output from classification) or a numeric value (such as the output from regression). If there is a more complex result output e.g. for multiple features the RecogniserResult entity is recommended instead of this entity. | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Recogniser Simple Result** entity

[Download context definition.](../examples/Recogniser-Simple-Result-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "recogniserInput": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/recogniserinput",
        "processedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/processedat",
        "processedDuration": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/processedduration",
        "result": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/result"
    }
}
```
## Example of Recogniser Simple Result Entity
The following is an example instance of the **Recogniser Simple Result** entity

[Download example entity definition.](../examples/Recogniser-Simple-Result.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Recogniser-Simple-Result-context.jsonld"
    ],
    "id": "urn:ngsi-ld:RecogniserSimpleResult:4ec233e6-a135-11e8-8235-e73012e70d05",
    "type": "RecogniserSimpleResult",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "recogniserInput": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:RecogniserInput:4aad67e8-9ae2-11e8-a2a9-f77b8d50602c"
    },
    "processedAt": {
        "type": "TemporalProperty",
        "value": "2018-05-04T10:18:16Z"
    },
    "processedDuration": {
        "type": "TemporalProperty",
        "value": "000:01:35"
    },
    "result": {
        "type": "Property",
        "value": "Alert"
    }
}
```
