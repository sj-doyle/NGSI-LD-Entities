# Device Model
This entity contains a harmonised description of a generic device model and is therefore applicable to all IoT segments and related IoT applications. The Device Model includes an optional hierarchical structure that allows device types to be grouped in a flexible way.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | TemporalProperty | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | TemporalProperty | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| name | Property | The name of this DeviceModel. | Mandatory |
| doc | Property | Reference to Product Data Sheet or other manufacturer’s documentation about this device model including where relevant, details of the accuracy, trueness, precision and units of measure. | Recommended |
| category | Property | A choice from an enumerated list defining the category of this device including: **sensor, actuator, meter, appliance, heater, chiller, lighting, boiler, vessel, airHandlingUnit, consumer, other.** | Optional |
| description | Property | Description of this device model. | Recommended |
| manufacturerName | Property | The name of manufacturer of this DeviceModel. | Recommended |
| brandName | Property | The brand name of this DeviceModel. | Recommended |
| root | Property | A logical indicator that this DeviceModel is the root of a DeviceModel hierarchy. True indicates it is the root, false indicates that it is not the root. | Mandatory |
| deviceModelParent | Relationship | References any higher level Device Model that this device model is based on. | Optional |
| deviceModelChildren | Relationship | References any lower level Device Models that are based on this device model. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Device Model** entity

[Download context definition.](../examples/Device-Model-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "name": "https://schema.org/name",
        "doc": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/doc",
        "category": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/category",
        "description": "https://schema.org/description",
        "manufacturerName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/manufacturername",
        "brandName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/brandname",
        "root": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/root",
        "deviceModelParent": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/devicemodelparent",
        "deviceModelChildren": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/devicemodelchildren"
    }
}
```
## Example of Device Model Entity
The following is an example instance of the **Device Model** entity

[Download example entity definition.](../examples/Device-Model.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Device-Model-context.jsonld"
    ],
    "id": "urn:ngsi-ld:DeviceModel:ba2d4fd9-f57f-4610-a589-2d52670d14f3",
    "type": "DeviceModel",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "name": {
        "type": "Property",
        "value": "Sensor Model 501"
    },
    "doc": {
        "type": "Property",
        "value": {
            "@value": "https://example.com",
            "@type": "https://schema.org/url"
        }
    },
    "category": {
        "type": "Property",
        "value": [
            "sensor"
        ]
    },
    "description": {
        "type": "Property",
        "value": "Monomatics All Weather Temperature Sensor."
    },
    "manufacturerName": {
        "type": "Property",
        "value": "ACME Manufacturing, Inc."
    },
    "brandName": {
        "type": "Property",
        "value": "SuperWidgets"
    },
    "root": {
        "type": "Property",
        "value": false
    },
    "deviceModelParent": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:DeviceModel:29477bba-46f6-11e8-9ebe-979a9513bf23"
    },
    "deviceModelChildren": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:DeviceModel:95051122-58f9-11e8-85ac-07519c4f0770",
            "urn:ngsi-ld:DeviceModel:9a76da28-58f9-11e8-b59c-2bc9949dfc9e",
            "urn:ngsi-ld:DeviceModel:a0b87360-58f9-11e8-80a3-4373f857494b"
        ]
    }
}
```
