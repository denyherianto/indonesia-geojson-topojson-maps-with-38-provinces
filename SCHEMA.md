# Dataset Schema

This repository contains province boundaries for Indonesia (38 provinces) in:

- GeoJSON: `GeoJSON/indonesia-38-provinces.geojson`
- TopoJSON: `TopoJSON/indonesia-38-provinces.topo.json`

## Coordinate reference system

GeoJSON coordinates are expected to be longitude/latitude in **WGS84** (EPSG:4326), as is typical for GeoJSON.

## Properties

Each province feature includes:

- `PROVINSI` (string): Province name (example: `Jawa Barat`)
- `KODE_PROV` (string): Province code (example: `32`)

GeoJSON features also include:

- `id` (string): Identifier for the feature (in this dataset it matches `KODE_PROV`)

## Expected counts

- **38** features/geometries (one per province)

