# Water Quality Observed
This entity contains a harmonised description of the water quality at a particular location and time. This entity is primarily associated with the vertical segments of agricultural and environment and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| POIs | Relationship | A reference to associated Points of Interest (e.g. monitoring station, body of water) that this observation is related to. | Recommended |
| devices | Relationship | Reference to the IoT devices (i.e. sensors) which generated the water quality observations. | Recommended |
| location | GeoProperty | The geo location (point/ polygon) for this observation. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time the observation was recorded. | Mandatory |
| depth | Property | Depth below surface level where the observation was taken, nominally in metres. | Optional |
| pressure | Property | Hydrostatic pressure where the observation was taken, nominally in Hector Pascals. | Optional |
| conductivity | Property | Electrical conductivity, nominally in Siemens/metre. | Optional |
| conductance | Property | Specific conductivity at 25 degrees Celsius, nominally in Siemens/metre. | Optional |
| temperature | Property | The water temperature, nominally in degrees Celsius. | Optional |
| tss | Property | Total suspended solids. | Optional |
| tds | Property | Total dissolved solids. | Optional |
| turbidity | Property | Amount of light scattered by particles in the water column. | Optional |
| salinity | Property | Derived from the conductivity measurement, nominally reported as parts per thousand. | Optional |
| pH | Property | pH measurement (typically a number between 0 and 14). | Optional |
| orp | Property | Oxidation-Reduction potential, nominally reported as milli-volts (mV). | Optional |
| cdom | Property | Color dissolved organic matter. | Optional |
| Chla | Property | Concentration of chlorophyll A. | Optional |
| Cl | Property | Concentration of chlorides. | Optional |
| CO | Property | The level of free non-compound carbon monoxide present. ( | Optional |
| CO2 | Property | The level of free non-compound carbon dioxide present. | Optional |
| Hg | Property | The level of compound mercury present. | Optional |
| NH3 | Property | Concentration of free ammonia. | Optional |
| NH4 | Property | Concentration of ammonium (ions). | Optional |
| NO3 | Property | Concentration of nitrates. | Optional |
| O2 | Property | The level of free non-compound oxygen present. | Optional |
| PC | Property | Concentration of pigment phycocyanin which can be measured to estimate cyanobacteria concentrations specifically. | Optional |
| PE | Property | Concentration of pigment phycoerythrin which can be measured to estimate cyanobacteria concentrations specifically. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Water Quality Observed** entity

[Download context definition.](../examples/Water-Quality-Observed-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "POIs": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/pois",
        "devices": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/devices",
        "depth": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/depth",
        "pressure": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/pressure",
        "conductivity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/conductivity",
        "conductance": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/conductance",
        "temperature": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/temperature",
        "tss": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/tss",
        "tds": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/tds",
        "turbidity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/turbidity",
        "salinity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/salinity",
        "pH": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/ph",
        "orp": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/orp",
        "cdom": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/cdom",
        "Chla": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/chla",
        "Cl": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/cl",
        "CO": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/co",
        "CO2": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/co2",
        "Hg": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/hg",
        "NH3": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/nh3",
        "NH4": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/nh4",
        "NO3": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/no3",
        "O2": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/o2",
        "PC": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/pc",
        "PE": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/pe"
    }
}
```
## Example of Water Quality Observed Entity
The following is an example instance of the **Water Quality Observed** entity

[Download example entity definition.](../examples/Water-Quality-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Water-Quality-Observed-context.jsonld"
    ],
    "id": "urn:ngsi-ld:WaterQualityObserved:72a30ca8-888e-49a2-8d8d-a5bebc19e98b",
    "type": "WaterQualityObserved",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "POIs": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:POI:2f578c8c-59ae-11e8-be5d-eb00d5850710",
            "urn:ngsi-ld:POI:350d5b2a-59ae-11e8-afac-7b08447a9507",
            "urn:ngsi-ld:POI:3b154be0-59ae-11e8-a97d-9b0e9854e167"
        ]
    },
    "devices": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:Device:4514d07a-59ae-11e8-8d8d-8fb340a9451f",
            "urn:ngsi-ld:Device:4bdbd926-59ae-11e8-a29d-1f6336c78c14",
            "urn:ngsi-ld:Device:52890d20-59ae-11e8-8449-ef9315a0a3ca",
            "urn:ngsi-ld:581fc4e0-59ae-11e8-99fe-17206cbbcec7"
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
    "depth": {
        "type": "Property",
        "value": 4,
        "unitCode": "MTR",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "pressure": {
        "type": "Property",
        "value": 1020.2,
        "unitCode": "A97",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "conductivity": {
        "type": "Property",
        "value": 10,
        "unitCode": "D10",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "conductance": {
        "type": "Property",
        "value": 25,
        "unitCode": "SIE",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "temperature": {
        "type": "Property",
        "value": 15,
        "unitCode": "CEL",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "tss": {
        "type": "Property",
        "value": 200,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "tds": {
        "type": "Property",
        "value": 150,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "turbidity": {
        "type": "Property",
        "value": 343,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "salinity": {
        "type": "Property",
        "value": 220,
        "unitCode": "NX",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "pH": {
        "type": "Property",
        "value": 5,
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "orp": {
        "type": "Property",
        "value": 210,
        "unitCode": "2Z",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "cdom": {
        "type": "Property",
        "value": 22,
        "unitCode": "RFU",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "Chla": {
        "type": "Property",
        "value": null,
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "Cl": {
        "type": "Property",
        "value": 11,
        "unitCode": "H29",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "CO": {
        "type": "Property",
        "value": 40,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "CO2": {
        "type": "Property",
        "value": 1,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "Hg": {
        "type": "Property",
        "value": 0.2,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NH3": {
        "type": "Property",
        "value": 0.03,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NH4": {
        "type": "Property",
        "value": 0.02,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "NO3": {
        "type": "Property",
        "value": 1,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "O2": {
        "type": "Property",
        "value": 50,
        "unitCode": "M1",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "PC": {
        "type": "Property",
        "value": 52,
        "unitCode": "H29",
        "observedAt": "2017-05-04T12:30:00Z"
    },
    "PE": {
        "type": "Property",
        "value": 66,
        "unitCode": "H29",
        "observedAt": "2017-05-04T12:30:00Z"
    }
}
```
