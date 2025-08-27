<div style="background-color: #FFFFFF; padding: 0px; border-radius: 50px;">
    <p style="text-align:center; font-size:200%; font-family: 'Arial', sans-serif; color: #1d1a24; font-weight: 350">
        OVL portal: data of interest for OOE
    </p>
</div>


   ![[odl-logo-full-color.png|center|250]]

**<center>Lucile Gaultier, lucile.gaultier@oceandatalab.com, OceanDataLab </center>**
<center>Release: 2025-08-10 </center>

 ------------------------------------------------------------------------ 


This document lists data in the OVL portal that can be of interest for the One Ocean Expedition. We have listed only products that are easy to understand for every one and processed in near real time. Let us know if you have more specific needs, we can redirect you to the proper product if available.

Note: 
1. Satellite data can be provided at different level (L1, L2, L3 or L4) depending on the processing that has been set up:
	* L1: Level 1 products are in the geometry of the sensor, with as little processing as possible (e.g. True Color or False Color products)
	* L2: Level 2 products are in the geometry of the sensor, the resolution can be a bit lower than L1 as geophysical variables are retrieved (e.g Radial velocity, Sea Surface Temperature, Chlorophyll)
	* L3: Level 3 are filtered and interpolated in space and time to provide data from the same sensor or sensor type on the same grid
	* L4: Level 4 are interpolation in space and time of a wide variety of remote sensor observation to reconstruct a geophysical variable
2. Models are provided with their forecast over few days
  

# Ice

| OVL Product                                                | Type         | Resolution | Sensor type                               | Coverage                            | Revisit                       | Limitation                                   |
| ---------------------------------------------------------- | ------------ | ---------- | ----------------------------------------- | -------------------------------------- | ----------------------------- | -------------------------------------------- |
| SAR roughness Sentinel-1 (ESA, ODL)                        | Satellite L2 | 20-40m     | SAR (synthetic Aperture Radar)            | Coastal / in specific areas for images | ~3 days at mid latitude       |                                              |
| True Color Sentinel-2 (ESA, Sinergise)                     | Satellite L1 | 10m        | Visible (RGB Bands)                       | Coastal                                | ~3 days at mid latitude       | Cannot see through clouds, during night      |
| False Color Sentinel-2 (ESA, Sinergise)                    | Satellite L1 | 10m        | Visible / Near Infra Red (NIR / GB Bands) | Coastal                                | ~3 days at mid latitude       | Cannot see through clouds, during night      |
| True color OLCI Sentinel-3 (ESA)                           | Satellite L1 | 300m       | Visible (RGB Bands for True Color)        | Global                                 | ~ 1 to 2 days at mid-latitude | Cannot see through clouds, during night      |
| False Color SLSTR Sentinel-3 (ESA)                         | Satellite L1 | 500m       | Visible / Near Infra Red (NIR G B bands)  | Global                                 | ~ 1 to 2 days at mid-latitude | Cannot go through thick clouds, during night |
| Sea ice concentration AMSR Aqua GCOM-W1 (JAXA, Uni Bremen) | Satellite L3 | 6.25 km    | Microwave                                 | Global                                 | 1 day                         | Low resolution                               |

  

# Chlorophyll

| OVL Product                              | Type         | Resolution | Sensor type | Coverage | Revisit                  | Limitation                                                                        |
| ---------------------------------------- | ------------ | ---------- | ----------- | ----------- | ----------------------------- | --------------------------------------------------------------------------------- |
| Chl-a (oc4me) OLCI Sentinel-3 (ESA, ODL) | Satellite L2 | 300m       | Visible     | Global,     | ~ 1 to 2 days at mid-latitude | Cannot measure through clouds nor during night, reconstruction algorithm can fail |
|                                          |              |            |             |             |                               |                                                                                   |

  

  

# Sea Surface Temperature

| OVL Product                           | Type         | Resolution | Sensor type           | Coverage                         | Revisit                       | Limitation                                                             |
| ------------------------------------- | ------------ | ---------- | --------------------- | -------------------------------- | ----------------------------- | ---------------------------------------------------------------------- |
| SST-SLSTR Sentinel-3 (ESA, ODL)       | Satellite L2 | 1 km       | Infra Red             | Global                           | ~ 1 to 2 days at mid-latitude | Cannot see through thick clouds                                        |
| SST L3C SEVIRI MSG (Météo France)     | Satellite L3 | ~5 km      | Infra Red             | East Atlantic, West Indian Ocean | 1 hour                        | Geostationnary, only covers a region at mid/low  latitude (below 60ºN) |
| SST L3C ABI GOES-16/19 (Météo France) | Satellite L3 | ~5 km      | Infra Red             | West Atlantic                    | 1 hour                        | Geostationnary, only covers a region at mid/low  latitude (below 60ºN) |
| SST L3C ABI GOES-18 (NOAA)            | Satellite L3 | ~5 km      | Infra Red             | East Pacific                     | 1 hour                        | Geostationnary, only covers a region at mid/low  latitude (below 60ºN) |
| SST Odyssea Global L4 (IFREMER)       | Satellite L4 | 25 km      | Infra Red + MicroWave | Global                           | 1 day                         | Can have erroneous  / smooth dynamical structures due to interpolation |
| SST Odyssea Regional L4 (IFREMER)     | Satellite L4 | 4 km       | Infra Red + MicroWave | Med, Natl, Agulhas, Brazil       | 1 day                         | Can have erroneous  / smooth dynamical structures due to interpolation |
| SST MicrowaveOI v5.x L4 (RSS)         | Satellite L4 | 25-100km   | MicroWave             | Global                           | 1 day                         | Low resolution, no data at less than 50km from coast                   |


# Surface Current

| OVL Product                                                  | Type         | Resolution | Sensor type                        | Coverage | Revisit | Limitation                                                              |
| ------------------------------------------------------------ | ------------ | ---------- | ---------------------------------- | -------- | ------- | ----------------------------------------------------------------------- |
| Geostrophic surface current streamlines (GlobCurrent, CMEMS) | Satellite L4 | 12.5 km    | Altimeters                         | Global   | daily   | Only geostrophic currents are represented at mesoscale                  |
| Total surface current streamlins (GlobCurrent, CMEMS)        | Satellite L4 | 12.5km     | Altimeters +  Drifters + Wind ERA5 | Global   | hourly  | Only geostrophic and wind induced currents are represented at mesoscale |

  

# Wind

| OVL Product                            | Type  | Resolution | Sensor type | Coverage | Revisit | Limitation |
| -------------------------------------- | ----- | ---------- | ----------- | -------- | ------- | ---------- |
| 10m wind barbs model ECMWF 1/10º hourly | Model | 10km       | NA          | Global   | Hourly  | Model      |
| 10m wind barbs streamlines ECMWF 1/10º hourly | Model | 10km       | NA          | Global   | Hourly  | Model      |

# Wave

| OVL Product                            | Type  | Resolution | Sensor type | Coverage | Revisit | Limitation |
| -------------------------------------- | ----- | ---------- | ----------- | -------- | ------- | ---------- |
| SWH model MFWAM (MétéoFrance, CMEMS)| Model | 8km       | NA          | Global   | 3-Hour | Model      |
| Wave 1rst spectral partition model MFWAM (Météo-France, CMEMS) | Model | 9 km       | NA          | Global   | 3-Hour  | Model      |


# Other


| OVL Product                            | Type  | Resolution | Sensor type | Coverage | Revisit | Limitation |
| -------------------------------------- | ----- | ---------- | ----------- | -------- | ------- | ---------- |
| Stastraad Lehmkuhl (IMR) | Model | NA       | GPS from Ferrybox | Global   | Hourly  | Needs Ferrybox turned on |
