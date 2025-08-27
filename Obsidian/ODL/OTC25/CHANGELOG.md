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