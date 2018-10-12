# Point of Interest
This entity contains a harmonised geographic description of a Point of Interest. This entity is used in applications that use spatial data and is applicable to Automotive, Environment, Industry and Smart City vertical segments and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| location | GeoProperty | The geo:json encoded location (point, polygon, multi-polygon etc) of this point of interest. | Mandatory |
| category | Property | One or more category codes relating to this point of interest as per the taxonomy definition at https://github.com/Factual/places/blob/master/categories/factual_taxonomy.json | Mandatory |
| description | Relationship | An optional description of the entity. | Recommended |
| place | Property | The definition of the place for this Point Of Interest. See https://schema.org/Place | Recommended |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Point of Interest** entity

[Download context definition.](../examples/Point-of-Interest-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "location": "http://uri.etsi.org/ngsi-ld/location",
        "category": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/category",
        "description": "https://schema.org/description",
        "place": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/place"
    }
}
```
## Example of Point of Interest Entity
The following is an example instance of the **Point of Interest** entity

[Download example entity definition.](../examples/Point-of-Interest.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Point-of-Interest-context.jsonld"
    ],
    "id": "urn:ngsi-ld:PointOfInterest:44e47705-90c3-4dbc-a0ae-7810306de5e9",
    "type": "PointOfInterest",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -104.99404,
                39.75621
            ]
        }
    },
    "category": {
        "type": "Property",
        "value": [
            "36"
        ]
    },
    "description": {
        "type": "Relationship",
        "value": "Learn all about mobile at the GSMA Academy"
    },
    "place": {
        "type": "Property",
        "value": {
            "name": "GSMA Academy",
            "address": {
                "@type": "https://schema.org/PostalAddress",
                "addressLocality": "London",
                "postalCode": "EC4N 8AF",
                "streetAddress": "25 Walbrook"
            },
            "telephone": "0212345678"
        }
    }
}
```
