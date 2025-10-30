
2025-10-25
--
Reprocess Teledyne75 ADCP raw files using coda
 4 types of files are available:

* LTA files are 10min averages computed on board the instrument
* STA files are 5 min averages directly computed on board the instrument
* ENR_60 are 1 min averages reprocessed using pings
* ENR_300 are 5 min averages reprocessed using pings
Files for leg 3 and leg 4 are here:

[ftp://ftp.eopp.esa.int/from_esa/processed-geomatics-instruments/ADCP_Teledyne75_from_coda](ftp://ftp.eopp.esa.int/from_esa/processed-geomatics-instruments/ADCP_Teledyne75_from_coda)


2025-09-20
--
* Add surface drifting buoys Spot and Melodi trajectories in ftp://ftp.eopp.esa.int/from_esa/otc25-raw-instruments/spot_trajectory_20250918 and ftp://ftp.eopp.esa.int/from_esa/otc25-raw-instruments/MELODI/melodi_trajectory_20250918
* Update EK80 netcdf data for lofoten eddy as ADCP info were missing, part of the ADCP is still missing for the 24th of April


2025-09-08
-------------------
* Add EK80 data on interesting test cases in ftp://ftp.eopp.esa.int/from_esa/processed-geomatics-instruments/netcdf-ek80

| Directory               | Description                                  | Period                            | Leg | Size nc |    
| ----------------------- | -------------------------------------------- | --------------------------------- | --- | ------- | 
| netcdf-convergence-st2 | Convergence area (station 2)                 | 20250423T225920 - 20250424T215830 | 3   | 6.9     | 
| netcdf-lofoten          | Lofoten eddy (Station 4)                     | 20250425T050000 - 20250426T100000 | 3   | 60.4    |     
| netcdf-eddy-sl8         | Eddy, Slow 8                                 | 20250429T205900 - 20250429T235900 | 3   | 5.5     |     
| netcdf-st9              | Bloom (station 9 A&B)                        | 20250501T045600 - 20250501T145621 | 3   | 16.4    |     
| netcdf-swot             | SWOT pass                                    | 20250511T235958 - 20250512T180038 | 4   | 69      |     
| netcdf-sl17-drifter     | Slow 17, deployement drifters                | 20250515T080000 - 20250515T110000 | 4   | 5.5     |     
| netcdf-st18             | PAP station plus eddy (st18)                 | 20250517T225950 - 20250518T225750 | 4   | 39.4    |     
| netcdf-st20             | Upwelling + Internal wave                    | 20250522T015770 - 20250522T135810 | 4   | 51      |     
| netcdf-st24-meddies     | Meddies (station 24)                         | 20250526T095600 - 20250526T205721 | 4   | 15      |     
| netcdf-gibraltar         | Internal waves and Alboran gyre (station 25)| 20250527T110000 - 20250527T235700 | 4   | 60      |     



2025-08-22
--------------------
* Add Vardyn SSH / SST / Geostrophic and cyclogeostrophic current reconstruction
	*  nadir + SST: ftp://ftp.eopp.esa.int/from_esa/raw-downloaded/vardyn_nadir
	* nadir + SWOT + SST: ftp://ftp.eopp.esa.int/from_esa/raw-downloaded/vardyn_nadir_swot

2025-07-22
--------------------
* Update GMX-Gill wind processing, 
	* data have been added in a new directory: processed-geomaatics-intruments/GMX-Gill-wind
	* scripts have been added in a new directory processing-scripts/GMX-Gill-scripts
* Create processing-scripts directory to store all necessary scripts to generate processed data

2025-06-20
---------------------
Intial Push of data, the architecture is the following:
* from_esa
	* OVL-shapes: json and geojson with routes, ARGO, AIS data
	* geomatrics-raw: intruments from lehmkuhl (see catalog sheet [OTC25-data- inventory.xlsx](https://esait.sharepoint.com/:x:/r/sites/Ocean.Training/Shared%20Documents/17.%20Data%20-%20Information%20-%20FTP/OTC25-data-%20inventory.xlsx?d=w4479844078f4435fa967f7ebef9889f4&csf=1&web=1&e=7cfNyL) for more details )
	* idf-seascope: data compatible with SEAScope 
	* lecturers: Backup of lecturers drive (2025-06-06)
	* otc26-raw-instruments: Raw data from instruments brought my lecturers
	* processed-geomatics-instruments: Processed data 
	* raw-downloaded: Raw satellite and in-situ data that have been downloaded during the voyage
	
* to_esa:
	* shared_all: Backup of shared_all drive (2025-06-06)