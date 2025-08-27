Learning
- From model -> Ask JPL MLD vs KPHbbl, is there a MLD reconstructed
- DOnnée réel -> Profil, vérifier avec Clément Base de données
- wind / pression ERA5 / wind wave sea: journalier 15 ans. 
- SST: ODysea
- SSS: 
- SSH: 
- wind wave SWH ? 
- courant total GlobCurrent ?
- 

 https://data.cci.ceda.ac.uk/thredds/fileServer/esacci/sea_surface_salinity/data/v05.5/GLOBALv5.5/7days/2010/ESACCI-SEASURFACESALINITY-L4-SSS-GLOBAL-MERGED_OI_7DAY_RUNNINGMEAN_DAILY_0.25deg-20100110-fv5.5.nc
Download Tabe



OSSE:

| Data       | From                      | Size | To                                                     |
| ---------- | ------------------------- | ---- | ------------------------------------------------------ |
| LLC KPPHBL | Jackzilla:/ODYSEA1/MITGCM | 490  | alfheim:/mnt/data_b/mitgcm/KPPhbl                      |
| LLC SST    | Jackzilla:/ODYSEA1/MITGCM | 411  | alfheim:/mnt/data_b/mitgcm/SST                         |
| LLC SSS    | Jackzilla:/ODYSEA1/MITGCM | 345  | alfheim:/mnt/data_b/mitgcm/SSS                         |
| LLC Wind   | Jackzilla:/ODYSEA1/MITGCM | 1300 | alfheim:/mnt/data_b/mitgcm/wind10m                     |
| LLC SSC    | Jackzilla:/ODYSEA1/MITGCM | 1100 | alfheim:/mnt/data_b/mitgcm/SSC                         |
| LLC SSH    | Jackzilla:/ODYSEA1/MITGCM | 474  | alfheim:/mnt/data_12t/llc2160_daily_latlon_SSH_notides |
|            |                           |      |                                                        |

Observation

| Data                                                                                                                                                                                                                                                                                                                | From  | Size       | Period    | To                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ---------- | --------- | ---------------------------------------------------------------------------------------------------------------- |
| "10m_u_component_of_wind",<br> "10m_v_component_of_wind",<br> "mean_sea_level_pressure",<br> "mean_wave_direction",<br> "mean_wave_period",<br> "significant_height_of_combined_wind_waves_and_swell",<br>  "mean_direction_of_wind_waves",<br> "mean_period_of_wind_waves",<br> "significant_height_of_wind_waves" | CDS   | 440 for 7y | 2016-2024 | data_lg:era5_wind                                                                                                |
| ARGO Float                                                                                                                                                                                                                                                                                                          | CMEMS | 28         | All       | _data_lg:INSITU_GLO_PHYBGCWAV_DISCRETE_MYNRT_013_030/cmems_obs-ins_glo_phybgcwav_mynrt_na_irr_202311/history/PF_ |
| SST (odysea or MWOI)                                                                                                                                                                                                                                                                                                |       |            |           |                                                                                                                  |
| SSS CCI                                                                                                                                                                                                                                                                                                             |       |            |           |                                                                                                                  |
| SSH cmems_008_046                                                                                                                                                                                                                                                                                                   |       |            |           |                                                                                                                  |
| SSC cmems_015_003                                                                                                                                                                                                                                                                                                   |       |            |           |                                                                                                                  |
|                                                                                                                                                                                                                                                                                                                     |       |            |           |                                                                                                                  |



