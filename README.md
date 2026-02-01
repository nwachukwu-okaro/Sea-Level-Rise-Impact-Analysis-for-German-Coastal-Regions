##Sea Level Rise Impact Analysis for German Coastal Regions
1. Project Overview

This project analyses the potential impact of sea level rise (SLR) on Germany’s coastal regions and islands, focusing on simulated scenarios of 2 m and 4 m sea level rise.

The objective is to identify low-lying land areas that would become inundated, calculate the total land area affected, and present the results in a way that supports risk assessment, spatial planning, and climate adaptation strategies.

The final output enables decision-makers, researchers, and planners to:

Visualize flood-prone areas clearly

Quantify land loss in square kilometres (km²)

Repeat the analysis easily for any future sea level value

2. Software, Tools, and Skills Used
Software

QGIS (Long Term Release – QGIS 3.x LTR)

QGIS Processing Toolbox

QGIS Print Layout

Core GIS Skills Applied

Raster data processing

Vector data processing

Coordinate Reference System (CRS) management

Spatial clipping and buffering

Raster calculation and reclassification

Raster-to-vector conversion

Attribute table analysis and area calculation

Cartographic design and map layout

3. Data Utilized
3.1 Digital Elevation Model (DEM)

Dataset: Copernicus GLO-30 DEM

Resolution: ~30 meters

Source: Copernicus / ESA

Purpose:
Used to represent ground elevation and determine which areas lie at or below specific sea level thresholds.

3.2 Administrative Boundary Data

Dataset: Germany national boundary shapefile

Source: GADM (Global Administrative Areas)

Purpose:
Defines the official spatial extent of Germany, ensuring the analysis remains geographically accurate.

4. Step-by-Step Methodology
Step 1: Load and Organize Base Data

The German administrative boundary and the Copernicus DEM were loaded into QGIS and organized logically within the project.

Why this step is important:
All subsequent spatial analysis depends on having reliable elevation and boundary data correctly loaded.

Step 2: Coordinate Reference System (CRS) Harmonization

All layers were reprojected into a common projected CRS (ETRS89 / UTM Zone 32N – EPSG:25832).

Why this step is important:

Prevents spatial misalignment

Ensures accurate distance and area calculations

Avoids processing errors during clipping and raster calculations

Effect if skipped:
Results would be spatially incorrect and area calculations unreliable.

Step 3: Creation of Buffer Around Area of Interest (AOI)

A buffer was created around the German coastal AOI.

Why this step is important:

Ensures coastal edge pixels are fully included

Prevents DEM clipping from cutting off near-shore low-lying areas

Improves accuracy of flood simulation along coastlines

Effect if skipped:
Flooded areas near coastlines may be underestimated or lost.

Step 4: Clipping the DEM to the Buffered AOI

The DEM was clipped using the buffered AOI.

Why this step is important:

Reduces file size

Improves processing speed

Limits analysis strictly to relevant geographic areas

Step 5: Sea Level Rise Simulation (Raster Calculator)

Raster Calculator was used to simulate flooding using expressions such as:

DEM <= 2   (for 2m SLR)
DEM <= 4   (for 4m SLR)


Output:
Binary raster where:

1 = Flooded

0 = Not flooded

Why this step is important:
This is the core analytical step that identifies flood-prone land.

Step 6: Raster Symbology

The flood raster was styled using:

Blue → Flooded areas

Light gray → Unaffected areas

Why this step is important:
Clear visual interpretation of flood risk for non-technical users.

Step 7: Clipping Flood Raster to AOI

The flood raster was clipped again to the buffered AOI.

Why this step is important:
Ensures results are spatially consistent and suitable for reporting.

Step 8: Raster to Vector Conversion

The flood raster was converted to vector polygons.

Why this step is important:
Area calculations are more transparent and manageable in vector format.

Step 9: Extraction of Flooded Areas Only

Only polygons with value 1 (flooded) were selected and saved as a new layer.

Why this step is important:
Prevents unaffected land from inflating total flooded area calculations.

Step 10: Area Calculation

A new attribute field was created using:

area($geometry) / 1,000,000


Result:
Flooded area calculated in square kilometres (km²).

Step 11: Statistical Summary

The Statistics panel was used to calculate the total flooded area for each sea level scenario.

Step 12: Cartographic Presentation

Final maps were produced using:

Google Hybrid basemap

Clean legend (Flooded / Not Flooded)

Scale bar, north arrow, and annotation

5. Interpretation of Results

Flood-impacted areas are shown in blue

Unaffected land areas are shown in light gray

Low-lying coastal zones and island regions are disproportionately affected

Higher sea level scenarios significantly increase inland penetration of flooding

For example:

A 4 m sea level rise scenario indicates a potential loss of 32,857.60 km² of land across Germany’s coastal and island regions.

6. Key Project Outcomes

Repeatable workflow for any sea level value

Accurate land-loss quantification in km²

Clear, presentation-ready maps

Beginner-friendly methodology suitable for academic use

7. Conclusion

This project demonstrates how open geospatial data and QGIS can be used to model climate-driven sea level rise impacts with high transparency and reproducibility. The workflow supports both scientific analysis and policy-oriented decision making, making it suitable for academic research, environmental planning, and coastal risk assessment.
