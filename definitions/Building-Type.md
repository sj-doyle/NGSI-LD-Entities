# Building Type
This entity contains a harmonised description of a generic building type. This entity is associated with the vertical segments of smart home, smart cities, industry and related IoT applications. The building type includes a hierarchical structure that allows building types to be grouped in a flexible way.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| name | Property | The name of this BuildingType. | Mandatory |
| description | Property | A description for this BuildingType. | Recommended |
| root | Property | A logical indicator that this is the root of a BuildingType hierarchy. True indicates it is the root, false indicates that it is not the root. | Recommended |
| parentBuildingType | Relationship | References any higher level Building Type entities that this type is based on. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Building Type** entity

[Download context definition.](../examples/Building-Type-context.jsonld)

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
    "Relationship": "http://uri.etsi.org/ngsi-ld/Relationship"
}
```
## Example of Building Type Entity
The following is an example instance of the **Building Type** entity

[Download example entity definition.](../examples/Building-Type.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Building-Type-context.jsonld"
    ],
    "id": "urn:ngsi-ld:BuildingType:57b912ab-eb47-4cd5-bc9d-73abece1f1b3",
    "type": "BuildingType",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "name": {
        "type": "Property",
        "value": "House"
    },
    "description": {
        "type": "Property",
        "value": "Standard building type definition for a domestic house"
    },
    "root": {
        "type": "Property",
        "value": false
    },
    "parentBuildingType": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:BuildingType:4146335f-839f-4ff9-a575-6b4e6232b734"
    }
}
```
