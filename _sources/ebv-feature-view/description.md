# EBV Feature View

Discovery layer for the OGC Building Blocks map viewer. Represents EBV raster coverage metadata as GeoJSON Features with semantically linked properties.

## Why this block exists

The OGC BB viewer only renders GeoJSON Features on its map. The CoverageJSON blocks model the raster correctly but cannot be visualized in the default viewer. This block bridges both worlds:

- **GeoJSON geometry**: Finland bounding box as polygon (for the map)
- **Semantic properties**: Each property is linked via `context.jsonld` to ontology URIs
- **Click → linked descriptions**: When you click a feature on the map, property names link to their definitions in other building blocks

## Properties → Building Block Links

| Property | Ontology URI | Defined in |
|----------|-------------|------------|
| `entity_type` | `ebv:entity_type` | EBV Ontology |
| `year` | `ebv:year` | EBV Ontology |
| `vap_doy` | `ebv:vap_doy` | CovJSON Parameter |
| `mean_doy` | `ebv:mean_doy` | CovJSON NdArray (statistics) |
| `crs` | `covjson:referenceSystem` | CovJSON Reference System |
| `grid_width` | `covjson:axisSize` | CovJSON Axis |
| `sensor` | `prov:wasGeneratedBy` | Data Provenance |
| `algorithm` | `prov:used` | Data Provenance |
| `trend_slope` | `ebv:trend_slope` | Phenology Indicators |

## [→ Interactive CoverageJSON Viewer](../../viewer/)

For full raster visualization with pixel-level click interaction, use the dedicated CoverageJSON viewer.
