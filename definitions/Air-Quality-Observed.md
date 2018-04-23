# Air Quality Observed
This entity contains a harmonised description of the air quality observed at a particular location and time. This entity is primarily associated with the vertical segment of the environment and may also be used in smart homes, smart cities, agriculture, industry and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| POIs | Relationship | A reference to associated Points of Interest (e.g. monitoring station) that this observation is related to. | Optional |
| devices | Relationship | Reference to the IoT devices (i.e. sensors) which generated the air quality observations. | Optional |
| location | GeoProperty | The geo location (point/ polygon) for this observation. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time the fault was detected or identified. | Recommended |
| AQI | Property | Indicates the subjective Air Quality Index nominally according to a specified standard such as the US EPA (https://www3.epa.gov/airnow/aqi_brochure_02_14.pdf). | Optional |
| CO | Property | Indicates the level of observed Carbon Monoxide nominally in units of microgrammes per cubic metre. | Optional |
| NO | Property | Indicates the level of observed Nitrogen Monoxide nominally in units of microgrammes per cubic metre. | Optional |
| NO2 | Property | Indicates the level of observed Nitrogen Dioxide nominally in units of microgrammes per cubic metre. | Optional |
| NOx | Property | Indicates the level of observed Nitrous Oxides (excluding Nitrogen Dioxide) nominally in units of microgrammes per cubic metre. | Optional |
| O3 | Property | Indicates the level of observed Ozone nominally in units of microgrammes per cubic metre. | Optional |
| PM2.5 | Property | Indicates the level of observed Particulate Matter (under 2.5 microns in size) nominally in units of microgrammes per cubic metre. | Optional |
| PM10 | Property | Indicates the level of observed Particulate Matter (under 10 microns in size)  nominally in units of microgrammes per cubic metre. | Optional |
| SO2 | Property | Indicates the level of observed Suplhur Dioxide nominally in units of microgrammes per cubic metre. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Air Quality Observed** entity

[Download context definition.](../examples/Air-Quality-Observed-context.jsonld)

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
    "GeoProperty": "http://uri.etsi.org/ngsi-ld/GeoProperty",
    "observedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/observedAt",
        "@type": "DateTime"
    }
}
```
## Example of Air Quality Observed Entity
The following is an example instance of the **Air Quality Observed** entity

[Download example entity definition.](../examples/Air-Quality-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Air-Quality-Observed.jsonld"
    ],
    "id": "urn:ngsi-ld:AirQualityObserved:c9f32b35-a185-48e2-835f-c521efc294ab",
    "type": "AirQualityObserved",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "POIs": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:POI:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84",
            "urn:ngsi-ld:POI:42dcd5ea-46db-11e8-bea0-772aba733f93",
            "urn:ngsi-ld:POI:4912d78e-46db-11e8-8572-ab2b8e55590b"
        ]
    },
    "devices": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Device:e8bbad7e-46db-11e8-b23a-8bb626923249",
            "urn:ngsi-ld:Device:ef379c6c-46db-11e8-90ae-d3c85fee58c1",
            "urn:ngsi-ld:Device:f581d088-46db-11e8-96f8-33f0aaf9d24d",
            "urn:ngsi-ld:0be5c6ea-46dc-11e8-b16b-0ff93e4638ff"
        ]
    },
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
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2017-05-04T10:18:16Z"
    },
    "AQI": {
        "type": "Property",
        "value": 238,
        "unitText": "US EPA AQI",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "CO": {
        "type": "Property",
        "value": 0.8,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NO": {
        "type": "Property",
        "value": 137,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NO2": {
        "type": "Property",
        "value": 63,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NOx": {
        "type": "Property",
        "value": 273,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "O3": {
        "type": "Property",
        "value": 300,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "PM2.5": {
        "type": "Property",
        "value": 187,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "PM10": {
        "type": "Property",
        "value": 50,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "SO2": {
        "type": "Property",
        "value": 7,
        "unitCode": "GQ",
        "unitText": "microgramme per cubic metre",
        "observedAt": "2017-05-04T12:30:00Z"
    }
}
```
