# Indonesia GeoJSON & TopoJSON Maps (38 Provinces)

This repository provides Indonesia province boundaries in **GeoJSON** and **TopoJSON** format, updated to **38 provinces** (including the newer Papua-region provinces).

Source article: https://dev.to/denyherianto/geojson-topojson-maps-of-indonesia-38-provinces-591n

## What’s Included

- `GeoJSON/indonesia-38-provinces.geojson` (≈ 254 KB)
- `TopoJSON/indonesia-38-provinces.topo.json` (≈ 49 KB)

Both files contain **38 features/geometries** (one per province).

## GeoJSON vs TopoJSON (Quick Recap)

| Feature | GeoJSON | TopoJSON |
|---|---|---|
| Readability | High | Medium |
| File size | Larger | Smaller |
| Browser performance | Can be heavier | Typically faster |
| Best for | Simpler maps / overlays | Data viz / dashboards (D3) |

## Data Fields (Properties)

The province name and code are available under `properties`:

- `PROVINSI`: province name (e.g. `Jawa Barat`)
- `KODE_PROV`: province code as a string (e.g. `32`)

GeoJSON (`GeoJSON/indonesia-38-provinces.geojson`) also includes:

- `id`: string identifier (same value as `KODE_PROV` in this dataset)

## Usage Examples

### Leaflet (GeoJSON)

```js
import L from "leaflet";
import provinces from "./GeoJSON/indonesia-38-provinces.geojson";

L.geoJSON(provinces, {
  style: {
    color: "#1e40af",
    weight: 1,
    fillOpacity: 0.6,
  },
  onEachFeature: (feature, layer) => {
    layer.bindPopup(feature.properties.PROVINSI);
  },
}).addTo(map);
```

### D3 (TopoJSON → GeoJSON)

```js
import * as d3 from "d3";
import { feature } from "topojson-client";
import topoData from "./TopoJSON/indonesia-38-provinces.topo.json";

const objectName = "indonesia-38-prov-topo";
const provinces = feature(topoData, topoData.objects[objectName]);

const width = 800;
const height = 600;

const svg = d3
  .select("#map")
  .append("svg")
  .attr("width", width)
  .attr("height", height);

const projection = d3
  .geoMercator()
  .fitSize([width, height], provinces);

const path = d3.geoPath().projection(projection);

svg
  .selectAll("path")
  .data(provinces.features)
  .enter()
  .append("path")
  .attr("d", path)
  .attr("fill", "#60a5fa")
  .attr("stroke", "#1e3a8a")
  .append("title")
  .text((d) => d.properties.PROVINSI);
```

## Common Use Cases

- Choropleth maps (elections, demographics, analytics)
- Logistics/coverage planning
- Civic/government dashboards
- Disaster & flood tracking
- Mobile-first data visualizations

## Notes

- Province boundaries and naming can differ across sources and time. If you spot an issue (typo, missing/extra province, mismatched code), please open an issue or PR with references.

