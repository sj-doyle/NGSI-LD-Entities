# Subscription Service
This entity contains a harmonised description of a subscription service. This entity is primarily associated with the Smart Home/ Smart Building vertical segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| description | Property | The description of this service. | Mandatory |
| offer | Property | Encoded as Schema.org offer. https://schema.org/Offer | Recommended |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Subscription Service** entity

[Download context definition.](../examples/Subscription-Service-context.jsonld)

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
    "offer": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    }
}
```
## Example of Subscription Service Entity
The following is an example instance of the **Subscription Service** entity

[Download example entity definition.](../examples/Subscription-Service.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Subscription-Service-context.jsonld"
    ],
    "id": "urn:ngsi-ld:SubscriptionService:a1e76f95-c627-4ec4-86dc-483431d25352",
    "type": "SubscriptionService",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "description": {
        "type": "Property",
        "value": "Broadband supply service"
    },
    "offer": {
        "type": "Property",
        "priceCurrency": "USD",
        "price": 50,
        "description": "100 mbps fibre broadband service"
    }
}
```
