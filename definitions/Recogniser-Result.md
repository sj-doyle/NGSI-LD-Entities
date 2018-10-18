# Recogniser Result
This entity contains a generic model for the resulting outputs from an AI/ Machine Learning based image/audio recogniser where multiple features are processed.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| input | Relationship | Reference to the input that was used to develop this result, this would usually be a 'RecogniserInput' for a direct source or a 'RecogniserOutput' in the case that a previous stage of recognition is being used. | Mandatory |
| processedAt | TemporalProperty | Indicates the date/time when the processing completed. | Mandatory |
| processedDuration | TemporalProperty | Indicates the elapsed time required to process the input (in hours, minutes and seconds). | Optional |
| recognisedFeatures | Property | The 'features' that were recognised from the input data. This should be an array of objects representing the output from the recognition process, though the contents of each result object will be specific to the recognition process. The actual contents of this will depend on the design of the recognition engine. See additional notes below. | Mandatory |


### recognisedFeatures sub-fields & notes
 the purpose of the *recognisedFeatures* property is to hold any of the results from the recognition process. Since recognition tasks are application specific this means that there will be various types of response that need to be supported. Also whilst certain recognition processes might identify single values such as the classification of an object, or a single numerical value, in the general case the recognition process could be generating multiple results and this is why this property is coded as an array.

 In the case that only a simple result or action is produced the RecogniserSimpleResult entity can be used rather than this more generic model.

 It is recommended that certain sub-field names have defined meanings within the recognition results. For example

 + *classification* designates the corresponding value is a result of classifying the input into one of a finite set of pre-defined 'named' classifications. This will usually have a text value.
 + *quantity* designates the corresponding value as a result of determining a numeric value from the source - the result will be a real (numeric) value.
 + *text* indicates that the recognition process has identified a textual value, this could be from either voice or image recognition.
 + *action* indicates that a specified action has been determined during the recognition process. This could be a human or machine readable textual value, or a numeric action code.
 + *confidence* designates the corresponding confidence level in the classification, with values between 0 (no confidence) and 1 (100% confidence).
 + *startTimecode* relevant to audio recognition and indicates the starting timecode (*hhh:mm:ss.ccc* - hours, minutes, seconds and milliseconds) of a recognised word in the *text* field.
 + *endTimecode* relevant to audio recognition and indicates the ending timecode (*hhh:mm:ss.ccc* - hours, minutes, seconds and milliseconds) of a recognised word in the *text* field.
 + *polygon* relevant to image recognition this indicates the area of the source frame that contains the recognised feature. This will be an array of pixel positions representing a closed polygon of 3 or more sides e.g. *[[x1,y1],[x2,y2],[x3,y3],[x4,y4],[x1,y1]]* relative to the bottom left of the source image.
 + *featureMediaUri* reference to the section of the image or audio (corresponding with *polygon* for images or *startTimecode*:*endTimecode* for audio) that the feature was recognised in, with the media content referenced by a URI. The expected use for this is in validation that the recognition result is correct or feedback to users.

 Custom fields that have more application specific uses can also be added to the above list as necessary but should use different field names.

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Recogniser Result** entity

[Download context definition.](../examples/Recogniser-Result-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "input": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/input",
        "processedAt": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/processedat",
        "processedDuration": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/processedduration",
        "recognisedFeatures": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/recognisedfeatures"
    }
}
```
## Example of Recogniser Result Entity
The following is an example instance of the **Recogniser Result** entity

[Download example entity definition.](../examples/Recogniser-Result.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Recogniser-Result-context.jsonld"
    ],
    "id": "urn:ngsi-ld:RecogniserResult:0df4c88a-9ae4-11e8-965d-0f9a6c9e5225",
    "type": "RecogniserResult",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "input": {
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
    "recognisedFeatures": {
        "type": "Property",
        "value": [
            {
                "classification": "car",
                "registration": "8128",
                "confidence": 0.98,
                "action": "none"
            }
        ]
    }
}
```
