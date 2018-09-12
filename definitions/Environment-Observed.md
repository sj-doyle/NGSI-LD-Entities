# Environment Observed
This entity contains a harmonised description of the environmental conditions observed at a particular location and time. This entity is primarily associated with the vertical segment of the environment and agriculture but may also be used in smart home, smart cities, industry and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| location | GeoProperty | The geo location (point/ polygon) that the associated observations are related to. | Mandatory |
| POIs | Relationship | A reference to associated Points of Interest (e.g. monitoring stations) that the associated observations are related to. | Recommended |
| weatherObserved | Relationship | A reference to associated WeatherObserved entities. | Optional |
| airQualityObserved | Relationship | A reference to associated AirQualityObserved entities. | Optional |
| waterQualityObserved | Relationship | A reference to associated WaterQualityObserved entities. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Environment Observed** entity

[Download context definition.](../examples/Environment-Observed-context.jsonld)

```JavaScript
{
    "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
    "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
    "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
    "POIs": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/pois",
    "weatherObserved": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/weatherobserved",
    "airQualityObserved": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/airqualityobserved",
    "waterQualityObserved": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/waterqualityobserved"
}
```
## Example of Environment Observed Entity
The following is an example instance of the **Environment Observed** entity

[Download example entity definition.](../examples/Environment-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Environment-Observed-context.jsonld"
    ],
    "id": "urn:ngsi-ld:EnvironmentObserved:33f02632-74f4-4c96-9ba1-e26945de9481",
    "type": "EnvironmentObserved",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -104.99404,
                39.75621
            ]
        }
    },
    "POIs": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:POI:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84",
            "urn:ngsi-ld:POI:42dcd5ea-46db-11e8-bea0-772aba733f93",
            "urn:ngsi-ld:POI:4912d78e-46db-11e8-8572-ab2b8e55590b"
        ]
    },
    "weatherObserved": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:WeatherObserved:fae29f4c-0691-4bab-bef8-ad1cd165cc28",
            "urn:ngsi-ld:WeatherObserved:1c7a2711-ae38-4ea9-8f9f-627067067d53"
        ]
    },
    "airQualityObserved": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:AirQualityObserved:4b8b09c9-ce54-46de-8067-5591e02d8f29",
            "urn:ngsi-ld:WeatherObserved:08a14933-b44d-4297-b2d2-2c3f3844012e"
        ]
    },
    "waterQualityObserved": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:WeatherObserved:68a83e68-61e6-4e3c-975c-5b301c184ca6",
            "urn:ngsi-ld:WeatherObserved:b01518e3-2b60-4bbd-9783-3af0d660349e"
        ]
    }
}
```
