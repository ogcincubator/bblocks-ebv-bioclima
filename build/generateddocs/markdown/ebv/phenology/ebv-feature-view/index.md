
# EBV Feature View (Schema)

`syke.ebv.phenology.ebv-feature-view` *v1.0*

Discovery layer: GeoJSON Feature with EBV phenology properties linked to CoverageJSON building blocks via semantic context. Enables map visualization in OGC BB viewer.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# EBV Feature View — Multilingual Attribute Definitions

Discovery layer for the OGC Building Blocks map viewer. Represents EBV phenology coverage statistics as GeoJSON Features with **semantically linked, multilingual property definitions**.

## Multilingual labels (EN · ES · 中文 · RO)

Each property has definitions in 4 languages via `x-jsonld-prefLabel` in the schema and `skos:prefLabel` in the EBV ontology:

| Property | EN | ES | 中文 | RO |
|----------|----|----|------|----|
| `entity_type` | Forest Entity Type | Tipo de Entidad Forestal | 森林实体类型 | Tip de Entitate Forestieră |
| `vap_doy` | Start of VAP (Day of Year) | Inicio del Período Activo de Vegetación | 植被活跃期起始 | Începutul Perioadei Active |
| `mean_doy` | Spatial Mean DOY | Media Espacial DOY | 空间平均年日数 | Media Spațială DOY |
| `trend_slope` | Linear Trend (days/year) | Tendencia Lineal (días/año) | 线性趋势（天/年） | Tendința Liniară (zile/an) |
| `sensor` | Source Sensor Platform | Plataforma Sensora | 源传感器平台 | Platforma Senzorului |
| `algorithm` | Derivation Algorithm | Algoritmo de Derivación | 推导算法 | Algoritmul de Derivare |
| `anomaly` | Annual Anomaly Status | Estado de Anomalía Anual | 年度异常状态 | Statusul Anomaliei |

## Real data from NetCDF (DOI: 10.25829/xf8ek6)

36 features = **18 years × 2 entities** with real pixel statistics from the MODIS grid (318×202 pixels):

| Year | Coniferous DOY | Deciduous DOY | Anomaly |
|------|---------------|---------------|---------|
| 2001 | 106 | 137 | normal |
| 2002 | **95** | 142 | **early** |
| 2007 | **97** | 139 | **early** |
| 2012 | **117** | 143 | **late** |
| 2014 | **92** | 139 | **early** |
| 2017 | 114 | **153** | normal / late |

## Properties → Building Block Links

| Property | Ontology URI | Block |
|----------|-------------|-------|
| `entity_type` | `ebv:entity_type` | [EBV Ontology](../ebv-ontology/) |
| `vap_doy` | `ebv:vap_doy` | [CovJSON Parameter](../covjson-parameter/) |
| `mean_doy`, `stddev` | `ebv:mean_doy` | [Phenology Indicators](../phenology-indicators/) |
| `crs` | `covjson:referenceSystem` | [CovJSON Reference System](../covjson-reference-system/) |
| `grid_width`, `grid_height` | `covjson:axisSize` | [CovJSON Axis](../covjson-axis/) |
| `sensor` | `prov:wasGeneratedBy` | [Data Provenance](../data-provenance/) |
| `algorithm` | `prov:used` | [Data Provenance](../data-provenance/) |
| `trend_slope`, `anomaly` | `ebv:trend_slope` | [Phenology Indicators](../phenology-indicators/) |

## [→ Interactive Raster Viewer with Real Pixel Values](../../viewer/)

Full 318×202 MODIS grid with click-to-inspect DOY values for every pixel.

## Examples

### EBV Phenology Finland — Real VAP Data (2001–2018)
examples/finland-vap-features.json
#### json
```json
{
  "type": "FeatureCollection",
  "name": "EBV_Phenology_Finland_VAP_Real",
  "features": [
    {
      "type": "Feature",
      "id": "vap-coniferous-2001",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "mean_doy": 106.4,
        "min_doy": 65,
        "max_doy": 138,
        "stddev": 12.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2002",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2002,
        "vap_doy": 95,
        "mean_doy": 94.7,
        "min_doy": 64,
        "max_doy": 124,
        "stddev": 8.5,
        "valid_percent": 11.09,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2003",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2003,
        "vap_doy": 111,
        "mean_doy": 111.4,
        "min_doy": 65,
        "max_doy": 134,
        "stddev": 13.9,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2004",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2004,
        "vap_doy": 110,
        "mean_doy": 109.7,
        "min_doy": 69,
        "max_doy": 133,
        "stddev": 12.0,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2005",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2005,
        "vap_doy": 111,
        "mean_doy": 111.1,
        "min_doy": 77,
        "max_doy": 153,
        "stddev": 20.1,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2006",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2006,
        "vap_doy": 113,
        "mean_doy": 113.0,
        "min_doy": 92,
        "max_doy": 135,
        "stddev": 5.7,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2007",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2007,
        "vap_doy": 97,
        "mean_doy": 96.9,
        "min_doy": 58,
        "max_doy": 144,
        "stddev": 23.2,
        "valid_percent": 19.43,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2008",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2008,
        "vap_doy": 107,
        "mean_doy": 107.4,
        "min_doy": 49,
        "max_doy": 149,
        "stddev": 17.9,
        "valid_percent": 19.43,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2009",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2009,
        "vap_doy": 110,
        "mean_doy": 110.0,
        "min_doy": 75,
        "max_doy": 130,
        "stddev": 10.4,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2010",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2010,
        "vap_doy": 109,
        "mean_doy": 109.4,
        "min_doy": 89,
        "max_doy": 135,
        "stddev": 14.2,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2011",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2011,
        "vap_doy": 107,
        "mean_doy": 106.6,
        "min_doy": 90,
        "max_doy": 135,
        "stddev": 7.8,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2012",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2012,
        "vap_doy": 117,
        "mean_doy": 117.1,
        "min_doy": 59,
        "max_doy": 144,
        "stddev": 14.1,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "late"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2013",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2013,
        "vap_doy": 110,
        "mean_doy": 110.2,
        "min_doy": 93,
        "max_doy": 138,
        "stddev": 9.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2014",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2014,
        "vap_doy": 92,
        "mean_doy": 91.7,
        "min_doy": 44,
        "max_doy": 142,
        "stddev": 29.0,
        "valid_percent": 19.29,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2015",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2015,
        "vap_doy": 102,
        "mean_doy": 101.8,
        "min_doy": 41,
        "max_doy": 142,
        "stddev": 25.2,
        "valid_percent": 19.41,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2016",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2016,
        "vap_doy": 101,
        "mean_doy": 101.3,
        "min_doy": 50,
        "max_doy": 132,
        "stddev": 16.8,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2017",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2017,
        "vap_doy": 114,
        "mean_doy": 113.8,
        "min_doy": 44,
        "max_doy": 158,
        "stddev": 30.3,
        "valid_percent": 19.4,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2018",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2018,
        "vap_doy": 113,
        "mean_doy": 113.4,
        "min_doy": 80,
        "max_doy": 131,
        "stddev": 11.5,
        "valid_percent": 20.08,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2001",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2001,
        "vap_doy": 137,
        "mean_doy": 137.2,
        "min_doy": 113,
        "max_doy": 198,
        "stddev": 9.6,
        "valid_percent": 20.61,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2002",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2002,
        "vap_doy": 142,
        "mean_doy": 141.9,
        "min_doy": 93,
        "max_doy": 167,
        "stddev": 8.6,
        "valid_percent": 20.7,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2003",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2003,
        "vap_doy": 140,
        "mean_doy": 140.4,
        "min_doy": 116,
        "max_doy": 199,
        "stddev": 10.3,
        "valid_percent": 21.1,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2004",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2004,
        "vap_doy": 138,
        "mean_doy": 138.5,
        "min_doy": 115,
        "max_doy": 199,
        "stddev": 13.0,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2005",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2005,
        "vap_doy": 145,
        "mean_doy": 145.0,
        "min_doy": 113,
        "max_doy": 198,
        "stddev": 14.2,
        "valid_percent": 21.15,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2006",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2006,
        "vap_doy": 138,
        "mean_doy": 137.6,
        "min_doy": 122,
        "max_doy": 192,
        "stddev": 9.4,
        "valid_percent": 20.99,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2007",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2007,
        "vap_doy": 139,
        "mean_doy": 138.8,
        "min_doy": 101,
        "max_doy": 199,
        "stddev": 15.2,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2008",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2008,
        "vap_doy": 144,
        "mean_doy": 144.5,
        "min_doy": 107,
        "max_doy": 199,
        "stddev": 17.3,
        "valid_percent": 21.1,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2009",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2009,
        "vap_doy": 137,
        "mean_doy": 137.4,
        "min_doy": 107,
        "max_doy": 183,
        "stddev": 10.2,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2010",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2010,
        "vap_doy": 139,
        "mean_doy": 138.7,
        "min_doy": 117,
        "max_doy": 196,
        "stddev": 10.7,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2011",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2011,
        "vap_doy": 135,
        "mean_doy": 135.0,
        "min_doy": 117,
        "max_doy": 196,
        "stddev": 11.1,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2012",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2012,
        "vap_doy": 143,
        "mean_doy": 143.3,
        "min_doy": 115,
        "max_doy": 199,
        "stddev": 11.5,
        "valid_percent": 21.13,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2013",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2013,
        "vap_doy": 138,
        "mean_doy": 137.6,
        "min_doy": 123,
        "max_doy": 194,
        "stddev": 9.6,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2014",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2014,
        "vap_doy": 139,
        "mean_doy": 138.6,
        "min_doy": 98,
        "max_doy": 199,
        "stddev": 14.9,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2015",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2015,
        "vap_doy": 139,
        "mean_doy": 139.4,
        "min_doy": 99,
        "max_doy": 196,
        "stddev": 14.8,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2016",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2016,
        "vap_doy": 137,
        "mean_doy": 136.7,
        "min_doy": 103,
        "max_doy": 199,
        "stddev": 8.8,
        "valid_percent": 21.18,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2017",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2017,
        "vap_doy": 153,
        "mean_doy": 153.3,
        "min_doy": 114,
        "max_doy": 198,
        "stddev": 14.1,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "late"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2018",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2018,
        "vap_doy": 138,
        "mean_doy": 138.0,
        "min_doy": 116,
        "max_doy": 196,
        "stddev": 9.6,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    }
  ]
}
```

#### jsonld
```jsonld
{
  "@context": "https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/context.jsonld",
  "type": "FeatureCollection",
  "name": "EBV_Phenology_Finland_VAP_Real",
  "features": [
    {
      "type": "Feature",
      "id": "vap-coniferous-2001",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "mean_doy": 106.4,
        "min_doy": 65,
        "max_doy": 138,
        "stddev": 12.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2002",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2002,
        "vap_doy": 95,
        "mean_doy": 94.7,
        "min_doy": 64,
        "max_doy": 124,
        "stddev": 8.5,
        "valid_percent": 11.09,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2003",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2003,
        "vap_doy": 111,
        "mean_doy": 111.4,
        "min_doy": 65,
        "max_doy": 134,
        "stddev": 13.9,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2004",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2004,
        "vap_doy": 110,
        "mean_doy": 109.7,
        "min_doy": 69,
        "max_doy": 133,
        "stddev": 12.0,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2005",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2005,
        "vap_doy": 111,
        "mean_doy": 111.1,
        "min_doy": 77,
        "max_doy": 153,
        "stddev": 20.1,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2006",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2006,
        "vap_doy": 113,
        "mean_doy": 113.0,
        "min_doy": 92,
        "max_doy": 135,
        "stddev": 5.7,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2007",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2007,
        "vap_doy": 97,
        "mean_doy": 96.9,
        "min_doy": 58,
        "max_doy": 144,
        "stddev": 23.2,
        "valid_percent": 19.43,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2008",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2008,
        "vap_doy": 107,
        "mean_doy": 107.4,
        "min_doy": 49,
        "max_doy": 149,
        "stddev": 17.9,
        "valid_percent": 19.43,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2009",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2009,
        "vap_doy": 110,
        "mean_doy": 110.0,
        "min_doy": 75,
        "max_doy": 130,
        "stddev": 10.4,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2010",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2010,
        "vap_doy": 109,
        "mean_doy": 109.4,
        "min_doy": 89,
        "max_doy": 135,
        "stddev": 14.2,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2011",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2011,
        "vap_doy": 107,
        "mean_doy": 106.6,
        "min_doy": 90,
        "max_doy": 135,
        "stddev": 7.8,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2012",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2012,
        "vap_doy": 117,
        "mean_doy": 117.1,
        "min_doy": 59,
        "max_doy": 144,
        "stddev": 14.1,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "late"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2013",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2013,
        "vap_doy": 110,
        "mean_doy": 110.2,
        "min_doy": 93,
        "max_doy": 138,
        "stddev": 9.5,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2014",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2014,
        "vap_doy": 92,
        "mean_doy": 91.7,
        "min_doy": 44,
        "max_doy": 142,
        "stddev": 29.0,
        "valid_percent": 19.29,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "early"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2015",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2015,
        "vap_doy": 102,
        "mean_doy": 101.8,
        "min_doy": 41,
        "max_doy": 142,
        "stddev": 25.2,
        "valid_percent": 19.41,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2016",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2016,
        "vap_doy": 101,
        "mean_doy": 101.3,
        "min_doy": 50,
        "max_doy": 132,
        "stddev": 16.8,
        "valid_percent": 19.44,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2017",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2017,
        "vap_doy": 114,
        "mean_doy": 113.8,
        "min_doy": 44,
        "max_doy": 158,
        "stddev": 30.3,
        "valid_percent": 19.4,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-coniferous-2018",
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2018,
        "vap_doy": 113,
        "mean_doy": 113.4,
        "min_doy": 80,
        "max_doy": 131,
        "stddev": 11.5,
        "valid_percent": 20.08,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Fractional Snow Cover (FSC)",
        "trend_slope": -0.45,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2001",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2001,
        "vap_doy": 137,
        "mean_doy": 137.2,
        "min_doy": 113,
        "max_doy": 198,
        "stddev": 9.6,
        "valid_percent": 20.61,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2002",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2002,
        "vap_doy": 142,
        "mean_doy": 141.9,
        "min_doy": 93,
        "max_doy": 167,
        "stddev": 8.6,
        "valid_percent": 20.7,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2003",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2003,
        "vap_doy": 140,
        "mean_doy": 140.4,
        "min_doy": 116,
        "max_doy": 199,
        "stddev": 10.3,
        "valid_percent": 21.1,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2004",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2004,
        "vap_doy": 138,
        "mean_doy": 138.5,
        "min_doy": 115,
        "max_doy": 199,
        "stddev": 13.0,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2005",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2005,
        "vap_doy": 145,
        "mean_doy": 145.0,
        "min_doy": 113,
        "max_doy": 198,
        "stddev": 14.2,
        "valid_percent": 21.15,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2006",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2006,
        "vap_doy": 138,
        "mean_doy": 137.6,
        "min_doy": 122,
        "max_doy": 192,
        "stddev": 9.4,
        "valid_percent": 20.99,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2007",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2007,
        "vap_doy": 139,
        "mean_doy": 138.8,
        "min_doy": 101,
        "max_doy": 199,
        "stddev": 15.2,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2008",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2008,
        "vap_doy": 144,
        "mean_doy": 144.5,
        "min_doy": 107,
        "max_doy": 199,
        "stddev": 17.3,
        "valid_percent": 21.1,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2009",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2009,
        "vap_doy": 137,
        "mean_doy": 137.4,
        "min_doy": 107,
        "max_doy": 183,
        "stddev": 10.2,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2010",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2010,
        "vap_doy": 139,
        "mean_doy": 138.7,
        "min_doy": 117,
        "max_doy": 196,
        "stddev": 10.7,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2011",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2011,
        "vap_doy": 135,
        "mean_doy": 135.0,
        "min_doy": 117,
        "max_doy": 196,
        "stddev": 11.1,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2012",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2012,
        "vap_doy": 143,
        "mean_doy": 143.3,
        "min_doy": 115,
        "max_doy": 199,
        "stddev": 11.5,
        "valid_percent": 21.13,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2013",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2013,
        "vap_doy": 138,
        "mean_doy": 137.6,
        "min_doy": 123,
        "max_doy": 194,
        "stddev": 9.6,
        "valid_percent": 21.17,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2014",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2014,
        "vap_doy": 139,
        "mean_doy": 138.6,
        "min_doy": 98,
        "max_doy": 199,
        "stddev": 14.9,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2015",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2015,
        "vap_doy": 139,
        "mean_doy": 139.4,
        "min_doy": 99,
        "max_doy": 196,
        "stddev": 14.8,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2016",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2016,
        "vap_doy": 137,
        "mean_doy": 136.7,
        "min_doy": 103,
        "max_doy": 199,
        "stddev": 8.8,
        "valid_percent": 21.18,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2017",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2017,
        "vap_doy": 153,
        "mean_doy": 153.3,
        "min_doy": 114,
        "max_doy": 198,
        "stddev": 14.1,
        "valid_percent": 21.14,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "late"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    },
    {
      "type": "Feature",
      "id": "vap-deciduous-2018",
      "properties": {
        "entity_type": "DeciduousForest",
        "year": 2018,
        "vap_doy": 138,
        "mean_doy": 138.0,
        "min_doy": 116,
        "max_doy": 196,
        "stddev": 9.6,
        "valid_percent": 21.16,
        "crs": "CRS84",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra Level 1B",
        "algorithm": "Normalized Difference Water Index (NDWI)",
        "trend_slope": -0.35,
        "anomaly": "normal"
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              14.1,
              57.75
            ],
            [
              35.23,
              57.75
            ],
            [
              35.23,
              71.17
            ],
            [
              14.1,
              71.17
            ],
            [
              14.1,
              57.75
            ]
          ]
        ]
      }
    }
  ]
}
```

#### ttl
```ttl


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: EBV phenology properties for map feature view
type: object
properties:
  entity_type:
    type: string
    title: Forest Entity Type
    description: The ecosystem entity type for which the phenology metric is derived.
      Values may identify forest entities such as coniferous or deciduous forest.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#entity_type
    x-jsonld-type: '@id'
    x-jsonld-base: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#
  year:
    type: integer
    title: Observation Year
    description: Calendar year associated with the phenology observation or derived
      annual EBV metric.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#year
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  vap_doy:
    type: integer
    title: Start of VAP (Day of Year)
    description: Integer day of year marking the start of the Vegetation Active Period.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#vap_doy
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  mean_doy:
    type: number
    title: Mean DOY (spatial average)
    description: Spatial mean day-of-year value calculated across valid grid cells
      or pixels for the selected feature.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#mean_doy
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#decimal
  min_doy:
    type: integer
    title: Minimum DOY
    description: Minimum day-of-year value observed across the valid spatial cells
      for the selected feature.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#min_doy
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  max_doy:
    type: integer
    title: Maximum DOY
    description: Maximum day-of-year value observed across the valid spatial cells
      for the selected feature.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#max_doy
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  stddev:
    type: number
    title: Standard Deviation of DOY
    description: Standard deviation of day-of-year values across valid spatial cells
      or pixels.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#stddev
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#decimal
  valid_percent:
    type: number
    title: Valid Pixel Percentage
    description: Percentage of valid spatial cells or pixels used to compute the phenology
      summary metric.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#valid_percent
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#decimal
  crs:
    type: string
    title: Coordinate Reference System
    description: Coordinate reference system used by the spatial representation of
      the feature or coverage-derived summary.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#crs
  grid_width:
    type: integer
    title: Grid Width (columns)
    description: Number of columns in the grid used for the coverage-derived phenology
      data.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#grid_width
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  grid_height:
    type: integer
    title: Grid Height (rows)
    description: Number of rows in the grid used for the coverage-derived phenology
      data.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#grid_height
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#integer
  sensor:
    type: string
    title: Source Sensor Platform
    description: Sensor or observation platform used as the source for the phenology
      derivation.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#sensor
  algorithm:
    type: string
    title: Derivation Algorithm
    description: Algorithm or processing method used to derive the phenology metric.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#algorithm
  trend_slope:
    type: number
    title: Trend Slope (days/year)
    description: Rate of change of the VAP start date over time, expressed in days
      per year.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#trend_slope
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#decimal
  anomaly:
    type: string
    title: Annual Anomaly Status
    description: Annual anomaly category relative to a baseline, for example early,
      normal or late.
    x-jsonld-id: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#anomaly
required:
- entity_type
- year
- vap_doy
x-jsonld-prefixes:
  ebv: https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#
  xsd: http://www.w3.org/2001/XMLSchema#

```

Links to the schema:

* YAML version: [schema.yaml](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/schema.json)
* JSON version: [schema.json](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "entity_type": {
      "@context": {
        "@base": "https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#"
      },
      "@id": "ebv:entity_type",
      "@type": "@id"
    },
    "year": {
      "@id": "ebv:year",
      "@type": "xsd:integer"
    },
    "vap_doy": {
      "@id": "ebv:vap_doy",
      "@type": "xsd:integer"
    },
    "mean_doy": {
      "@id": "ebv:mean_doy",
      "@type": "xsd:decimal"
    },
    "min_doy": {
      "@id": "ebv:min_doy",
      "@type": "xsd:integer"
    },
    "max_doy": {
      "@id": "ebv:max_doy",
      "@type": "xsd:integer"
    },
    "stddev": {
      "@id": "ebv:stddev",
      "@type": "xsd:decimal"
    },
    "valid_percent": {
      "@id": "ebv:valid_percent",
      "@type": "xsd:decimal"
    },
    "crs": "ebv:crs",
    "grid_width": {
      "@id": "ebv:grid_width",
      "@type": "xsd:integer"
    },
    "grid_height": {
      "@id": "ebv:grid_height",
      "@type": "xsd:integer"
    },
    "sensor": "ebv:sensor",
    "algorithm": "ebv:algorithm",
    "trend_slope": {
      "@id": "ebv:trend_slope",
      "@type": "xsd:decimal"
    },
    "anomaly": "ebv:anomaly",
    "ebv": "https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://maytetoscano.github.io/bblock-ebv-bioclima/build/annotated/ebv/phenology/ebv-feature-view/context.jsonld)

## Sources

* [OGC API - Features, Part 1, 7.16.2: Feature Response](https://docs.ogc.org/is/17-069r3/17-069r3.html#_response_7)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/MayteToscano/bblock-ebv-bioclima](https://github.com/MayteToscano/bblock-ebv-bioclima)
* Path: `_sources/ebv-feature-view`

