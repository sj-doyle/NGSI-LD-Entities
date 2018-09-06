# Vehicle
This entity contains a harmonised description of a Vehicle. This entity is primarily associated with the Automotive vertical segment but might also be relevant to Industry, Smart City and Agriculture related IoT applications. Where practicable https://schema.org/Vehicle naming conventions have been adopted.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| vehicleType | Relationship | Reference to the type of the vehicle entity. | Mandatory |
| fuelType | Property | A choice from an enumerated list describing the power source. One of: **gasoline, petrol(unleaded), petrol(leaded), petrol, diesel, electric, hydrogen, lpg autogas, cng, biodiesel, ethanol, hybrid electric/petrol, hybrid electric/diesel, other** | Optional |
| displacement | Property | A number indicating the cylinder capacity of the engine nominally in litres. | Optional |
| fuelEfficiency | Property | The efficiency of the vehicle expressed as kilometres per litre or miles per gallon. | Optional |
| vehicleModelDate | TemporalProperty | Indicates the date when the vehicle model was released in ISO 8601 format. | Optional |
| dateDiscontinued | TemporalProperty | Indicates the date when the vehicle model was discontinued in ISO 8601 format. | Optional |
| vehicleIdentificationNumber | Property | The Vehicle Identification Number (VIN) of the vehicle. | Optional |
| mileageFromOdometer | Property | The total distance the car has travelled according to the on-board odometer in kilometres (unitCode KMT) or miles (unitCode SMI). If unitCode is omitted the units are assumed to be kilometres. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Vehicle** entity

[Download context definition.](../examples/Vehicle-context.jsonld)

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
    "vehicleType": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "fuelType": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "displacement": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "fuelEfficiency": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "vehicleModelDate": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "dateDiscontinued": {
        "@id": "http://uri.etsi.org/ngsi-ld/TemporalProperty",
        "@type": "TemporalProperty"
    },
    "vehicleIdentificationNumber": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "mileageFromOdometer": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    }
}
```
## Example of Vehicle Entity
The following is an example instance of the **Vehicle** entity

[Download example entity definition.](../examples/Vehicle.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Vehicle-context.jsonld"
    ],
    "id": "urn:ngsi-ld:Vehicle:1fa179a6-b507-4857-ad72-eb5513ef05c6",
    "type": "Vehicle",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "vehicleType": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:VehicleType:33253089-9cea-4227-889e-61950965f6f9"
    },
    "fuelType": {
        "type": "Property",
        "value": "Diesel"
    },
    "displacement": {
        "type": "Property",
        "value": 3,
        "unitCode": "LTR"
    },
    "fuelEfficiency": {
        "type": "Property",
        "value": 10.4,
        "unitCode": "km/l"
    },
    "vehicleModelDate": {
        "type": "TemporalProperty",
        "value": "2016-08-18T10:18:16Z"
    },
    "dateDiscontinued": {
        "type": "TemporalProperty",
        "value": "2016-08-23T10:18:16Z"
    },
    "vehicleIdentificationNumber": {
        "type": "Property",
        "value": "2T2GK31U08C041124"
    },
    "mileageFromOdometer": {
        "value": 33015,
        "type": "Property",
        "unitCode": "SMI",
        "observedAt": "2016-08-23T10:18:16Z"
    }
}
```
