
# CovJSON Coverage (Schema)

`syke.ebv.phenology.covjson-coverage` *v1.0*

Complete coverage composing Domain, Parameters, ParameterGroups and Ranges. The core CoverageJSON object for raster data.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# CovJSON Coverage

The core CoverageJSON object. Composes all primitives from the UML:

## [→ Open Interactive Viewer](../../viewer/)

## UML Composition
```
Coverage
├── 1 Domain (→ 1..* Axis + * ReferenceSystem)
├── * ParameterGroup (→ 1..* Parameter)
├── 1..* Parameter (→ observedProperty → Ontology)
└── 1..* Range (→ NdArray or TiledNdArray)
```

## Finland Coniferous VAP Coverage
- **Domain**: Grid 320×200×18 (lon 14.10-35.23, lat 57.75-71.17, years 2001-2018)
- **Parameter**: VAP in Day of Year, 4-language descriptions, linked to ontology
- **Range**: NdArray integer [18, 200, 320] = 1,152,000 pixel values
- **CRS**: OGC CRS84 (WGS-84) + Gregorian calendar

## Band Statistics (from original dataset)
| Year | Min DOY | Max DOY | Mean DOY | StdDev | Valid % |
|------|---------|---------|----------|--------|---------|
| 2001 | 65 | 138 | 106.4 | 12.5 | 19.44% |
| 2002 | 64 | 124 | 94.7 | 8.5 | 11.09% |
| 2003 | 65 | 134 | 111.4 | 13.9 | 19.44% |

## Semantic Link
`observedProperty.id` → `https://w3id.org/ogc/hosted/ebv-phenology/StartOfVAP`

## Examples

### Finland coniferous VAP coverage (2001-2018)
Complete CoverageJSON Coverage for coniferous Start of Vegetation Active Period.
Grid domain 320x200 over 18 years. Parameter with 4-language descriptions linked 
to EBV ontology via observedProperty URI. NdArray range with 1,152,000 cells.

#### json
```json
{
  "type": "Coverage",
  "domain": {
    "type": "Domain",
    "domainType": "Grid",
    "axes": {
      "x": { "start": 14.10, "stop": 35.23, "num": 320 },
      "y": { "start": 57.75, "stop": 71.17, "num": 200 },
      "t": { "values": ["2001","2002","2003","2004","2005","2006","2007","2008","2009","2010","2011","2012","2013","2014","2015","2016","2017","2018"] }
    },
    "referencing": [
      {
        "coordinates": ["x","y"],
        "system": {
          "type": "GeographicCRS",
          "id": "http://www.opengis.net/def/crs/OGC/1.3/CRS84"
        }
      },
      {
        "coordinates": ["t"],
        "system": {
          "type": "TemporalRS",
          "calendar": "Gregorian"
        }
      }
    ]
  },
  "parameters": {
    "VAP": {
      "type": "Parameter",
      "description": {
        "en": "Start of Vegetation Active Period for coniferous forests derived from MODIS Fractional Snow Cover",
        "es": "Inicio del Periodo Activo de Vegetación para bosques de coníferas derivado de cobertura fraccional de nieve MODIS",
        "zh": "基于MODIS积雪覆盖的针叶林植被活跃期起始",
        "ro": "Începutul Perioadei Active a Vegetației pentru păduri de conifere derivat din acoperirea fracțională a zăpezii MODIS"
      },
      "unit": {
        "label": { "en": "Day of Year", "es": "Día del Año", "zh": "年日数", "ro": "Ziua anului" },
        "symbol": { "value": "d", "type": "http://www.opengis.net/def/uom/UCUM/" }
      },
      "observedProperty": {
        "id": "https://w3id.org/ogc/hosted/ebv-phenology/StartOfVAP",
        "label": {
          "en": "Start of Vegetation Active Period",
          "es": "Inicio del Periodo Activo de Vegetación",
          "zh": "植被活跃期起始",
          "ro": "Începutul Perioadei Active a Vegetației"
        }
      }
    }
  },
  "ranges": {
    "VAP": {
      "type": "NdArray",
      "dataType": "integer",
      "axisNames": ["t","y","x"],
      "shape": [18, 200, 320]
    }
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/covjson-coverage/context.jsonld",
  "type": "Coverage",
  "domain": {
    "type": "Domain",
    "domainType": "Grid",
    "axes": {
      "x": {
        "start": 14.1,
        "stop": 35.23,
        "num": 320
      },
      "y": {
        "start": 57.75,
        "stop": 71.17,
        "num": 200
      },
      "t": {
        "values": [
          "2001",
          "2002",
          "2003",
          "2004",
          "2005",
          "2006",
          "2007",
          "2008",
          "2009",
          "2010",
          "2011",
          "2012",
          "2013",
          "2014",
          "2015",
          "2016",
          "2017",
          "2018"
        ]
      }
    },
    "referencing": [
      {
        "coordinates": [
          "x",
          "y"
        ],
        "system": {
          "type": "GeographicCRS",
          "id": "http://www.opengis.net/def/crs/OGC/1.3/CRS84"
        }
      },
      {
        "coordinates": [
          "t"
        ],
        "system": {
          "type": "TemporalRS",
          "calendar": "Gregorian"
        }
      }
    ]
  },
  "parameters": {
    "VAP": {
      "type": "Parameter",
      "description": {
        "en": "Start of Vegetation Active Period for coniferous forests derived from MODIS Fractional Snow Cover",
        "es": "Inicio del Periodo Activo de Vegetaci\u00f3n para bosques de con\u00edferas derivado de cobertura fraccional de nieve MODIS",
        "zh": "\u57fa\u4e8eMODIS\u79ef\u96ea\u8986\u76d6\u7684\u9488\u53f6\u6797\u690d\u88ab\u6d3b\u8dc3\u671f\u8d77\u59cb",
        "ro": "\u00cenceputul Perioadei Active a Vegeta\u021biei pentru p\u0103duri de conifere derivat din acoperirea frac\u021bional\u0103 a z\u0103pezii MODIS"
      },
      "unit": {
        "label": {
          "en": "Day of Year",
          "es": "D\u00eda del A\u00f1o",
          "zh": "\u5e74\u65e5\u6570",
          "ro": "Ziua anului"
        },
        "symbol": {
          "value": "d",
          "type": "http://www.opengis.net/def/uom/UCUM/"
        }
      },
      "observedProperty": {
        "id": "https://w3id.org/ogc/hosted/ebv-phenology/StartOfVAP",
        "label": {
          "en": "Start of Vegetation Active Period",
          "es": "Inicio del Periodo Activo de Vegetaci\u00f3n",
          "zh": "\u690d\u88ab\u6d3b\u8dc3\u671f\u8d77\u59cb",
          "ro": "\u00cenceputul Perioadei Active a Vegeta\u021biei"
        }
      }
    }
  },
  "ranges": {
    "VAP": {
      "type": "NdArray",
      "dataType": "integer",
      "axisNames": [
        "t",
        "y",
        "x"
      ],
      "shape": [
        18,
        200,
        320
      ]
    }
  }
}
```

#### ttl
```ttl
@prefix covjson: <https://covjson.org/def/core#> .
@prefix covjsondt: <https://covjson.org/def/domainTypes#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix ebv: <https://w3id.org/ogc/hosted/ebv-phenology/> .
@prefix inspiregloss: <http://inspire.ec.europa.eu/glossary/> .
@prefix qudt: <http://qudt.org/schema/qudt#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix sosa1: <http://www.w3.org/ns/sosa#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<http://www.opengis.net/def/crs/OGC/1.3/CRS84> a [ ] .

ebv:StartOfVAP skos:prefLabel "Start of Vegetation Active Period"@en,
        "Inicio del Periodo Activo de Vegetación"@es,
        "Începutul Perioadei Active a Vegetației"@ro,
        "植被活跃期起始"@zh .

[] a covjson:Coverage ;
    covjson:domain [ a covjson:Domain ;
            covjson:axis [ covjson:num 320 ;
                    covjson:start 1.41e+01 ;
                    covjson:stop 3.523e+01 ],
                [ covjson:num 200 ;
                    covjson:start 5.775e+01 ;
                    covjson:stop 7.117e+01 ],
                [ ] ;
            covjson:domainType covjsondt:Grid ;
            covjson:referencing [ covjson:referenceSystem [ a inspiregloss:TemporalReferenceSystem ;
                            covjson:calendar <http://www.opengis.net/def/uom/ISO-8601/0/Gregorian> ] ],
                [ covjson:referenceSystem <http://www.opengis.net/def/crs/OGC/1.3/CRS84> ] ] ;
    covjson:parameter [ a covjson:Parameter ;
            dct:description "Start of Vegetation Active Period for coniferous forests derived from MODIS Fractional Snow Cover"@en,
                "Inicio del Periodo Activo de Vegetación para bosques de coníferas derivado de cobertura fraccional de nieve MODIS"@es,
                "Începutul Perioadei Active a Vegetației pentru păduri de conifere derivat din acoperirea fracțională a zăpezii MODIS"@ro,
                "基于MODIS积雪覆盖的针叶林植被活跃期起始"@zh ;
            qudt:unit [ qudt:symbol "d"^^<http://www.opengis.net/def/uom/UCUM/> ;
                    skos:prefLabel "Day of Year"@en,
                        "Día del Año"@es,
                        "Ziua anului"@ro,
                        "年日数"@zh ] ;
            sosa1:observedProperty ebv:StartOfVAP ] ;
    covjson:range [ a covjson:NdArray ;
            covjson:axisNames ( "t" "y" "x" ) ;
            covjson:dataType xsd:integer ;
            covjson:shape ( 18 200 320 ) ] .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: CoverageJSON Coverage - composite of Domain + Parameters + Ranges
type: object
required:
- type
- domain
- parameters
- ranges
properties:
  type:
    type: string
    const: Coverage
    x-jsonld-id: '@type'
  domain:
    type: object
    required:
    - type
    - axes
    x-jsonld-id: https://covjson.org/def/core#domain
  parameters:
    type: object
    x-jsonld-id: https://covjson.org/def/core#parameter
    x-jsonld-type: '@id'
    x-jsonld-container: '@index'
  parameterGroups:
    type: array
    items:
      type: object
  ranges:
    type: object
    x-jsonld-id: https://covjson.org/def/core#range
    x-jsonld-type: '@id'
    x-jsonld-container: '@index'
x-jsonld-extra-terms:
  meteogate: https://api.meteogate.eu/profiles/metocean/covjson
  id: '@id'
  value: '@value'
  label:
    x-jsonld-id: http://www.w3.org/2004/02/skos/core#prefLabel
    x-jsonld-container: '@language'
  title:
    x-jsonld-id: http://purl.org/dc/terms/title
    x-jsonld-container: '@language'
  description:
    x-jsonld-id: http://purl.org/dc/terms/description
    x-jsonld-container: '@language'
  unit: http://qudt.org/schema/qudt#unit
  symbol: http://qudt.org/schema/qudt#symbol
  Domain: https://covjson.org/def/core#Domain
  domainType:
    x-jsonld-id: https://covjson.org/def/core#domainType
    x-jsonld-type: '@vocab'
  axes:
    x-jsonld-id: https://covjson.org/def/core#axis
    x-jsonld-container: '@index'
  dataType:
    x-jsonld-id: https://covjson.org/def/core#dataType
    x-jsonld-type: '@vocab'
  primitive: https://covjson.org/def/core#primitive
  tuple: https://covjson.org/def/core#tuple
  polygon: https://covjson.org/def/core#polygon
  num: https://covjson.org/def/core#num
  start: https://covjson.org/def/core#start
  stop: https://covjson.org/def/core#stop
  referencing:
    x-jsonld-id: https://covjson.org/def/core#referencing
    x-jsonld-container: '@set'
  components:
    x-jsonld-id: https://covjson.org/def/core#components
    x-jsonld-container: '@list'
  system: https://covjson.org/def/core#referenceSystem
  RS: https://covjson.org/def/core#ReferenceSystem
  CRS: https://covjson.org/def/core#CoordinateReferenceSystem
  cs: http://data.ign.fr/def/ignf#coordinateSystem
  CS: http://data.ign.fr/def/ignf#CoordinateSystem
  TemporalRS: http://inspire.ec.europa.eu/glossary/TemporalReferenceSystem
  TemporalCRS: https://covjson.org/def/core#TemporalCRS
  calendar:
    x-jsonld-id: https://covjson.org/def/core#calendar
    x-jsonld-type: '@vocab'
  Gregorian: http://www.opengis.net/def/uom/ISO-8601/0/Gregorian
  timeScale: https://covjson.org/def/core#timeScale
  SpatialRS: http://inspire.ec.europa.eu/glossary/SpatialReferenceSystem
  SpatialCRS: http://data.ign.fr/def/ignf#CRS
  GeodeticCRS: http://data.ign.fr/def/ignf#GeodeticCRS
  ProjectedCRS: http://data.ign.fr/def/ignf#ProjectedCRS
  VerticalCRS: http://data.ign.fr/def/ignf#VerticalCRS
  datum: http://data.ign.fr/def/ignf#datum
  csAxes:
    x-jsonld-id: https://covjson.org/def/core#coordinateSystemAxes
    x-jsonld-container: '@list'
  direction: http://data.ign.fr/def/ignf#axisDirection
  IdentifierRS: https://covjson.org/def/core#IdentifierReferenceSystem
  targetConcept: https://covjson.org/def/core#targetConcept
  identifiers:
    x-jsonld-id: https://covjson.org/def/core#identifier
    x-jsonld-type: '@id'
    x-jsonld-container: '@index'
  Parameter: https://covjson.org/def/core#Parameter
  observedProperty: http://www.w3.org/ns/sosa#observedProperty
  usedProcedure: http://www.w3.org/ns/sosa#usedProcedure
  madeBySensor: http://www.w3.org/ns/sosa#madeBySensor
  hasFeatureOfInterest: http://www.w3.org/ns/sosa#hasFeatureOfInterest
  categoryEncoding: https://covjson.org/def/core#categoryEncoding
  ParameterGroup: https://covjson.org/def/core#ParameterGroup
  members:
    x-jsonld-id: https://covjson.org/def/core#member
    x-jsonld-type: '@vocab'
    x-jsonld-container: '@set'
  NdArray: https://covjson.org/def/core#NdArray
  TiledNdArray: https://covjson.org/def/core#TiledNdArray
  shape:
    x-jsonld-id: https://covjson.org/def/core#shape
    x-jsonld-container: '@list'
  tileShape:
    x-jsonld-id: https://covjson.org/def/core#tileShape
    x-jsonld-container: '@list'
  axisNames:
    x-jsonld-id: https://covjson.org/def/core#axisNames
    x-jsonld-container: '@list'
  urlTemplate: https://covjson.org/def/core#urlTemplate
  tileSets:
    x-jsonld-id: https://covjson.org/def/core#tileSet
    x-jsonld-container: '@set'
  float: http://www.w3.org/2001/XMLSchema#double
  integer: http://www.w3.org/2001/XMLSchema#integer
  string: http://www.w3.org/2001/XMLSchema#string
  Coverage: https://covjson.org/def/core#Coverage
  coverages:
    x-jsonld-id: http://www.w3.org/ns/hydra/core#member
    x-jsonld-container: '@set'
  CoverageCollection: https://covjson.org/def/core#CoverageCollection
  Grid: https://covjson.org/def/domainTypes#Grid
  VerticalProfile: https://covjson.org/def/domainTypes#VerticalProfile
  MultiPointSeries: https://covjson.org/def/domainTypes#MultiPointSeries
  MultiPoint: https://covjson.org/def/domainTypes#MultiPoint
  PointSeries: https://covjson.org/def/domainTypes#PointSeries
  Point: https://covjson.org/def/domainTypes#Point
  Trajectory: https://covjson.org/def/domainTypes#Trajectory
  Section: https://covjson.org/def/domainTypes#Section
  MultiPolygonSeries: https://covjson.org/def/domainTypes#MultiPolygonSeries
  MultiPolygon: https://covjson.org/def/domainTypes#MultiPolygon
  Polygon: https://covjson.org/def/domainTypes#Polygon
x-jsonld-vocab: '_:'
x-jsonld-prefixes:
  skos: http://www.w3.org/2004/02/skos/core#
  dct: http://purl.org/dc/terms/
  qudt: http://qudt.org/schema/qudt#
  covjson: https://covjson.org/def/core#
  ignf: http://data.ign.fr/def/ignf#
  inspiregloss: http://inspire.ec.europa.eu/glossary/
  sosa: http://www.w3.org/ns/sosa#
  xsd: http://www.w3.org/2001/XMLSchema#
  hydra: http://www.w3.org/ns/hydra/core#
  covjsondt: https://covjson.org/def/domainTypes#
  ssn: http://www.w3.org/2005/Incubator/ssn/ssnx/ssn#
  rel: http://www.iana.org/assignments/relation/
  ebv: https://w3id.org/ogc/hosted/ebv-phenology/
  prov: http://www.w3.org/ns/prov#

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/covjson-coverage/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/covjson-coverage/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "_:",
    "meteogate": "https://api.meteogate.eu/profiles/metocean/covjson",
    "id": "@id",
    "value": "@value",
    "label": {
      "@id": "skos:prefLabel",
      "@container": "@language"
    },
    "title": {
      "@id": "dct:title",
      "@container": "@language"
    },
    "description": {
      "@id": "dct:description",
      "@container": "@language"
    },
    "unit": "qudt:unit",
    "symbol": "qudt:symbol",
    "Domain": "covjson:Domain",
    "domainType": {
      "@id": "covjson:domainType",
      "@type": "@vocab"
    },
    "axes": {
      "@id": "covjson:axis",
      "@container": "@index"
    },
    "dataType": {
      "@id": "covjson:dataType",
      "@type": "@vocab"
    },
    "primitive": "covjson:primitive",
    "tuple": "covjson:tuple",
    "polygon": "covjson:polygon",
    "num": "covjson:num",
    "start": "covjson:start",
    "stop": "covjson:stop",
    "referencing": {
      "@id": "covjson:referencing",
      "@container": "@set"
    },
    "components": {
      "@id": "covjson:components",
      "@container": "@list"
    },
    "system": "covjson:referenceSystem",
    "RS": "covjson:ReferenceSystem",
    "CRS": "covjson:CoordinateReferenceSystem",
    "cs": "ignf:coordinateSystem",
    "CS": "ignf:CoordinateSystem",
    "TemporalRS": "inspiregloss:TemporalReferenceSystem",
    "TemporalCRS": "covjson:TemporalCRS",
    "calendar": {
      "@id": "covjson:calendar",
      "@type": "@vocab"
    },
    "Gregorian": "http://www.opengis.net/def/uom/ISO-8601/0/Gregorian",
    "timeScale": "covjson:timeScale",
    "SpatialRS": "inspiregloss:SpatialReferenceSystem",
    "SpatialCRS": "ignf:CRS",
    "GeodeticCRS": "ignf:GeodeticCRS",
    "ProjectedCRS": "ignf:ProjectedCRS",
    "VerticalCRS": "ignf:VerticalCRS",
    "datum": "ignf:datum",
    "csAxes": {
      "@id": "covjson:coordinateSystemAxes",
      "@container": "@list"
    },
    "direction": "ignf:axisDirection",
    "IdentifierRS": "covjson:IdentifierReferenceSystem",
    "targetConcept": "covjson:targetConcept",
    "identifiers": {
      "@id": "covjson:identifier",
      "@type": "@id",
      "@container": "@index"
    },
    "Parameter": "covjson:Parameter",
    "observedProperty": "sosa:observedProperty",
    "usedProcedure": "sosa:usedProcedure",
    "madeBySensor": "sosa:madeBySensor",
    "hasFeatureOfInterest": "sosa:hasFeatureOfInterest",
    "categoryEncoding": "covjson:categoryEncoding",
    "ParameterGroup": "covjson:ParameterGroup",
    "members": {
      "@id": "covjson:member",
      "@type": "@vocab",
      "@container": "@set"
    },
    "NdArray": "covjson:NdArray",
    "TiledNdArray": "covjson:TiledNdArray",
    "shape": {
      "@id": "covjson:shape",
      "@container": "@list"
    },
    "tileShape": {
      "@id": "covjson:tileShape",
      "@container": "@list"
    },
    "axisNames": {
      "@id": "covjson:axisNames",
      "@container": "@list"
    },
    "urlTemplate": "covjson:urlTemplate",
    "tileSets": {
      "@id": "covjson:tileSet",
      "@container": "@set"
    },
    "float": "xsd:double",
    "integer": "xsd:integer",
    "string": "xsd:string",
    "Coverage": "covjson:Coverage",
    "coverages": {
      "@id": "hydra:member",
      "@container": "@set"
    },
    "CoverageCollection": "covjson:CoverageCollection",
    "Grid": "covjsondt:Grid",
    "VerticalProfile": "covjsondt:VerticalProfile",
    "MultiPointSeries": "covjsondt:MultiPointSeries",
    "MultiPoint": "covjsondt:MultiPoint",
    "PointSeries": "covjsondt:PointSeries",
    "Point": "covjsondt:Point",
    "Trajectory": "covjsondt:Trajectory",
    "Section": "covjsondt:Section",
    "MultiPolygonSeries": "covjsondt:MultiPolygonSeries",
    "MultiPolygon": "covjsondt:MultiPolygon",
    "Polygon": "covjsondt:Polygon",
    "type": "@type",
    "domain": "covjson:domain",
    "parameters": {
      "@id": "covjson:parameter",
      "@type": "@id",
      "@container": "@index"
    },
    "ranges": {
      "@id": "covjson:range",
      "@type": "@id",
      "@container": "@index"
    },
    "skos": "http://www.w3.org/2004/02/skos/core#",
    "dct": "http://purl.org/dc/terms/",
    "qudt": "http://qudt.org/schema/qudt#",
    "covjson": "https://covjson.org/def/core#",
    "ignf": "http://data.ign.fr/def/ignf#",
    "inspiregloss": "http://inspire.ec.europa.eu/glossary/",
    "sosa": "http://www.w3.org/ns/sosa#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "hydra": "http://www.w3.org/ns/hydra/core#",
    "covjsondt": "https://covjson.org/def/domainTypes#",
    "ssn": "http://www.w3.org/2005/Incubator/ssn/ssnx/ssn#",
    "rel": "http://www.iana.org/assignments/relation/",
    "ebv": "https://w3id.org/ogc/hosted/ebv-phenology/",
    "prov": "http://www.w3.org/ns/prov#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/covjson-coverage/context.jsonld)

## Sources

* [OGC CoverageJSON 21-069r2 §6](https://docs.ogc.org/cs/21-069r2/21-069r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/covjson-coverage`

