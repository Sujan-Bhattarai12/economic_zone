# Zoning Protected Areas for Marine Species

## Overview
This project aims to identify Exclusive Economic Zones (EEZ) on the West Coast of the US that are best suited for developing marine aquaculture for various species of oysters. The suitability is determined based on sea surface temperature (SST) and ocean depth.

## Data
- **Sea Surface Temperature (SST):** Average annual SST data from 2008 to 2012 obtained from NOAA's 5km Daily Global Satellite Sea Surface Temperature Anomaly v3.1.
- **Bathymetry:** General Bathymetric Chart of the Oceans (GEBCO) data is used to characterize ocean depth.
- **Exclusive Economic Zones (EEZ):** Maritime boundaries are designated using EEZ data from Marineregions.org.

## Project Outline
1. **Prepare Data:**
   - Load necessary packages and set the working directory.
   - Read the shapefile for the West Coast EEZ (`wc_regions_clean.shp`).
   - Read in SST rasters for the years 2008 to 2012.
   - Combine SST rasters into a raster stack.
   - Read in bathymetry raster (`depth.tif`).
   - Ensure all data are in the same coordinate reference system.

2. **Process Data:**
   - Find the mean SST from 2008-2012.
   - Convert SST data from Kelvin to Celsius.
   - Crop depth raster to match the extent of the SST raster.
   - Resample the depth data to match the resolution of the SST data.

3. **Find Suitable Locations:**
   - Reclassify SST and depth data into suitable and unsuitable locations for oysters.
   - Find locations that satisfy both SST and depth conditions using the `lapp()` function.

4. **Determine the Most Suitable EEZ:**
   - Select suitable cells within West Coast EEZs.
   - Find the area of grid cells and the total suitable area within each EEZ.
   - Determine the percentage of each zone that is suitable.

5. **Visualize Results:**
   - Visualize suitable regions within each EEZ using basemaps.
   - Plot the percentage of suitable area by region.
   - Generate alternative maps including basemaps for the Economic Zone.

6. **Broaden the Workflow:**
   - Create a function (`economic_zone_finder`) for finding suitable areas for any fish species based on user-defined temperature and depth requirements.
   - Run the function for a specific species (e.g., Abra aequalis) as an example.

## References
- Hall, S. J., et al. (2011). *Blue Frontiers: Managing the Environmental Costs of Aquaculture.*
- Gentry, R. R., et al. (2017). "Mapping the global potential for marine aquaculture." *Nature Ecology & Evolution*, 1, 1317-1324.
- GEBCO Compilation Group (2022). GEBCO_2022 Grid (doi:10.5285/e0f0bb80-ab44-2739-e053-6c86abc0289c).

Feel free to explore and adapt this project for your specific needs.

