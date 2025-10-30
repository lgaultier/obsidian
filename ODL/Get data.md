# CMEMS
## Satellite
### Geostrophic current
```bash
copernicusmarine get --dataset-id cmems_obs-sl_glo_phy-ssh_nrt_allsat-l4-duacs-0.125deg_P1D --filter "*2025042*"
```
### Total Current

### Altimeter
```bash
copernicusmarine get --dataset-id cmems_obs-sl_glo_phy-ssh_nrt_c2n-l3-duacs_PT1S --filter "*2025042*"
```

```bash
dfilter="20250420*"
list_alti="c2n h2b j2g j3n al alg s3a s3b s6a-lr s6a-hr swon swonc"
for alti in ${list_alti}; do
     copernicusmarine get --dataset-id cmems_obs-sl_glo_phy-ssh_nrt_${alti}-l3-duacs_PT1S --filter $dfilter
done
```
## SST CCI
```bash
for year in {2010..2012} ; do 
for month in 0{1..9} {10..12}; do
for day in 0{1..9} {10..31}; do
wget https://dap.ceda.ac.uk/neodc/eocis/data/global_and_regional/sea_surface_temperature/CDR_v3/Analysis/L4/v3.0.1/${year}/${month}/${day}/${year}${month}${day}120000-ESACCI-L4_GHRSST-SSTdepth-OSTIA-GLOB_CDR3.0-v02.0-fv01.0.nc ;
done ;
done;
done
```
## Model
### GLORYS
```bash
copernicusmarine subset --dataset-id cmems_mod_glo_phy-cur_anfc_0.083deg_PT6H-i --variable uo  --variable vo --minimum-longitude -30 --maximum-longitude 25 --minimum-latitude 30 --maximum-latitude 75 --minimum-depth 0.49402499198913574 --maximum-depth 0.49402499198913574 --start-datetime 2025-04-20T00:00:00 --end-datetime 2025-04-29T00:00:00
```
### ERA5
```python
import cdsapi
# List of days
lday = [f'{x:02d}' for x in range(1, 32)]
#List of time
ltime = [f'{x:02d}:00' for x in range(24)]
smonth = "04"
syear = "2025"
lmonth = [f'{x:02d}' for x in range(1,13)]
for sday in lday:
	dic_h = {'dataset': "reanalysis-era5-pressure-levels",
			 "product_type": ["reanalysis"],
			 "day": [sday,],
			 "year": [syear,],
			 "month": [smonth],
			 "time": ltime,
			}

	dic = dic_h

	dataset = dic["dataset"] #"reanalysis-era5-pressure-levels"                     
	request = {
		"product_type": ["reanalysis"],
		"variable": [ #"specific_humidity",
			"u_component_of_wind",
			"v_component_of_wind"
		],
		"year": dic['year'],
		"month": dic['month'],
		"day": dic["day"],
		"time": dic["time"],
		"pressure_level": ["1000"], #["1", "1000"],
		"data_format": "netcdf",
		"download_format": "unarchived"
	}
	target = f'ERA5_{syear}{smonth}{sday}.nc'
	client = cdsapi.Client()
	client.retrieve(dataset, request, target)
```

## INSITU
### SVP
```bash
copernicusmarine get --dataset-id cmems_obs-ins_glo_phy-cur_nrt_drifter_irr --dataset-part history
```
### ARGO TRAJECTORIES NRT
```bash
copernicusmarine get --dataset-id cmems_obs-ins_glo_phy-cur_nrt_argo_irr --dataset-part history
```
### ARGO PROFILES
```bash
copernicusmarine get --dataset-id cmems_obs-ins_glo_phybgcwav_mynrt_na_irr--dataset-part history
```

### ADCP DT
```bash
copernicus get --dataset-id cmems_obs-ins_glo_phy-cur_my_adcp_irr --dataset-part history
```

### ARGO TRAJECTORIES DT ws corrected
```bash
copernicus get --dataset-id cmems_obs-ins_glo_phy-cur_my_argo_irr --dataset-part history
```

### GLIDER DT
```bash 
copernicus get --dataset-id cmems_obs-ins_glo_phy-cur_my_glider_irr --dataset-part history
```

# OceanColor
## Get listing of data
```bash
curl -fs 'https://ladsweb.modaps.eosdis.nasa.gov/archive/allData/5200/VJ103IMG/2020/282.csv' | grep 'VJ103IMG.A2020282.0048.002.' | cut -d, -f1
```