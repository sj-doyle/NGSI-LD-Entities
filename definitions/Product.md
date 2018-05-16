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
| gtin | Property | GS1 product code.

A Global Trade Item Number (GTIN) is the 14 digit GS1 Identification Key used to identify products. The key comprises a GS1 Company Prefix followed by an Item Reference Number and a Check Digit.

See http://www.gs1.org/gtin for more details.

There are four GTIN formats. A uniform 14-digit format is required for this harmonised model, add leading zeros as required: 
000000nnnnnnnn (GTIN-8) 
00nnnnnnnnnnnn (GTIN-12) 
0nnnnnnnnnnnnn (GTIN-13) | Optional |
| productName | Property | The name of this product. | Recommended |
| description | Property | A description of this product. | Recommended |
| brand | Property | The brand name for this product. | Recommended |
| inPackageWidth | Property | The width of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| inPackageDepth | Property | The depth of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| inPackageHeight | Property | The height of the product in the package, as measured according to the GS1 Package Measurement Rules. See http://www.gs1.org/package-measurement-rules-implementation-guide for more details. | Optional |
| netWeight | Property | Used to identify the net weight of the product. Net Weight excludes all packaging material, including the packaging material of all lower-level GTINs. Example:11.5 kg | Optional |
| grossWeight | Property | Used to identify the gross weight of the product. The gross weight includes all packaging materials of the product. At pallet level the gross weight includes the weight of the pallet itself. For example, 200 GRM, value - total pounds, total grams, etc. | Optional |
| countryOfOrigin | Property | Country where the product was manufactured, harvested, mined etc. Code indicating the country of origin of the product. | Optional |
| gpcCategoryCode | Property | Product category code

8-digit code (GPC "Brick Value") specifying a product category according to the GS1 Global Product Classification (GPC) standard. For more information see http://www.gs1.org/gpc | Optional |
| images | uri | List of URIs (URNs/URLs) of images of the product.

Each URI links to a resource containing a visual representation of the product either as catalogue images or as actual images of the specific product. | Optional |
| producerURI | uri | URI (URL/URN) to the producer of the product | Optional |
| manufacturer | Property | Details of the product manufacturer according to http://schema.org/Organization | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Product** entity

[Download context definition.](../examples/Product-context.jsonld)

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
    "Relationship": "http://uri.etsi.org/ngsi-ld/Relationship",
    "uri": "http://uri.etsi.org/ngsi-ld/uri"
}
```
## Example of Product Entity
The following is an example instance of the **Product** entity

[Download example entity definition.](../examples/Product.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Product-context.jsonld"
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
        "unitText": "inch",
        "unitCode": "INH",
        "value": 25
    },
    "inPackageDepth": {
        "type": "Property",
        "unitText": "inch",
        "unitCode": "INH",
        "value": 5
    },
    "inPackageHeight": {
        "type": "Property",
        "unitText": "inch",
        "unitCode": "INH",
        "value": 15
    },
    "netWeight": {
        "type": "Property",
        "unitText": "grammes",
        "unitCode": "GRM",
        "value": 2500
    },
    "grossWeight": {
        "type": "Property",
        "unitText": "grammes",
        "unitCode": "GRM",
        "value": 3000
    },
    "countryOfOrigin": {
        "type": "Property",
        "value": "UK"
    },
    "gpcCategoryCode": {
        "type": "Property",
        "value": "10000271"
    },
    "images": {
        "type": "uri",
        "value": [
            "http://example.com/productImg1.jpg",
            "http://example.com/productImg2.jpg"
        ]
    },
    "producerURI": {
        "type": "uri",
        "value": "http://www.example.com"
    },
    "manufacturer": {
        "type": "Property",
        "name": "ACME Suffolk Spice Company"
    }
}
```
