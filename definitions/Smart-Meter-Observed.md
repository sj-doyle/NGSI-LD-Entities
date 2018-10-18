# Smart Meter Observed
This entity contains a harmonised description of a Smart Meter Observation, generally applicable for Smart Homes, Industry, Cities and Agriculture.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| smartMeter | Relationship | Reference to the Smart Meter that this observation relates to. | Mandatory |
| location | GeoProperty | The geo:json encoded current GPS position of the Smart Meter. The main purpose for this is with meters that are installed for example on mobile fuel supply vehicles (such as for heating oil). | Optional |
| observedAt | TemporalProperty | Indicates the date/time the most recent observation was recorded. | Mandatory |
| totalConsumption | Property | The total amount of product supplied as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Mandatory |
| photo | Property | A picture of the meter showing the reading. Comprises the text string encoded from the binary data of a JPEG format photo of the meter. The binary data must be converted to ASCII text using the base64 encoding standard. | Recommended |
| peakConsumption | Property | The total amount of product supplied during 'peak' hours (particularly relevant to Electricity supply) as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Optional |
| offPeakConsumption | Property | The total amount of product supplied during 'off-peak' hours (particularly relevant to Electricity supply) as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Optional |
| powerFactor | Property | Relevant to 3-Phase electricity supplies often used in industry - the power factor ranges from -1 to +1 depending on the net balance between capacitive and inductive loads. If used this measures the average power factor since meter installation. | Optional |
| place | Property | Confirmation of the current location for the Smart Meter. This may be used to confirm a delivery address for example for the supply of fuel/ gas product. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Smart Meter Observed** entity

[Download context definition.](../examples/Smart-Meter-Observed-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "smartMeter": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/smartmeter",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "totalConsumption": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/totalconsumption",
        "photo": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/photo",
        "peakConsumption": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/peakconsumption",
        "offPeakConsumption": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/offpeakconsumption",
        "powerFactor": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/powerfactor",
        "place": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/place"
    }
}
```
## Example of Smart Meter Observed Entity
The following is an example instance of the **Smart Meter Observed** entity

[Download example entity definition.](../examples/Smart-Meter-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Smart-Meter-Observed-context.jsonld"
    ],
    "id": "urn:ngsi-ld:SmartMeterObserved:bc7930aa-965f-11e8-b327-2be817efd126",
    "type": "SmartMeterObserved",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "smartMeter": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:SmartMeter:8ac0db56-9adf-11e8-ad67-e7308e2e8b15"
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
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2018-05-04T10:18:16Z"
    },
    "totalConsumption": {
        "type": "Property",
        "value": 1076.5,
        "unitCode": "KWH"
    },
    "photo": {
        "type": "Property",
        "value": "iVBORw0KGgoAAAANSUhEUgAAAGcAAABkCAIAAAAUt...ErkJggg=="
    },
    "peakConsumption": {
        "type": "Property",
        "value": 976.5,
        "unitCode": "KWH"
    },
    "offPeakConsumption": {
        "type": "Property",
        "value": 100.0,
        "unitCode": "KWH"
    },
    "powerFactor": {
        "type": "Property",
        "value": 1.05,
        "unitCode": "C62"
    },
    "place": {
        "type": "Property",
        "value": {
            "@type": "https://schema.org/PostalAddress",
            "addressLocality": "London",
            "postalCode": "EC4N 8AF",
            "streetAddress": "25 Walbrook"
        }
    }
}
```
