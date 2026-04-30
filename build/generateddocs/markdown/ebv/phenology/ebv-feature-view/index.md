
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


### EBV Phenology Finland — Raster cell sample (Coniferous, 2001)
examples/finland-vap-grid-sample-2001.json
#### json
```json
{
  "type": "FeatureCollection",
  "entity_type": "ConiferousForest",
  "year": 2001,
  "vap_doy": 106.26,
  "mean_doy": 106.26,
  "min_doy": 71,
  "max_doy": 125,
  "valid_percent": 0.1915,
  "crs": "EPSG:4326",
  "grid_width": 318,
  "grid_height": 202,
  "sensor": "MODIS Terra",
  "algorithm": "VAP derived from Fractional Snow Cover time series",
  "anomaly": "not_applicable_sample",
  "name": "EBV Phenology Finland — sampled raster cells",
  "description": "GeoJSON sample generated from the original NetCDF raster. Each feature is one sampled raster cell for coniferous forest in 2001. This is intended for visualisation in the Building Blocks examples page, not as a replacement for the full raster dataset.",
  "features": [
    {
      "type": "Feature",
      "id": "coniferous-2001-r30-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              69.11246
            ],
            [
              27.453207,
              69.11246
            ],
            [
              27.453207,
              69.178888
            ],
            [
              27.386779,
              69.178888
            ],
            [
              27.386779,
              69.11246
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 121,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 30,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r30-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              69.11246
            ],
            [
              28.781768,
              69.11246
            ],
            [
              28.781768,
              69.178888
            ],
            [
              28.71534,
              69.178888
            ],
            [
              28.71534,
              69.11246
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 30,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              68.44818
            ],
            [
              26.124646,
              68.44818
            ],
            [
              26.124646,
              68.514608
            ],
            [
              26.058218,
              68.514608
            ],
            [
              26.058218,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              68.44818
            ],
            [
              26.788927,
              68.44818
            ],
            [
              26.788927,
              68.514608
            ],
            [
              26.722498,
              68.514608
            ],
            [
              26.722498,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              68.44818
            ],
            [
              27.453207,
              68.44818
            ],
            [
              27.453207,
              68.514608
            ],
            [
              27.386779,
              68.514608
            ],
            [
              27.386779,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              68.44818
            ],
            [
              28.117488,
              68.44818
            ],
            [
              28.117488,
              68.514608
            ],
            [
              28.05106,
              68.514608
            ],
            [
              28.05106,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              67.783899
            ],
            [
              24.131804,
              67.783899
            ],
            [
              24.131804,
              67.850327
            ],
            [
              24.065376,
              67.850327
            ],
            [
              24.065376,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              67.783899
            ],
            [
              24.796085,
              67.783899
            ],
            [
              24.796085,
              67.850327
            ],
            [
              24.729657,
              67.850327
            ],
            [
              24.729657,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 119,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              67.783899
            ],
            [
              25.460365,
              67.783899
            ],
            [
              25.460365,
              67.850327
            ],
            [
              25.393937,
              67.850327
            ],
            [
              25.393937,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              67.783899
            ],
            [
              26.124646,
              67.783899
            ],
            [
              26.124646,
              67.850327
            ],
            [
              26.058218,
              67.850327
            ],
            [
              26.058218,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 125,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              67.783899
            ],
            [
              26.788927,
              67.783899
            ],
            [
              26.788927,
              67.850327
            ],
            [
              26.722498,
              67.850327
            ],
            [
              26.722498,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              67.783899
            ],
            [
              27.453207,
              67.783899
            ],
            [
              27.453207,
              67.850327
            ],
            [
              27.386779,
              67.850327
            ],
            [
              27.386779,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 123,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              67.783899
            ],
            [
              28.117488,
              67.783899
            ],
            [
              28.117488,
              67.850327
            ],
            [
              28.05106,
              67.850327
            ],
            [
              28.05106,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              67.783899
            ],
            [
              28.781768,
              67.783899
            ],
            [
              28.781768,
              67.850327
            ],
            [
              28.71534,
              67.850327
            ],
            [
              28.71534,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              67.783899
            ],
            [
              29.446049,
              67.783899
            ],
            [
              29.446049,
              67.850327
            ],
            [
              29.379621,
              67.850327
            ],
            [
              29.379621,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 119,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              67.119618
            ],
            [
              24.131804,
              67.119618
            ],
            [
              24.131804,
              67.186046
            ],
            [
              24.065376,
              67.186046
            ],
            [
              24.065376,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              67.119618
            ],
            [
              24.796085,
              67.119618
            ],
            [
              24.796085,
              67.186046
            ],
            [
              24.729657,
              67.186046
            ],
            [
              24.729657,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              67.119618
            ],
            [
              25.460365,
              67.119618
            ],
            [
              25.460365,
              67.186046
            ],
            [
              25.393937,
              67.186046
            ],
            [
              25.393937,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              67.119618
            ],
            [
              26.124646,
              67.119618
            ],
            [
              26.124646,
              67.186046
            ],
            [
              26.058218,
              67.186046
            ],
            [
              26.058218,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 121,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              67.119618
            ],
            [
              26.788927,
              67.119618
            ],
            [
              26.788927,
              67.186046
            ],
            [
              26.722498,
              67.186046
            ],
            [
              26.722498,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              67.119618
            ],
            [
              28.117488,
              67.119618
            ],
            [
              28.117488,
              67.186046
            ],
            [
              28.05106,
              67.186046
            ],
            [
              28.05106,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              67.119618
            ],
            [
              28.781768,
              67.119618
            ],
            [
              28.781768,
              67.186046
            ],
            [
              28.71534,
              67.186046
            ],
            [
              28.71534,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              66.455338
            ],
            [
              24.131804,
              66.455338
            ],
            [
              24.131804,
              66.521766
            ],
            [
              24.065376,
              66.521766
            ],
            [
              24.065376,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              66.455338
            ],
            [
              24.796085,
              66.455338
            ],
            [
              24.796085,
              66.521766
            ],
            [
              24.729657,
              66.521766
            ],
            [
              24.729657,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              66.455338
            ],
            [
              25.460365,
              66.455338
            ],
            [
              25.460365,
              66.521766
            ],
            [
              25.393937,
              66.521766
            ],
            [
              25.393937,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              66.455338
            ],
            [
              26.124646,
              66.455338
            ],
            [
              26.124646,
              66.521766
            ],
            [
              26.058218,
              66.521766
            ],
            [
              26.058218,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              66.455338
            ],
            [
              26.788927,
              66.455338
            ],
            [
              26.788927,
              66.521766
            ],
            [
              26.722498,
              66.521766
            ],
            [
              26.722498,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              66.455338
            ],
            [
              27.453207,
              66.455338
            ],
            [
              27.453207,
              66.521766
            ],
            [
              27.386779,
              66.521766
            ],
            [
              27.386779,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              66.455338
            ],
            [
              28.117488,
              66.455338
            ],
            [
              28.117488,
              66.521766
            ],
            [
              28.05106,
              66.521766
            ],
            [
              28.05106,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              66.455338
            ],
            [
              28.781768,
              66.455338
            ],
            [
              28.781768,
              66.521766
            ],
            [
              28.71534,
              66.521766
            ],
            [
              28.71534,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              66.455338
            ],
            [
              29.446049,
              66.455338
            ],
            [
              29.446049,
              66.521766
            ],
            [
              29.379621,
              66.521766
            ],
            [
              29.379621,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              65.791057
            ],
            [
              24.796085,
              65.791057
            ],
            [
              24.796085,
              65.857485
            ],
            [
              24.729657,
              65.857485
            ],
            [
              24.729657,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              65.791057
            ],
            [
              26.124646,
              65.791057
            ],
            [
              26.124646,
              65.857485
            ],
            [
              26.058218,
              65.857485
            ],
            [
              26.058218,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              65.791057
            ],
            [
              26.788927,
              65.791057
            ],
            [
              26.788927,
              65.857485
            ],
            [
              26.722498,
              65.857485
            ],
            [
              26.722498,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              65.791057
            ],
            [
              27.453207,
              65.791057
            ],
            [
              27.453207,
              65.857485
            ],
            [
              27.386779,
              65.857485
            ],
            [
              27.386779,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              65.791057
            ],
            [
              28.117488,
              65.791057
            ],
            [
              28.117488,
              65.857485
            ],
            [
              28.05106,
              65.857485
            ],
            [
              28.05106,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              65.791057
            ],
            [
              28.781768,
              65.791057
            ],
            [
              28.781768,
              65.857485
            ],
            [
              28.71534,
              65.857485
            ],
            [
              28.71534,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              65.791057
            ],
            [
              29.446049,
              65.791057
            ],
            [
              29.446049,
              65.857485
            ],
            [
              29.379621,
              65.857485
            ],
            [
              29.379621,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              65.791057
            ],
            [
              30.11033,
              65.791057
            ],
            [
              30.11033,
              65.857485
            ],
            [
              30.043902,
              65.857485
            ],
            [
              30.043902,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              65.126776
            ],
            [
              25.460365,
              65.126776
            ],
            [
              25.460365,
              65.193205
            ],
            [
              25.393937,
              65.193205
            ],
            [
              25.393937,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              65.126776
            ],
            [
              26.124646,
              65.126776
            ],
            [
              26.124646,
              65.193205
            ],
            [
              26.058218,
              65.193205
            ],
            [
              26.058218,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              65.126776
            ],
            [
              26.788927,
              65.126776
            ],
            [
              26.788927,
              65.193205
            ],
            [
              26.722498,
              65.193205
            ],
            [
              26.722498,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              65.126776
            ],
            [
              27.453207,
              65.126776
            ],
            [
              27.453207,
              65.193205
            ],
            [
              27.386779,
              65.193205
            ],
            [
              27.386779,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              65.126776
            ],
            [
              28.117488,
              65.126776
            ],
            [
              28.117488,
              65.193205
            ],
            [
              28.05106,
              65.193205
            ],
            [
              28.05106,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              65.126776
            ],
            [
              28.781768,
              65.126776
            ],
            [
              28.781768,
              65.193205
            ],
            [
              28.71534,
              65.193205
            ],
            [
              28.71534,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              65.126776
            ],
            [
              29.446049,
              65.126776
            ],
            [
              29.446049,
              65.193205
            ],
            [
              29.379621,
              65.193205
            ],
            [
              29.379621,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              64.462496
            ],
            [
              24.796085,
              64.462496
            ],
            [
              24.796085,
              64.528924
            ],
            [
              24.729657,
              64.528924
            ],
            [
              24.729657,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              64.462496
            ],
            [
              25.460365,
              64.462496
            ],
            [
              25.460365,
              64.528924
            ],
            [
              25.393937,
              64.528924
            ],
            [
              25.393937,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              64.462496
            ],
            [
              26.124646,
              64.462496
            ],
            [
              26.124646,
              64.528924
            ],
            [
              26.058218,
              64.528924
            ],
            [
              26.058218,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 109,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              64.462496
            ],
            [
              26.788927,
              64.462496
            ],
            [
              26.788927,
              64.528924
            ],
            [
              26.722498,
              64.528924
            ],
            [
              26.722498,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 111,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              64.462496
            ],
            [
              27.453207,
              64.462496
            ],
            [
              27.453207,
              64.528924
            ],
            [
              27.386779,
              64.528924
            ],
            [
              27.386779,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              64.462496
            ],
            [
              28.117488,
              64.462496
            ],
            [
              28.117488,
              64.528924
            ],
            [
              28.05106,
              64.528924
            ],
            [
              28.05106,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              64.462496
            ],
            [
              28.781768,
              64.462496
            ],
            [
              28.781768,
              64.528924
            ],
            [
              28.71534,
              64.528924
            ],
            [
              28.71534,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              64.462496
            ],
            [
              29.446049,
              64.462496
            ],
            [
              29.446049,
              64.528924
            ],
            [
              29.379621,
              64.528924
            ],
            [
              29.379621,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              63.798215
            ],
            [
              23.467523,
              63.798215
            ],
            [
              23.467523,
              63.864643
            ],
            [
              23.401095,
              63.864643
            ],
            [
              23.401095,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 93,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              63.798215
            ],
            [
              24.131804,
              63.798215
            ],
            [
              24.131804,
              63.864643
            ],
            [
              24.065376,
              63.864643
            ],
            [
              24.065376,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              63.798215
            ],
            [
              24.796085,
              63.798215
            ],
            [
              24.796085,
              63.864643
            ],
            [
              24.729657,
              63.864643
            ],
            [
              24.729657,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              63.798215
            ],
            [
              25.460365,
              63.798215
            ],
            [
              25.460365,
              63.864643
            ],
            [
              25.393937,
              63.864643
            ],
            [
              25.393937,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              63.798215
            ],
            [
              26.124646,
              63.798215
            ],
            [
              26.124646,
              63.864643
            ],
            [
              26.058218,
              63.864643
            ],
            [
              26.058218,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              63.798215
            ],
            [
              26.788927,
              63.798215
            ],
            [
              26.788927,
              63.864643
            ],
            [
              26.722498,
              63.864643
            ],
            [
              26.722498,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              63.798215
            ],
            [
              27.453207,
              63.798215
            ],
            [
              27.453207,
              63.864643
            ],
            [
              27.386779,
              63.864643
            ],
            [
              27.386779,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              63.798215
            ],
            [
              28.117488,
              63.798215
            ],
            [
              28.117488,
              63.864643
            ],
            [
              28.05106,
              63.864643
            ],
            [
              28.05106,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              63.798215
            ],
            [
              28.781768,
              63.798215
            ],
            [
              28.781768,
              63.864643
            ],
            [
              28.71534,
              63.864643
            ],
            [
              28.71534,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              63.798215
            ],
            [
              29.446049,
              63.798215
            ],
            [
              29.446049,
              63.864643
            ],
            [
              29.379621,
              63.864643
            ],
            [
              29.379621,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              63.798215
            ],
            [
              30.11033,
              63.798215
            ],
            [
              30.11033,
              63.864643
            ],
            [
              30.043902,
              63.864643
            ],
            [
              30.043902,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              63.133935
            ],
            [
              22.138962,
              63.133935
            ],
            [
              22.138962,
              63.200363
            ],
            [
              22.072534,
              63.200363
            ],
            [
              22.072534,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              63.133935
            ],
            [
              22.803243,
              63.133935
            ],
            [
              22.803243,
              63.200363
            ],
            [
              22.736815,
              63.200363
            ],
            [
              22.736815,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 93,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              63.133935
            ],
            [
              23.467523,
              63.133935
            ],
            [
              23.467523,
              63.200363
            ],
            [
              23.401095,
              63.200363
            ],
            [
              23.401095,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              63.133935
            ],
            [
              24.131804,
              63.133935
            ],
            [
              24.131804,
              63.200363
            ],
            [
              24.065376,
              63.200363
            ],
            [
              24.065376,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              63.133935
            ],
            [
              24.796085,
              63.133935
            ],
            [
              24.796085,
              63.200363
            ],
            [
              24.729657,
              63.200363
            ],
            [
              24.729657,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              63.133935
            ],
            [
              25.460365,
              63.133935
            ],
            [
              25.460365,
              63.200363
            ],
            [
              25.393937,
              63.200363
            ],
            [
              25.393937,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              63.133935
            ],
            [
              26.124646,
              63.133935
            ],
            [
              26.124646,
              63.200363
            ],
            [
              26.058218,
              63.200363
            ],
            [
              26.058218,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              63.133935
            ],
            [
              26.788927,
              63.133935
            ],
            [
              26.788927,
              63.200363
            ],
            [
              26.722498,
              63.200363
            ],
            [
              26.722498,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              63.133935
            ],
            [
              27.453207,
              63.133935
            ],
            [
              27.453207,
              63.200363
            ],
            [
              27.386779,
              63.200363
            ],
            [
              27.386779,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              63.133935
            ],
            [
              28.117488,
              63.133935
            ],
            [
              28.117488,
              63.200363
            ],
            [
              28.05106,
              63.200363
            ],
            [
              28.05106,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              63.133935
            ],
            [
              28.781768,
              63.133935
            ],
            [
              28.781768,
              63.200363
            ],
            [
              28.71534,
              63.200363
            ],
            [
              28.71534,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              63.133935
            ],
            [
              29.446049,
              63.133935
            ],
            [
              29.446049,
              63.200363
            ],
            [
              29.379621,
              63.200363
            ],
            [
              29.379621,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 111,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              63.133935
            ],
            [
              30.11033,
              63.133935
            ],
            [
              30.11033,
              63.200363
            ],
            [
              30.043902,
              63.200363
            ],
            [
              30.043902,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c250",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.708182,
              63.133935
            ],
            [
              30.77461,
              63.133935
            ],
            [
              30.77461,
              63.200363
            ],
            [
              30.708182,
              63.200363
            ],
            [
              30.708182,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 250
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c110",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              21.408253,
              62.469654
            ],
            [
              21.474681,
              62.469654
            ],
            [
              21.474681,
              62.536082
            ],
            [
              21.408253,
              62.536082
            ],
            [
              21.408253,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 110
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              62.469654
            ],
            [
              22.138962,
              62.469654
            ],
            [
              22.138962,
              62.536082
            ],
            [
              22.072534,
              62.536082
            ],
            [
              22.072534,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 97,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              62.469654
            ],
            [
              22.803243,
              62.469654
            ],
            [
              22.803243,
              62.536082
            ],
            [
              22.736815,
              62.536082
            ],
            [
              22.736815,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              62.469654
            ],
            [
              23.467523,
              62.469654
            ],
            [
              23.467523,
              62.536082
            ],
            [
              23.401095,
              62.536082
            ],
            [
              23.401095,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 95,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              62.469654
            ],
            [
              24.131804,
              62.469654
            ],
            [
              24.131804,
              62.536082
            ],
            [
              24.065376,
              62.536082
            ],
            [
              24.065376,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              62.469654
            ],
            [
              24.796085,
              62.469654
            ],
            [
              24.796085,
              62.536082
            ],
            [
              24.729657,
              62.536082
            ],
            [
              24.729657,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              62.469654
            ],
            [
              25.460365,
              62.469654
            ],
            [
              25.460365,
              62.536082
            ],
            [
              25.393937,
              62.536082
            ],
            [
              25.393937,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 100,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              62.469654
            ],
            [
              26.124646,
              62.469654
            ],
            [
              26.124646,
              62.536082
            ],
            [
              26.058218,
              62.536082
            ],
            [
              26.058218,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 102,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              62.469654
            ],
            [
              26.788927,
              62.469654
            ],
            [
              26.788927,
              62.536082
            ],
            [
              26.722498,
              62.536082
            ],
            [
              26.722498,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              62.469654
            ],
            [
              27.453207,
              62.469654
            ],
            [
              27.453207,
              62.536082
            ],
            [
              27.386779,
              62.536082
            ],
            [
              27.386779,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              62.469654
            ],
            [
              28.117488,
              62.469654
            ],
            [
              28.117488,
              62.536082
            ],
            [
              28.05106,
              62.536082
            ],
            [
              28.05106,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              62.469654
            ],
            [
              28.781768,
              62.469654
            ],
            [
              28.781768,
              62.536082
            ],
            [
              28.71534,
              62.536082
            ],
            [
              28.71534,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              62.469654
            ],
            [
              29.446049,
              62.469654
            ],
            [
              29.446049,
              62.536082
            ],
            [
              29.379621,
              62.536082
            ],
            [
              29.379621,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              62.469654
            ],
            [
              30.11033,
              62.469654
            ],
            [
              30.11033,
              62.536082
            ],
            [
              30.043902,
              62.536082
            ],
            [
              30.043902,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 102,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c250",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.708182,
              62.469654
            ],
            [
              30.77461,
              62.469654
            ],
            [
              30.77461,
              62.536082
            ],
            [
              30.708182,
              62.536082
            ],
            [
              30.708182,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 105,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 250
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              61.805373
            ],
            [
              22.138962,
              61.805373
            ],
            [
              22.138962,
              61.871801
            ],
            [
              22.072534,
              61.871801
            ],
            [
              22.072534,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              61.805373
            ],
            [
              22.803243,
              61.805373
            ],
            [
              22.803243,
              61.871801
            ],
            [
              22.736815,
              61.871801
            ],
            [
              22.736815,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              61.805373
            ],
            [
              23.467523,
              61.805373
            ],
            [
              23.467523,
              61.871801
            ],
            [
              23.401095,
              61.871801
            ],
            [
              23.401095,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              61.805373
            ],
            [
              24.131804,
              61.805373
            ],
            [
              24.131804,
              61.871801
            ],
            [
              24.065376,
              61.871801
            ],
            [
              24.065376,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 104,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              61.805373
            ],
            [
              24.796085,
              61.805373
            ],
            [
              24.796085,
              61.871801
            ],
            [
              24.729657,
              61.871801
            ],
            [
              24.729657,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              61.805373
            ],
            [
              25.460365,
              61.805373
            ],
            [
              25.460365,
              61.871801
            ],
            [
              25.393937,
              61.871801
            ],
            [
              25.393937,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              61.805373
            ],
            [
              26.124646,
              61.805373
            ],
            [
              26.124646,
              61.871801
            ],
            [
              26.058218,
              61.871801
            ],
            [
              26.058218,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 95,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              61.805373
            ],
            [
              27.453207,
              61.805373
            ],
            [
              27.453207,
              61.871801
            ],
            [
              27.386779,
              61.871801
            ],
            [
              27.386779,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 104,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              61.805373
            ],
            [
              28.117488,
              61.805373
            ],
            [
              28.117488,
              61.871801
            ],
            [
              28.05106,
              61.871801
            ],
            [
              28.05106,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              61.805373
            ],
            [
              28.781768,
              61.805373
            ],
            [
              28.781768,
              61.871801
            ],
            [
              28.71534,
              61.871801
            ],
            [
              28.71534,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              61.141093
            ],
            [
              22.138962,
              61.141093
            ],
            [
              22.138962,
              61.207521
            ],
            [
              22.072534,
              61.207521
            ],
            [
              22.072534,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 82,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              61.141093
            ],
            [
              22.803243,
              61.141093
            ],
            [
              22.803243,
              61.207521
            ],
            [
              22.736815,
              61.207521
            ],
            [
              22.736815,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 82,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              61.141093
            ],
            [
              23.467523,
              61.141093
            ],
            [
              23.467523,
              61.207521
            ],
            [
              23.401095,
              61.207521
            ],
            [
              23.401095,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 87,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              61.141093
            ],
            [
              24.796085,
              61.141093
            ],
            [
              24.796085,
              61.207521
            ],
            [
              24.729657,
              61.207521
            ],
            [
              24.729657,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              61.141093
            ],
            [
              25.460365,
              61.141093
            ],
            [
              25.460365,
              61.207521
            ],
            [
              25.393937,
              61.207521
            ],
            [
              25.393937,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              61.141093
            ],
            [
              26.124646,
              61.141093
            ],
            [
              26.124646,
              61.207521
            ],
            [
              26.058218,
              61.207521
            ],
            [
              26.058218,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              61.141093
            ],
            [
              27.453207,
              61.141093
            ],
            [
              27.453207,
              61.207521
            ],
            [
              27.386779,
              61.207521
            ],
            [
              27.386779,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              61.141093
            ],
            [
              28.117488,
              61.141093
            ],
            [
              28.117488,
              61.207521
            ],
            [
              28.05106,
              61.207521
            ],
            [
              28.05106,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              61.141093
            ],
            [
              28.781768,
              61.141093
            ],
            [
              28.781768,
              61.207521
            ],
            [
              28.71534,
              61.207521
            ],
            [
              28.71534,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 90,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c110",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              21.408253,
              60.476812
            ],
            [
              21.474681,
              60.476812
            ],
            [
              21.474681,
              60.54324
            ],
            [
              21.408253,
              60.54324
            ],
            [
              21.408253,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 74,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 110
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              60.476812
            ],
            [
              22.138962,
              60.476812
            ],
            [
              22.138962,
              60.54324
            ],
            [
              22.072534,
              60.54324
            ],
            [
              22.072534,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 71,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              60.476812
            ],
            [
              22.803243,
              60.476812
            ],
            [
              22.803243,
              60.54324
            ],
            [
              22.736815,
              60.54324
            ],
            [
              22.736815,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 77,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              60.476812
            ],
            [
              23.467523,
              60.476812
            ],
            [
              23.467523,
              60.54324
            ],
            [
              23.401095,
              60.54324
            ],
            [
              23.401095,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 76,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              60.476812
            ],
            [
              24.131804,
              60.476812
            ],
            [
              24.131804,
              60.54324
            ],
            [
              24.065376,
              60.54324
            ],
            [
              24.065376,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 88,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              60.476812
            ],
            [
              24.796085,
              60.476812
            ],
            [
              24.796085,
              60.54324
            ],
            [
              24.729657,
              60.54324
            ],
            [
              24.729657,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              60.476812
            ],
            [
              25.460365,
              60.476812
            ],
            [
              25.460365,
              60.54324
            ],
            [
              25.393937,
              60.54324
            ],
            [
              25.393937,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              60.476812
            ],
            [
              26.124646,
              60.476812
            ],
            [
              26.124646,
              60.54324
            ],
            [
              26.058218,
              60.54324
            ],
            [
              26.058218,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 88,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              60.476812
            ],
            [
              26.788927,
              60.476812
            ],
            [
              26.788927,
              60.54324
            ],
            [
              26.722498,
              60.54324
            ],
            [
              26.722498,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              60.476812
            ],
            [
              27.453207,
              60.476812
            ],
            [
              27.453207,
              60.54324
            ],
            [
              27.386779,
              60.54324
            ],
            [
              27.386779,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 96,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 200
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
  "entity_type": "ConiferousForest",
  "year": 2001,
  "vap_doy": 106.26,
  "mean_doy": 106.26,
  "min_doy": 71,
  "max_doy": 125,
  "valid_percent": 0.1915,
  "crs": "EPSG:4326",
  "grid_width": 318,
  "grid_height": 202,
  "sensor": "MODIS Terra",
  "algorithm": "VAP derived from Fractional Snow Cover time series",
  "anomaly": "not_applicable_sample",
  "name": "EBV Phenology Finland \u2014 sampled raster cells",
  "description": "GeoJSON sample generated from the original NetCDF raster. Each feature is one sampled raster cell for coniferous forest in 2001. This is intended for visualisation in the Building Blocks examples page, not as a replacement for the full raster dataset.",
  "features": [
    {
      "type": "Feature",
      "id": "coniferous-2001-r30-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              69.11246
            ],
            [
              27.453207,
              69.11246
            ],
            [
              27.453207,
              69.178888
            ],
            [
              27.386779,
              69.178888
            ],
            [
              27.386779,
              69.11246
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 121,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 30,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r30-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              69.11246
            ],
            [
              28.781768,
              69.11246
            ],
            [
              28.781768,
              69.178888
            ],
            [
              28.71534,
              69.178888
            ],
            [
              28.71534,
              69.11246
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 30,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              68.44818
            ],
            [
              26.124646,
              68.44818
            ],
            [
              26.124646,
              68.514608
            ],
            [
              26.058218,
              68.514608
            ],
            [
              26.058218,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              68.44818
            ],
            [
              26.788927,
              68.44818
            ],
            [
              26.788927,
              68.514608
            ],
            [
              26.722498,
              68.514608
            ],
            [
              26.722498,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              68.44818
            ],
            [
              27.453207,
              68.44818
            ],
            [
              27.453207,
              68.514608
            ],
            [
              27.386779,
              68.514608
            ],
            [
              27.386779,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r40-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              68.44818
            ],
            [
              28.117488,
              68.44818
            ],
            [
              28.117488,
              68.514608
            ],
            [
              28.05106,
              68.514608
            ],
            [
              28.05106,
              68.44818
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 40,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              67.783899
            ],
            [
              24.131804,
              67.783899
            ],
            [
              24.131804,
              67.850327
            ],
            [
              24.065376,
              67.850327
            ],
            [
              24.065376,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              67.783899
            ],
            [
              24.796085,
              67.783899
            ],
            [
              24.796085,
              67.850327
            ],
            [
              24.729657,
              67.850327
            ],
            [
              24.729657,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 119,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              67.783899
            ],
            [
              25.460365,
              67.783899
            ],
            [
              25.460365,
              67.850327
            ],
            [
              25.393937,
              67.850327
            ],
            [
              25.393937,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              67.783899
            ],
            [
              26.124646,
              67.783899
            ],
            [
              26.124646,
              67.850327
            ],
            [
              26.058218,
              67.850327
            ],
            [
              26.058218,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 125,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              67.783899
            ],
            [
              26.788927,
              67.783899
            ],
            [
              26.788927,
              67.850327
            ],
            [
              26.722498,
              67.850327
            ],
            [
              26.722498,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              67.783899
            ],
            [
              27.453207,
              67.783899
            ],
            [
              27.453207,
              67.850327
            ],
            [
              27.386779,
              67.850327
            ],
            [
              27.386779,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 123,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              67.783899
            ],
            [
              28.117488,
              67.783899
            ],
            [
              28.117488,
              67.850327
            ],
            [
              28.05106,
              67.850327
            ],
            [
              28.05106,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 124,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              67.783899
            ],
            [
              28.781768,
              67.783899
            ],
            [
              28.781768,
              67.850327
            ],
            [
              28.71534,
              67.850327
            ],
            [
              28.71534,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r50-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              67.783899
            ],
            [
              29.446049,
              67.783899
            ],
            [
              29.446049,
              67.850327
            ],
            [
              29.379621,
              67.850327
            ],
            [
              29.379621,
              67.783899
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 119,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 50,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              67.119618
            ],
            [
              24.131804,
              67.119618
            ],
            [
              24.131804,
              67.186046
            ],
            [
              24.065376,
              67.186046
            ],
            [
              24.065376,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              67.119618
            ],
            [
              24.796085,
              67.119618
            ],
            [
              24.796085,
              67.186046
            ],
            [
              24.729657,
              67.186046
            ],
            [
              24.729657,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              67.119618
            ],
            [
              25.460365,
              67.119618
            ],
            [
              25.460365,
              67.186046
            ],
            [
              25.393937,
              67.186046
            ],
            [
              25.393937,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              67.119618
            ],
            [
              26.124646,
              67.119618
            ],
            [
              26.124646,
              67.186046
            ],
            [
              26.058218,
              67.186046
            ],
            [
              26.058218,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 121,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              67.119618
            ],
            [
              26.788927,
              67.119618
            ],
            [
              26.788927,
              67.186046
            ],
            [
              26.722498,
              67.186046
            ],
            [
              26.722498,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 122,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              67.119618
            ],
            [
              28.117488,
              67.119618
            ],
            [
              28.117488,
              67.186046
            ],
            [
              28.05106,
              67.186046
            ],
            [
              28.05106,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r60-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              67.119618
            ],
            [
              28.781768,
              67.119618
            ],
            [
              28.781768,
              67.186046
            ],
            [
              28.71534,
              67.186046
            ],
            [
              28.71534,
              67.119618
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 60,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              66.455338
            ],
            [
              24.131804,
              66.455338
            ],
            [
              24.131804,
              66.521766
            ],
            [
              24.065376,
              66.521766
            ],
            [
              24.065376,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 120,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              66.455338
            ],
            [
              24.796085,
              66.455338
            ],
            [
              24.796085,
              66.521766
            ],
            [
              24.729657,
              66.521766
            ],
            [
              24.729657,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              66.455338
            ],
            [
              25.460365,
              66.455338
            ],
            [
              25.460365,
              66.521766
            ],
            [
              25.393937,
              66.521766
            ],
            [
              25.393937,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              66.455338
            ],
            [
              26.124646,
              66.455338
            ],
            [
              26.124646,
              66.521766
            ],
            [
              26.058218,
              66.521766
            ],
            [
              26.058218,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              66.455338
            ],
            [
              26.788927,
              66.455338
            ],
            [
              26.788927,
              66.521766
            ],
            [
              26.722498,
              66.521766
            ],
            [
              26.722498,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              66.455338
            ],
            [
              27.453207,
              66.455338
            ],
            [
              27.453207,
              66.521766
            ],
            [
              27.386779,
              66.521766
            ],
            [
              27.386779,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              66.455338
            ],
            [
              28.117488,
              66.455338
            ],
            [
              28.117488,
              66.521766
            ],
            [
              28.05106,
              66.521766
            ],
            [
              28.05106,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              66.455338
            ],
            [
              28.781768,
              66.455338
            ],
            [
              28.781768,
              66.521766
            ],
            [
              28.71534,
              66.521766
            ],
            [
              28.71534,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r70-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              66.455338
            ],
            [
              29.446049,
              66.455338
            ],
            [
              29.446049,
              66.521766
            ],
            [
              29.379621,
              66.521766
            ],
            [
              29.379621,
              66.455338
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 70,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              65.791057
            ],
            [
              24.796085,
              65.791057
            ],
            [
              24.796085,
              65.857485
            ],
            [
              24.729657,
              65.857485
            ],
            [
              24.729657,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              65.791057
            ],
            [
              26.124646,
              65.791057
            ],
            [
              26.124646,
              65.857485
            ],
            [
              26.058218,
              65.857485
            ],
            [
              26.058218,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              65.791057
            ],
            [
              26.788927,
              65.791057
            ],
            [
              26.788927,
              65.857485
            ],
            [
              26.722498,
              65.857485
            ],
            [
              26.722498,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              65.791057
            ],
            [
              27.453207,
              65.791057
            ],
            [
              27.453207,
              65.857485
            ],
            [
              27.386779,
              65.857485
            ],
            [
              27.386779,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              65.791057
            ],
            [
              28.117488,
              65.791057
            ],
            [
              28.117488,
              65.857485
            ],
            [
              28.05106,
              65.857485
            ],
            [
              28.05106,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 118,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              65.791057
            ],
            [
              28.781768,
              65.791057
            ],
            [
              28.781768,
              65.857485
            ],
            [
              28.71534,
              65.857485
            ],
            [
              28.71534,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 116,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              65.791057
            ],
            [
              29.446049,
              65.791057
            ],
            [
              29.446049,
              65.857485
            ],
            [
              29.379621,
              65.857485
            ],
            [
              29.379621,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 117,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r80-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              65.791057
            ],
            [
              30.11033,
              65.791057
            ],
            [
              30.11033,
              65.857485
            ],
            [
              30.043902,
              65.857485
            ],
            [
              30.043902,
              65.791057
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 80,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              65.126776
            ],
            [
              25.460365,
              65.126776
            ],
            [
              25.460365,
              65.193205
            ],
            [
              25.393937,
              65.193205
            ],
            [
              25.393937,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              65.126776
            ],
            [
              26.124646,
              65.126776
            ],
            [
              26.124646,
              65.193205
            ],
            [
              26.058218,
              65.193205
            ],
            [
              26.058218,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              65.126776
            ],
            [
              26.788927,
              65.126776
            ],
            [
              26.788927,
              65.193205
            ],
            [
              26.722498,
              65.193205
            ],
            [
              26.722498,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              65.126776
            ],
            [
              27.453207,
              65.126776
            ],
            [
              27.453207,
              65.193205
            ],
            [
              27.386779,
              65.193205
            ],
            [
              27.386779,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              65.126776
            ],
            [
              28.117488,
              65.126776
            ],
            [
              28.117488,
              65.193205
            ],
            [
              28.05106,
              65.193205
            ],
            [
              28.05106,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              65.126776
            ],
            [
              28.781768,
              65.126776
            ],
            [
              28.781768,
              65.193205
            ],
            [
              28.71534,
              65.193205
            ],
            [
              28.71534,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r90-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              65.126776
            ],
            [
              29.446049,
              65.126776
            ],
            [
              29.446049,
              65.193205
            ],
            [
              29.379621,
              65.193205
            ],
            [
              29.379621,
              65.126776
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 90,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              64.462496
            ],
            [
              24.796085,
              64.462496
            ],
            [
              24.796085,
              64.528924
            ],
            [
              24.729657,
              64.528924
            ],
            [
              24.729657,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              64.462496
            ],
            [
              25.460365,
              64.462496
            ],
            [
              25.460365,
              64.528924
            ],
            [
              25.393937,
              64.528924
            ],
            [
              25.393937,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              64.462496
            ],
            [
              26.124646,
              64.462496
            ],
            [
              26.124646,
              64.528924
            ],
            [
              26.058218,
              64.528924
            ],
            [
              26.058218,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 109,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              64.462496
            ],
            [
              26.788927,
              64.462496
            ],
            [
              26.788927,
              64.528924
            ],
            [
              26.722498,
              64.528924
            ],
            [
              26.722498,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 111,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              64.462496
            ],
            [
              27.453207,
              64.462496
            ],
            [
              27.453207,
              64.528924
            ],
            [
              27.386779,
              64.528924
            ],
            [
              27.386779,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              64.462496
            ],
            [
              28.117488,
              64.462496
            ],
            [
              28.117488,
              64.528924
            ],
            [
              28.05106,
              64.528924
            ],
            [
              28.05106,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 114,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              64.462496
            ],
            [
              28.781768,
              64.462496
            ],
            [
              28.781768,
              64.528924
            ],
            [
              28.71534,
              64.528924
            ],
            [
              28.71534,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r100-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              64.462496
            ],
            [
              29.446049,
              64.462496
            ],
            [
              29.446049,
              64.528924
            ],
            [
              29.379621,
              64.528924
            ],
            [
              29.379621,
              64.462496
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 100,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              63.798215
            ],
            [
              23.467523,
              63.798215
            ],
            [
              23.467523,
              63.864643
            ],
            [
              23.401095,
              63.864643
            ],
            [
              23.401095,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 93,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              63.798215
            ],
            [
              24.131804,
              63.798215
            ],
            [
              24.131804,
              63.864643
            ],
            [
              24.065376,
              63.864643
            ],
            [
              24.065376,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              63.798215
            ],
            [
              24.796085,
              63.798215
            ],
            [
              24.796085,
              63.864643
            ],
            [
              24.729657,
              63.864643
            ],
            [
              24.729657,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              63.798215
            ],
            [
              25.460365,
              63.798215
            ],
            [
              25.460365,
              63.864643
            ],
            [
              25.393937,
              63.864643
            ],
            [
              25.393937,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              63.798215
            ],
            [
              26.124646,
              63.798215
            ],
            [
              26.124646,
              63.864643
            ],
            [
              26.058218,
              63.864643
            ],
            [
              26.058218,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              63.798215
            ],
            [
              26.788927,
              63.798215
            ],
            [
              26.788927,
              63.864643
            ],
            [
              26.722498,
              63.864643
            ],
            [
              26.722498,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              63.798215
            ],
            [
              27.453207,
              63.798215
            ],
            [
              27.453207,
              63.864643
            ],
            [
              27.386779,
              63.864643
            ],
            [
              27.386779,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 112,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              63.798215
            ],
            [
              28.117488,
              63.798215
            ],
            [
              28.117488,
              63.864643
            ],
            [
              28.05106,
              63.864643
            ],
            [
              28.05106,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 115,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              63.798215
            ],
            [
              28.781768,
              63.798215
            ],
            [
              28.781768,
              63.864643
            ],
            [
              28.71534,
              63.864643
            ],
            [
              28.71534,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              63.798215
            ],
            [
              29.446049,
              63.798215
            ],
            [
              29.446049,
              63.864643
            ],
            [
              29.379621,
              63.864643
            ],
            [
              29.379621,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r110-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              63.798215
            ],
            [
              30.11033,
              63.798215
            ],
            [
              30.11033,
              63.864643
            ],
            [
              30.043902,
              63.864643
            ],
            [
              30.043902,
              63.798215
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 113,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 110,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              63.133935
            ],
            [
              22.138962,
              63.133935
            ],
            [
              22.138962,
              63.200363
            ],
            [
              22.072534,
              63.200363
            ],
            [
              22.072534,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              63.133935
            ],
            [
              22.803243,
              63.133935
            ],
            [
              22.803243,
              63.200363
            ],
            [
              22.736815,
              63.200363
            ],
            [
              22.736815,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 93,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              63.133935
            ],
            [
              23.467523,
              63.133935
            ],
            [
              23.467523,
              63.200363
            ],
            [
              23.401095,
              63.200363
            ],
            [
              23.401095,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              63.133935
            ],
            [
              24.131804,
              63.133935
            ],
            [
              24.131804,
              63.200363
            ],
            [
              24.065376,
              63.200363
            ],
            [
              24.065376,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              63.133935
            ],
            [
              24.796085,
              63.133935
            ],
            [
              24.796085,
              63.200363
            ],
            [
              24.729657,
              63.200363
            ],
            [
              24.729657,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              63.133935
            ],
            [
              25.460365,
              63.133935
            ],
            [
              25.460365,
              63.200363
            ],
            [
              25.393937,
              63.200363
            ],
            [
              25.393937,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 106,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              63.133935
            ],
            [
              26.124646,
              63.133935
            ],
            [
              26.124646,
              63.200363
            ],
            [
              26.058218,
              63.200363
            ],
            [
              26.058218,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              63.133935
            ],
            [
              26.788927,
              63.133935
            ],
            [
              26.788927,
              63.200363
            ],
            [
              26.722498,
              63.200363
            ],
            [
              26.722498,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              63.133935
            ],
            [
              27.453207,
              63.133935
            ],
            [
              27.453207,
              63.200363
            ],
            [
              27.386779,
              63.200363
            ],
            [
              27.386779,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              63.133935
            ],
            [
              28.117488,
              63.133935
            ],
            [
              28.117488,
              63.200363
            ],
            [
              28.05106,
              63.200363
            ],
            [
              28.05106,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              63.133935
            ],
            [
              28.781768,
              63.133935
            ],
            [
              28.781768,
              63.200363
            ],
            [
              28.71534,
              63.200363
            ],
            [
              28.71534,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              63.133935
            ],
            [
              29.446049,
              63.133935
            ],
            [
              29.446049,
              63.200363
            ],
            [
              29.379621,
              63.200363
            ],
            [
              29.379621,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 111,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              63.133935
            ],
            [
              30.11033,
              63.133935
            ],
            [
              30.11033,
              63.200363
            ],
            [
              30.043902,
              63.200363
            ],
            [
              30.043902,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 108,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r120-c250",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.708182,
              63.133935
            ],
            [
              30.77461,
              63.133935
            ],
            [
              30.77461,
              63.200363
            ],
            [
              30.708182,
              63.200363
            ],
            [
              30.708182,
              63.133935
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 110,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 120,
        "source_cell_col": 250
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c110",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              21.408253,
              62.469654
            ],
            [
              21.474681,
              62.469654
            ],
            [
              21.474681,
              62.536082
            ],
            [
              21.408253,
              62.536082
            ],
            [
              21.408253,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 110
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              62.469654
            ],
            [
              22.138962,
              62.469654
            ],
            [
              22.138962,
              62.536082
            ],
            [
              22.072534,
              62.536082
            ],
            [
              22.072534,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 97,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              62.469654
            ],
            [
              22.803243,
              62.469654
            ],
            [
              22.803243,
              62.536082
            ],
            [
              22.736815,
              62.536082
            ],
            [
              22.736815,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              62.469654
            ],
            [
              23.467523,
              62.469654
            ],
            [
              23.467523,
              62.536082
            ],
            [
              23.401095,
              62.536082
            ],
            [
              23.401095,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 95,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              62.469654
            ],
            [
              24.131804,
              62.469654
            ],
            [
              24.131804,
              62.536082
            ],
            [
              24.065376,
              62.536082
            ],
            [
              24.065376,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              62.469654
            ],
            [
              24.796085,
              62.469654
            ],
            [
              24.796085,
              62.536082
            ],
            [
              24.729657,
              62.536082
            ],
            [
              24.729657,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              62.469654
            ],
            [
              25.460365,
              62.469654
            ],
            [
              25.460365,
              62.536082
            ],
            [
              25.393937,
              62.536082
            ],
            [
              25.393937,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 100,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              62.469654
            ],
            [
              26.124646,
              62.469654
            ],
            [
              26.124646,
              62.536082
            ],
            [
              26.058218,
              62.536082
            ],
            [
              26.058218,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 102,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              62.469654
            ],
            [
              26.788927,
              62.469654
            ],
            [
              26.788927,
              62.536082
            ],
            [
              26.722498,
              62.536082
            ],
            [
              26.722498,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              62.469654
            ],
            [
              27.453207,
              62.469654
            ],
            [
              27.453207,
              62.536082
            ],
            [
              27.386779,
              62.536082
            ],
            [
              27.386779,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              62.469654
            ],
            [
              28.117488,
              62.469654
            ],
            [
              28.117488,
              62.536082
            ],
            [
              28.05106,
              62.536082
            ],
            [
              28.05106,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 101,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              62.469654
            ],
            [
              28.781768,
              62.469654
            ],
            [
              28.781768,
              62.536082
            ],
            [
              28.71534,
              62.536082
            ],
            [
              28.71534,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 107,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c230",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              29.379621,
              62.469654
            ],
            [
              29.446049,
              62.469654
            ],
            [
              29.446049,
              62.536082
            ],
            [
              29.379621,
              62.536082
            ],
            [
              29.379621,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 99,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 230
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c240",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.043902,
              62.469654
            ],
            [
              30.11033,
              62.469654
            ],
            [
              30.11033,
              62.536082
            ],
            [
              30.043902,
              62.536082
            ],
            [
              30.043902,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 102,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 240
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r130-c250",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              30.708182,
              62.469654
            ],
            [
              30.77461,
              62.469654
            ],
            [
              30.77461,
              62.536082
            ],
            [
              30.708182,
              62.536082
            ],
            [
              30.708182,
              62.469654
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 105,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 130,
        "source_cell_col": 250
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              61.805373
            ],
            [
              22.138962,
              61.805373
            ],
            [
              22.138962,
              61.871801
            ],
            [
              22.072534,
              61.871801
            ],
            [
              22.072534,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              61.805373
            ],
            [
              22.803243,
              61.805373
            ],
            [
              22.803243,
              61.871801
            ],
            [
              22.736815,
              61.871801
            ],
            [
              22.736815,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              61.805373
            ],
            [
              23.467523,
              61.805373
            ],
            [
              23.467523,
              61.871801
            ],
            [
              23.401095,
              61.871801
            ],
            [
              23.401095,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              61.805373
            ],
            [
              24.131804,
              61.805373
            ],
            [
              24.131804,
              61.871801
            ],
            [
              24.065376,
              61.871801
            ],
            [
              24.065376,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 104,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              61.805373
            ],
            [
              24.796085,
              61.805373
            ],
            [
              24.796085,
              61.871801
            ],
            [
              24.729657,
              61.871801
            ],
            [
              24.729657,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              61.805373
            ],
            [
              25.460365,
              61.805373
            ],
            [
              25.460365,
              61.871801
            ],
            [
              25.393937,
              61.871801
            ],
            [
              25.393937,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 94,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              61.805373
            ],
            [
              26.124646,
              61.805373
            ],
            [
              26.124646,
              61.871801
            ],
            [
              26.058218,
              61.871801
            ],
            [
              26.058218,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 95,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              61.805373
            ],
            [
              27.453207,
              61.805373
            ],
            [
              27.453207,
              61.871801
            ],
            [
              27.386779,
              61.871801
            ],
            [
              27.386779,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 104,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              61.805373
            ],
            [
              28.117488,
              61.805373
            ],
            [
              28.117488,
              61.871801
            ],
            [
              28.05106,
              61.871801
            ],
            [
              28.05106,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r140-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              61.805373
            ],
            [
              28.781768,
              61.805373
            ],
            [
              28.781768,
              61.871801
            ],
            [
              28.71534,
              61.871801
            ],
            [
              28.71534,
              61.805373
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 98,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 140,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              61.141093
            ],
            [
              22.138962,
              61.141093
            ],
            [
              22.138962,
              61.207521
            ],
            [
              22.072534,
              61.207521
            ],
            [
              22.072534,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 82,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              61.141093
            ],
            [
              22.803243,
              61.141093
            ],
            [
              22.803243,
              61.207521
            ],
            [
              22.736815,
              61.207521
            ],
            [
              22.736815,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 82,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              61.141093
            ],
            [
              23.467523,
              61.141093
            ],
            [
              23.467523,
              61.207521
            ],
            [
              23.401095,
              61.207521
            ],
            [
              23.401095,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 87,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              61.141093
            ],
            [
              24.796085,
              61.141093
            ],
            [
              24.796085,
              61.207521
            ],
            [
              24.729657,
              61.207521
            ],
            [
              24.729657,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              61.141093
            ],
            [
              25.460365,
              61.141093
            ],
            [
              25.460365,
              61.207521
            ],
            [
              25.393937,
              61.207521
            ],
            [
              25.393937,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              61.141093
            ],
            [
              26.124646,
              61.141093
            ],
            [
              26.124646,
              61.207521
            ],
            [
              26.058218,
              61.207521
            ],
            [
              26.058218,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              61.141093
            ],
            [
              27.453207,
              61.141093
            ],
            [
              27.453207,
              61.207521
            ],
            [
              27.386779,
              61.207521
            ],
            [
              27.386779,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 200
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c210",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.05106,
              61.141093
            ],
            [
              28.117488,
              61.141093
            ],
            [
              28.117488,
              61.207521
            ],
            [
              28.05106,
              61.207521
            ],
            [
              28.05106,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 92,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 210
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r150-c220",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              28.71534,
              61.141093
            ],
            [
              28.781768,
              61.141093
            ],
            [
              28.781768,
              61.207521
            ],
            [
              28.71534,
              61.207521
            ],
            [
              28.71534,
              61.141093
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 90,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 150,
        "source_cell_col": 220
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c110",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              21.408253,
              60.476812
            ],
            [
              21.474681,
              60.476812
            ],
            [
              21.474681,
              60.54324
            ],
            [
              21.408253,
              60.54324
            ],
            [
              21.408253,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 74,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 110
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c120",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.072534,
              60.476812
            ],
            [
              22.138962,
              60.476812
            ],
            [
              22.138962,
              60.54324
            ],
            [
              22.072534,
              60.54324
            ],
            [
              22.072534,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 71,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 120
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c130",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              22.736815,
              60.476812
            ],
            [
              22.803243,
              60.476812
            ],
            [
              22.803243,
              60.54324
            ],
            [
              22.736815,
              60.54324
            ],
            [
              22.736815,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 77,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 130
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c140",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              23.401095,
              60.476812
            ],
            [
              23.467523,
              60.476812
            ],
            [
              23.467523,
              60.54324
            ],
            [
              23.401095,
              60.54324
            ],
            [
              23.401095,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 76,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 140
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c150",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.065376,
              60.476812
            ],
            [
              24.131804,
              60.476812
            ],
            [
              24.131804,
              60.54324
            ],
            [
              24.065376,
              60.54324
            ],
            [
              24.065376,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 88,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 150
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c160",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              24.729657,
              60.476812
            ],
            [
              24.796085,
              60.476812
            ],
            [
              24.796085,
              60.54324
            ],
            [
              24.729657,
              60.54324
            ],
            [
              24.729657,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 160
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c170",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              25.393937,
              60.476812
            ],
            [
              25.460365,
              60.476812
            ],
            [
              25.460365,
              60.54324
            ],
            [
              25.393937,
              60.54324
            ],
            [
              25.393937,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 91,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 170
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c180",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.058218,
              60.476812
            ],
            [
              26.124646,
              60.476812
            ],
            [
              26.124646,
              60.54324
            ],
            [
              26.058218,
              60.54324
            ],
            [
              26.058218,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 88,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 180
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c190",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              26.722498,
              60.476812
            ],
            [
              26.788927,
              60.476812
            ],
            [
              26.788927,
              60.54324
            ],
            [
              26.722498,
              60.54324
            ],
            [
              26.722498,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 89,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 190
      }
    },
    {
      "type": "Feature",
      "id": "coniferous-2001-r160-c200",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              27.386779,
              60.476812
            ],
            [
              27.453207,
              60.476812
            ],
            [
              27.453207,
              60.54324
            ],
            [
              27.386779,
              60.54324
            ],
            [
              27.386779,
              60.476812
            ]
          ]
        ]
      },
      "properties": {
        "entity_type": "ConiferousForest",
        "year": 2001,
        "vap_doy": 96,
        "crs": "EPSG:4326",
        "grid_width": 318,
        "grid_height": 202,
        "sensor": "MODIS Terra",
        "algorithm": "VAP derived from Fractional Snow Cover time series",
        "source_cell_row": 160,
        "source_cell_col": 200
      }
    }
  ]
}
```

#### ttl
```ttl
@prefix ebv: <https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] ebv:algorithm "VAP derived from Fractional Snow Cover time series" ;
    ebv:anomaly "not_applicable_sample" ;
    ebv:crs "EPSG:4326" ;
    ebv:entity_type <https://maytetoscano.github.io/bblock-ebv-bioclima/vocab/ConiferousForest> ;
    ebv:grid_height 202 ;
    ebv:grid_width 318 ;
    ebv:max_doy 125 ;
    ebv:mean_doy 106.26 ;
    ebv:min_doy 71 ;
    ebv:sensor "MODIS Terra" ;
    ebv:valid_percent 0.1915 ;
    ebv:vap_doy 106.26 ;
    ebv:year 2001 .


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

