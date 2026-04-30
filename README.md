# EBV Phenology Finland — 17 OGC Building Blocks

Complete modelling of the **CoverageJSON UML** (OGC 21-069r2, 9 classes) plus **7 EBV-specific blocks**.

## CoverageJSON UML → Building Blocks (1:1 mapping)

```
CoverageCollection  →  covjson-coverage-collection
  └─ 1..* Coverage  →  covjson-coverage
       ├─ 1 Domain  →  covjson-domain
       │   ├─ 1..* Axis           →  covjson-axis
       │   └─ * ReferenceSystem   →  covjson-reference-system
       ├─ * ParameterGroup        →  covjson-parameter-group
       │   └─ 1..* Parameter      →  covjson-parameter
       └─ 1..* Range              →  covjson-range
            ├─ 1..* NdArray       →  covjson-ndarray
            └─ 0..1 TiledNdArray  →  covjson-tiled-ndarray
```

## EBV-Specific Blocks

| Block | Layer | Purpose |
|-------|-------|---------|
| EBV Dataset Profile | Identity | What EBV class/name/entities |
| Phenology Indicators | Analysis | Trends, anomalies, change points |
| Data Provenance | Lineage | W3C PROV: sensor → algorithm → product |
| Data Quality | Quality | Uncertainty ±9d, bias ~3d |
| EBV Phenology Ontology | Semantics | OWL 4 languages (EN, ES, ZH, RO) |
| Policy Alignment | Policy | GBF, SDGs, IPBES, NBSAP |
| Ecosystem Services Link | Services | Pollination, carbon, water |

## Dataset
Vegetation Phenology in Finland (2001–2018). DOI: [10.25829/xf8ek6](https://doi.org/10.25829/xf8ek6). 
MODIS Terra → FSC (coniferous) / NDWI (deciduous) → Start of VAP (Day of Year). CC BY 4.0.
