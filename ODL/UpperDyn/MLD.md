Learning
- From model -> Ask JPL MLD vs KPHbbl, is there a MLD reconstructed
- DOnnée réel -> Profil, vérifier avec Clément Base de données
- wind / pression ERA5 / wind wave sea: journalier 15 ans. 
- SST: ODysea
- SSS: climato ESA
- SSH: 
- wind wave SWH ? from ERA5
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
| ARGO MLD CLement                                                                                                                                                                                                                                                                                                    |       |            |           |                                                                                                                  |
| ARGO MLD Guillaume                                                                                                                                                                                                                                                                                                  |       |            |           |                                                                                                                  |

| Variable                 | Long Name                                                                                                                                                                                                                                                  | Unit  |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| MLD                      | surface mixed layer depth = min(mld_dreqdtm02, mld_dt02) = depth of theocean surface layer mixed in BOTH temperature and salinity = "optimal" MLD estimation, to be used e.g. for biological studies (for flags details see the flags of the 2 basic mlds) | m     |
| N2                       | Brunt Vaisila frequncy at the interface                                                                                                                                                                                                                    |       |
| u10, v10, Wind           | 10-m component of wind (u, v, norm)                                                                                                                                                                                                                        | m/s   |
| u10n, v10n, Neutral Wind | 10-m component of neutral wind (u, v, norm)                                                                                                                                                                                                                | m/s   |
| msl                      | Mean Sea Level Pressure                                                                                                                                                                                                                                    | Pa    |
| mwp                      | Mean Wave Period                                                                                                                                                                                                                                           | s     |
| swh                      | Significant height of combined wind waves and swell                                                                                                                                                                                                        | m     |
| mdww                     | Mean direction of wind waves                                                                                                                                                                                                                               | º     |
| mpww                     | Mean period of wind waves                                                                                                                                                                                                                                  | s     |
| shww                     | Significant height of wind waves                                                                                                                                                                                                                           | m     |
| ssr                      | Surface net short-wave (solar) radiation                                                                                                                                                                                                                   | J.m-2 |
| str                      | Surface net long-wave (thermal) radiation                                                                                                                                                                                                                  | J.m-2 |
| sshf                     | Time-integrated surface sensible heat net flux                                                                                                                                                                                                             | J.m-2 |
| tsr                      | Top net short-wave (solar) radiation                                                                                                                                                                                                                       | J.m-2 |
| sst                      | analysed sea surface temperature                                                                                                                                                                                                                           | ºK    |
| sss                      | Unbiased merged Sea Surface Salinity                                                                                                                                                                                                                       |       |
| rho                      | Density derived from SSS and SST using UNESCO formulae                                                                                                                                                                                                     |       |
| SSH                      | Sea Surface Height                                                                                                                                                                                                                                         | m     |
MLD: surface mixed layer depth = min(mld_dreqdtm02, mld_dt02) = depth of theocean surface layer mixed in BOTH temperature and salinity = "optimal" MLD estimation, to be used e.g. for biological studies (for flags details see the flags of the 2 basic mlds) (m)
N2: Brunt Vaisila function
u10, v10, speed: 10-m component of wind (m/s)
u10n, v10n, speedn: 10m component of neutral wind (m/s)
msl: Mean Sea Level Pressure (Pa)
mwp Mean Wave Period (s)
swh: Significant height of combined wind waves and swell (m)
mdww: Mean direction of wind waves (º)
mpww: Mean period of wind waves (s)
shww: Significant height of wind waves (m)
ssr: Surface net short-wave (solar) radiation (J.m-2)
str:   Surface net long-wave (thermal) radiation  (J.m-2)
sshf: Time-integrated surface sensible heat net flux (J.m-2)
tsr: Top net short-wave (solar) radiation (J.m-2)
sst: analysed sea surface temperature (ºK)
sss: Unbiased merged Sea Surface Salinity 
rho: Density computed using SST, SSS and UNESCO formulae
