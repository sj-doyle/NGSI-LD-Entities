# Subscriber
This entity contains a harmonised description of a subscriber to a service. This entity is primarily associated with the Smart Home/ Smart Buildings vertical segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| subscription | Relationship | Reference to the associated service subscription | Mandatory |
| startAt | TemporalProperty | The start timestamp for the corresponding subscription service. | Recommended |
| endAt | TemporalProperty | The end timestamp for the corresponding subscription service. | Recommended |
| category | Property | The category of subscription. One selection from an enumerated list including: **prepay, postpay, utility, broadband, electric, gas, heat, water, landline, mobile, tv, security, financial, energy management, other.** | Optional |
| users | Relationship | References to those persons or organisations that will be using the subscription.

Corresponds to a Schema.org person or organization.

https://schema.org/Person

https://schema.org/Organization | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Subscriber** entity

[Download context definition.](../examples/Subscriber-context.jsonld)

```JavaScript
{
    "source": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "@type": "Property"
    },
    "dataProvider": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "@type": "Property"
    },
    "entityVersion": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "@type": "Property"
    },
    "subscription": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/subscription",
        "@type": "Relationship"
    },
    "startAt": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/startat",
        "@type": "TemporalProperty"
    },
    "endAt": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/endat",
        "@type": "TemporalProperty"
    },
    "category": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/category",
        "@type": "Property"
    },
    "users": {
        "@id": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/users",
        "@type": "Relationship"
    }
}
```
## Example of Subscriber Entity
The following is an example instance of the **Subscriber** entity

[Download example entity definition.](../examples/Subscriber.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Subscriber-context.jsonld"
    ],
    "id": "urn:ngsi-ld:Subscriber:c1716dea-6a4d-4171-a733-916123942f09",
    "type": "Subscriber",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "subscription": {
        "type": "Relationship",
        "value": "urn:ngsi-ld:SubscriptionService:65b1ccb0-ee32-41c1-9746-7ba83fb0f0f1"
    },
    "startAt": {
        "type": "TemporalProperty",
        "value": "2016-08-22T10:18:16Z"
    },
    "endAt": {
        "type": "TemporalProperty",
        "value": "2017-08-22T23:59:59Z"
    },
    "category": {
        "type": "Property",
        "value": "utility"
    },
    "users": {
        "type": "Relationship",
        "value": [
            "urn:ngsi-ld:Person:10f59922-5919-11e8-a93b-1fea12b786c2"
        ]
    }
}
```
