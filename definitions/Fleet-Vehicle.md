# Fleet Vehicle
This entity contains a harmonised description of a generic fleet vehicle such as a delivery vehicle, an ambulance or a postal vehicle. This entity is primarily associated with the vertical segment of the transport and logistics but may also be used many other related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| vehicle | Relationship | Reference to the related Vehicle entity instance that describes the core attributes of this Fleet Vehicle. | Mandatory |
| fleetVehicleType | Property | The type of the Vehicle for example (not limited to): **Taxi, Ambulance, Postal, Fire & Rescue, Delivery.** | Mandatory |
| operatingCompany | Property | Details of the organization that is operating this fleet vehicle. Based on Schema.org 'organization': https://schema.org/Organization | Mandatory |
| operator | Relationship | The usual operator/driver/keeper of this fleet vehicle encoded as a Schema.org 'person'. https://schema.org/Person

Should be omitted if there is no usual operator/driver/keeper. | Recommended |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Fleet Vehicle** entity

[Download context definition.](../examples/Fleet-Vehicle-context.jsonld)

```JavaScript
{
    "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
    "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
    "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
    "vehicle": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/vehicle",
    "fleetVehicleType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/fleetvehicletype",
    "operatingCompany": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operatingcompany",
    "operator": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/operator"
}
```
## Example of Fleet Vehicle Entity
The following is an example instance of the **Fleet Vehicle** entity

[Download example entity definition.](../examples/Fleet-Vehicle.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Fleet-Vehicle-context.jsonld"
    ],
    "id": "urn:ngsi-ld:FleetVehicle:630b8818-5aa2-11e8-91c6-bf6b90c0ad02",
    "type": "FleetVehicle",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "vehicle": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Vehicle:76a67054-5aa2-11e8-b0ee-43cfe58d3cd1"
    },
    "fleetVehicleType": {
        "type": "Property",
        "value": "Ambulance"
    },
    "operatingCompany": {
        "type": "Property",
        "name": "NHS"
    },
    "operator": {
        "type": "Relationship",
        "givenName": "John Smith",
        "jobTitle": "Ambulance Operator",
        "object": "urn:ngsi-ld:Person:fe018d4e-46f8-11e8-ae6b-df5577f85836"
    }
}
```
