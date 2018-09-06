# Market Price Observed
This entity contains a harmonised description of a generic commodity, crop or product price that varies over time (a spot price). This entity is primarily associated with the agricultural vertical and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| entity | Relationship | Reference to the entity this price forecast relates to e.g. an AgriProduct entity. | Mandatory |
| priceAverage5Year | Property | The five year average market price observed represented using schema.org PriceSpecification attributes http://schema.org/PriceSpecification | Mandatory |
| priceObserved | Property | The market price observed represented using schema.org PriceSpecification attributes http://schema.org/PriceSpecification | Mandatory |
| address | Property | The market location for this observation encoded as a Schema.org PostalAddress. https://schema.org/PostalAddress | Mandatory |
| marketScale | Property | Unique code assigned to market scale type. The content includes both a name and a value.

 "Wholesale":Wholesale market price 
"Retail":Retail market price for example
{"name":"Wholesale", 'value':"02"}
or
{"name":"Retail", "value":"01"} | Mandatory |
| weatherForecast | Relationship | A reference to a related weather forecast record | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Market Price Observed** entity

[Download context definition.](../examples/Market-Price-Observed-context.jsonld)

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
    "entity": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "priceAverage5Year": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "priceObserved": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "address": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "marketScale": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "weatherForecast": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    }
}
```
## Example of Market Price Observed Entity
The following is an example instance of the **Market Price Observed** entity

[Download example entity definition.](../examples/Market-Price-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Market-Price-Observed-context.jsonld"
    ],
    "id": "urn:ngsi-ld:MarketPriceObserved:398aa5f4-6a81-4dea-9f85-e9869441a257",
    "type": "MarketPriceObserved",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "entity": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:AgriProduct:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84"
    },
    "priceAverage5Year": {
        "type": "Property",
        "value": 15,
        "priceCurrency": "USD",
        "validFrom": {
            "value": "2012-08-23T10:18:16Z",
            "type": "TemporalProperty"
        },
        "validThrough": {
            "value": "2017-08-23T10:18:16Z",
            "type": "TemporalProperty"
        }
    },
    "priceObserved": {
        "type": "Property",
        "value": 5,
        "priceCurrency": "USD",
        "validFrom": {
            "value": "2017-08-22T10:18:16Z",
            "type": "TemporalProperty"
        },
        "validThrough": {
            "value": "2017-08-22T10:18:16Z",
            "type": "TemporalProperty"
        }
    },
    "address": {
        "type": "Property",
        "addressCountry": "UK",
        "addressLocality\"": "London"
    },
    "marketScale": {
        "type": "Property",
        "value": "02",
        "marketType": "Wholesale"
    },
    "weatherForecast": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:WeatherForecast:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c85"
    }
}
```
