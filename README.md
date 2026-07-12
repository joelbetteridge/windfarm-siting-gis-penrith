# Chasing the Wind: GIS-Based Wind Farm Siting Assessment (Penrith, Cumbria)

## Overview
This project uses multi-criteria GIS analysis in ArcGIS Pro to identify 
optimal onshore wind turbine sites within a study area near Penrith, 
Cumbria, UK — in support of the UK's 2030 clean power target. The workflow 
combines wind resource downscaling, suitability screening, energy-based 
site ranking, and viewshed/population impact analysis to identify and 
evaluate the three top-performing candidate sites.

## Study area
A ~2,500 ha rectangular sub-region ("a62") within the wider Penrith area, 
Cumbria, northern England (OS grid: SW 334349,509087 – NE 386094,586668).

## Data sources
- 30m SRTM Digital Elevation Model (DEM)
- 5km Met Office mean April wind speed data (1981–2010)
- 25m CEH Land Cover Map
- OS road network and settlement point data
- National Park boundaries
- LSOA boundaries and 2011 Census population data

## Methodology
1. **Wind speed downscaling** — 5km wind speed data downscaled to 30m 
   resolution using a power law wind profile, adjusted for each cell's 
   elevation relative to its 5km zonal mean, at 80m turbine hub height.
2. **Energy estimation** — Applied a Siemens turbine power curve 
   (Power = 230 × wind speed − 690 kW) to estimate monthly energy output 
   per turbine.
3. **Suitability screening** — Applied six spatial constraints (elevation, 
   gradient, road proximity, urban/settlement buffers, National Park 
   exclusion) via conditional raster overlay to isolate viable sites.
4. **Site ranking** — Top 0.5% of suitable cells (by energy output) 
   converted to polygons and ranked using zonal statistics; top 3 sites 
   selected.
5. **Viewshed & population impact** — 20km-radius viewshed analysis from 
   each candidate site, joined to 2011 Census data via LSOA boundaries to 
   estimate visual exposure and affected population.

Full step-by-step ArcGIS Pro tool sequence is documented in `report.pdf` 
(Appendix).

## Key findings
- Estimated turbine energy potential ranged from 0–1,034 MWh/month, 
  strongly driven by topography (highest along North Pennine and Lake 
  District ridges).
- Suitability constraints — particularly National Park exclusion — removed 
  ~20% of otherwise viable terrain.
- The three top-ranked sites (501–523 MWh/month) had minimal population 
  visual impact: only ~0.8% of the 160,088 residents across 104 LSOAs had 
  any line-of-sight to the proposed sites.

## Tools used
ArcGIS Pro 3.6.0 — Spatial Analyst (raster calculator, zonal statistics, 
slope, visibility/viewshed), Conversion Tools, Analysis Tools, feature 
joins.

## Skills demonstrated
Multi-criteria spatial suitability analysis, raster algebra, DEM-based 
terrain analysis, viewshed/visibility modelling, spatial data joins, 
reproducible GIS workflow documentation.

## Contents
- `report.pdf` — full write-up including methods, results, discussion, 
  and step-by-step ArcGIS appendix
- `figures/` — output maps (energy potential, suitability, visibility)
