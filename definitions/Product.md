# Product
This entity contains a harmonised description of a generic product. This entity is primarily associated with products and supply chains. It is based on the GS1 standard available at http://gs1.org/voc/Product

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| productType | Relationship | Refers to the relevant ProductType record that this entity is associated with. | Recommended |
| supplierName | Property | The name of the supplier of this product. | Recommended |
| gtin | Property | GS1 product code.<br/><br/>A Global Trade Item Number (GTIN) is the 14 digit GS1 Identification Key used to identify products.<br/><br/>See http://www.gs1.org/gtin for more details. | Optional |
| gpcCategoryCode | Property | Product category code<br/><br/>8-digit code (GPC "Brick Value") specifying a product category according to the GS1 Global Product Classification (GPC) standard.<br/><br/>For more information see http://www.gs1.org/gpc | Recommended |
| productName | Property | The name of this product. | Recommended |
| description | Property | A description of this product. | Recommended |
| brand | Property | The brand name for this product. | Recommended |
| inPackageWidth | Property | The width of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| inPackageDepth | Property | The depth of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| inPackageHeight | Property | The height of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| netWeight | Property | Used to identify the net weight of the product. Net Weight excludes all packaging material, including the packaging material of all lower-level GTINs. Example:11.5 kg | Optional |
| grossWeight | Property | Used to identify the gross weight of the product. The gross weight includes all packaging materials of the product. At pallet level the gross weight includes the weight of the pallet itself. For example, 200 GRM, value - total pounds, total grams, etc. | Optional |
| countryOfOrigin | Property | Country where the product was manufactured, harvested, mined etc. Code indicating the country of origin of the product. | Optional |
| images | Property | List of URIs (URNs/URLs) of images of the product.

Each URI links to a resource containing a visual representation of the product either as catalogue images or as actual images of the specific product. | Optional |
| producerURI | Property | URI (URL/URN) to the producer of the product | Optional |
| manufacturer | Property | Details of the product manufacturer according to http://schema.org/Organization | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Product** entity

[Download context definition.](../examples/Product-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "productType": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/producttype",
        "supplierName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/suppliername",
        "gtin": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/gtin",
        "gpcCategoryCode": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/gpccategorycode",
        "productName": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/productname",
        "brand": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/brand",
        "inPackageWidth": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/inpackagewidth",
        "inPackageDepth": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/inpackagedepth",
        "inPackageHeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/inpackageheight",
        "netWeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/netweight",
        "grossWeight": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/grossweight",
        "countryOfOrigin": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/countryoforigin",
        "images": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/images",
        "producerURI": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/produceruri",
        "manufacturer": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/manufacturer"
    }
}
```
## Example of Product Entity
The following is an example instance of the **Product** entity

[Download example entity definition.](../examples/Product.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Product-context.jsonld"
    ],
    "id": "urn:ngsi-ld:Product:6223903a-d8c5-4e7e-af24-cc90967feb61",
    "type": "Product",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "productType": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:ProductType:27242396-032d-11e7-83f3-83fdf070a882"
    },
    "supplierName": {
        "type": "Property",
        "value": "ACME Direct, Inc."
    },
    "gtin": {
        "type": "Property",
        "value": "01234567890"
    },
    "gpcCategoryCode": {
        "type": "Property",
        "value": "10000271"
    },
    "productName": {
        "type": "Property",
        "value": "Paprika, dried, powdered"
    },
    "description": {
        "type": "Property",
        "value": "Natural paprika grown in Suffolk"
    },
    "brand": {
        "type": "Property",
        "value": "All natural Suffolk spice"
    },
    "inPackageWidth": {
        "type": "Property",
        "value": {
            "value": 25,
            "unitText": "inch"
        },
        "unitCode": "INH"
    },
    "inPackageDepth": {
        "type": "Property",
        "value": {
            "value": 5,
            "unitText": "inch"
        },
        "unitCode": "INH"
    },
    "inPackageHeight": {
        "type": "Property",
        "value": {
            "value": 15,
            "unitText": "inch"
        },
        "unitCode": "INH"
    },
    "netWeight": {
        "type": "Property",
        "value": {
            "value": 2500,
            "unitText": "grammes"
        },
        "unitCode": "GRM"
    },
    "grossWeight": {
        "type": "Property",
        "value": {
            "value": 3000,
            "unitText": "grammes"
        },
        "unitCode": "GRM"
    },
    "countryOfOrigin": {
        "type": "Property",
        "value": "UK"
    },
    "images": {
        "type": "Property",
        "value": [
            "http://example.com/productImg1.jpg",
            "http://example.com/productImg2.jpg"
        ]
    },
    "producerURI": {
        "type": "Property",
        "value": {
            "@value": "http://www.example.com",
            "@type": "https://schema.org/url"
        }
    },
    "manufacturer": {
        "type": "Property",
        "name": "ACME Suffolk Spice Company"
    }
}
```
