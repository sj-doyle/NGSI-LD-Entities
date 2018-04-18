# Vehicle Type
This entity contains a harmonised description of a vehicleType it forms part of the description of a Vehicle. This entity is primarily associated with the Automotive vertical segment but might also be relevant to Industry, Smart City and Agriculture related IoT applications. Where practicable https://schema.org/Vehicle naming conventions have been adopted.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| model | Property | The vehicle model identifier. | Mandatory |
| category | Property | The vehicle category identifier. | Mandatory |
| manufacturer | Property | The manufacturer’s identifier. | Mandatory |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Vehicle Type** entity

[Download context definition.](../examples/Vehicle-Type-context.jsonld)

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
    "Property": "http://etsi.org/nsgi-ld/Property"
}
```
## Example of Vehicle Type Entity
The following is an example instance of the **Vehicle Type** entity

[Download example entity definition.](../examples/Vehicle-Type.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://example.com/contexts/vehicle-type.jsonld"
    ],
    "id": "urn:ngsi-ld:VehicleType:33253089-9cea-4227-889e-61950965f6f9",
    "type": "VehicleType",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "model": {
        "type": "Property",
        "value": "M Class"
    },
    "category": {
        "type": "Property",
        "value": "SUV"
    },
    "manufacturer": {
        "type": "Property",
        "value": "Mercedes Benz"
    }
}
```
