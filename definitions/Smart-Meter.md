# Smart Meter
This entity contains a harmonised description of a Smart Meter, generally applicable for Smart Homes, Industry, Cities and Agriculture. It is designed to be a base for smart meter observations

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | TemporalProperty | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | TemporalProperty | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| meterType | Property | The type of supply being metered e.g.: **Electricity, Gasoline, Water, Methane, Diesel.** | Mandatory |
| device | Relationship | Reference to the base IoT device definition for the smart meter to cover standard attributes such as serial number, manufacturer etc. | Mandatory |
| location | GeoProperty | The geo:json encoded GPS position where a fixed location Smart Meter is installed e.g. a home/ building. | Optional |
| photo | Property | A picture of the meter installation. Comprises the text string encoded from the binary data of a JPEG format photo of the meter. The binary data must be converted to ASCII text using the base64 encoding standard. | Recommended |
| place | Property | Alternate specification of the installation location for a fixed position Smart Meter | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Smart Meter** entity

[Download context definition.](../examples/Smart-Meter-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "meterType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/metertype",
        "device": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/device",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "photo": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/photo",
        "place": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/place"
    }
}
```
## Example of Smart Meter Entity
The following is an example instance of the **Smart Meter** entity

[Download example entity definition.](../examples/Smart-Meter.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Smart-Meter-context.jsonld"
    ],
    "id": "urn:ngsi-ld:SmartMeter:8ac0db56-9adf-11e8-ad67-e7308e2e8b15",
    "type": "SmartMeter",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "meterType": {
        "type": "Property",
        "value": "Electricity"
    },
    "device": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Device:7a0708f6-9668-11e8-8f77-abc2b62ebaac"
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
    "photo": {
        "type": "Property",
        "value": "iVBORw0KGgoAAAANSUhEUgAAAGcAAABkCAIAAAAUt...ErkJggg=="
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
