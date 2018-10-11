# Product Type
This entity contains a harmonised description of a generic product type. This entity is primarily associated with the product supply chain verticals and related IoT applications. The ProductType includes a hierarchical structure that allows product types to be grouped in a flexible way.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| name | Property | The name of this product type. | Mandatory |
| description | Property | A description of this product type. | Mandatory |
| root | Property | A logical indicator that this product is the root of the ProductType hierarchy. Logical true indicates it is the root. | Mandatory |
| parentType | Relationship | Reference to the parent product type i.e. immediately above the entity in the hierarchy. | Optional |
| childrenTypes | Relationship | Reference to child product types i.e. immediately below this entity in the hierarchy. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Product Type** entity

[Download context definition.](../examples/Product-Type-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "root": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/root",
        "parentType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/parenttype",
        "childrenTypes": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/childrentypes"
    }
}
```
## Example of Product Type Entity
The following is an example instance of the **Product Type** entity

[Download example entity definition.](../examples/Product-Type.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Product-Type-context.jsonld"
    ],
    "id": "urn:ngsi-ld:ProductType:8bd39518-041d-4a9a-8c0c-0bf15d5f07f1",
    "type": "ProductType",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "name": {
        "type": "Property",
        "value": "Soft Fruits"
    },
    "description": {
        "type": "Property",
        "value": "Soft edible fruits"
    },
    "root": {
        "type": "Property",
        "value": true
    },
    "parentType": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:ProductType:66edbb59-90ea-4757-aa06-5a5b95675092"
    },
    "childrenTypes": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:ProductType:5d4fcc9e-590e-11e8-ae23-3f2d135d7537",
            "urn:ngsi-ld:ProductType:625c4ffa-590e-11e8-b3bf-17a3afd2e135",
            "urn:ngsi-ld:ProductType:682b48f0-590e-11e8-a107-d3709d55a369"
        ]
    }
}
```
