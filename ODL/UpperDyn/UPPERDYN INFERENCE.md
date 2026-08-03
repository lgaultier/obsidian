# Prepare data on alfheim
## Build input map
```bash
python tools/merge_input.py --out-res 0.25 --start-date 2022-01-01 --end-date 2024-01-02 --workdir /mnt/data_12t/upperdyn
```


# Compute inference (Datarmor DGX)
## Source
```bash
bash
cd /scale/project/lops-siam-oceandatalab/projects/upperdyn_new
conda deactivate
source $HOME/upperdyn-venv/bin/activate
uv venv --python 3.11 ~/upperdyn-venv  
uv pip install --python ~/upperdyn-venv/bin/python
```


## Preprocess
```bash
python prod/code/scripts/precompute_dataset.py --config prod/config/preprocess/pool_assim.toml --input-dir data/mld_split/all --out-dir data/pool/precompute/all --single-file --overwrite
```

```bash
python prod/code/scripts/build_coords.py --config prod/config/preprocess/pool_assim.toml --input-dir data/mld_split/all --out data/pool/coords_all.npz               
```

```bash
python prod/code/scripts/build_neighbor_pool.py --config prod/config/preprocess/pool_assim.toml --precompute data/pool/precompute/all --coords data/pool/coords_all.npz --out data/pool/neighbor_all_aligned.npz
```

```bash
python prod/code/pipeline/data/build_argo_pool.py --precompute data/pool/precompute/all \--coords data/pool/coords_all.npz --config prod/config/preprocess/pool_assim.toml --out data/pool/grid_pool_argo_2021.npz --year 2021
```
——

| Year | Preprocess | Inputs | Cache | Inference assim prod | Inference ongoing | Inference baseline prod | Inference baseline |
| ---- | :--------: | ------ | :---: | :------------------: | ----------------- | ----------------------- | ------------------ |
| 2025 |            |        |       |                      |                   |                         |                    |
| 2024 |            | -      |       |                      |                   |                         |                    |
| 2023 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2022 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2021 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2020 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2019 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2018 |     x      | xD1    |  xx   |        -1>12         |                   | Done                    |                    |
| 2017 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2016 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2015 |     x      | xD1    |  xx   |         Done         |                   | DOne                    |                    |
| 2014 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2013 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2012 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2011 |     x      | xD1    |  xx   |         Done         |                   | Done                    |                    |
| 2010 |     x      | xD1    |       |                      |                   |                         |                    |

 

## Cache
```bash
python prod/code/scripts/build_input_cache.py --input-dir data/maps/output_daily_025  --out-dir data/cachelg/raw/na_2017_cache_h --start 2017-01-01 --end 2018-01-01
```
```bash
python prod/code/scripts/fill_input_cache.py --raw-dir data/cachelg/raw/na_2020_cache_h --out-dir data/cachelg/na_2020_filled_h --start 2020-01-01 --end 2021-01-01
```
## Inference
```bash
nvidia-smi
nvidia-smi --query-gpu=index,memory.used,utilization.gpu --format=csv
```
### Assim
```bash
CUDA_VISIBLE_DEVICES=1 python prod/code/scripts/infer_output_daily_maps_stream.py --config prod/config/profiles/assim.toml --checkpoint prod/train/canonical/assim/assim.pt --input-dir data/maps/output_daily_025 --cache-dir data/cachelg/na_2022_filled_h/ --mem-days 34 --bathy data/bathy/inputs_bathymetry.nc --eddy-data data/assets/dummy_eddy.npz --neighbor-pool data/pool/grid_pool_argo_2022.npz --neighbor-mode symmetric --assim-km 50 --assim-days 10 --sss-source sos --hours 0,3,6,9,12,15,18,21 --batch-size 2048 --overwrite --start-date 2022-11-01 --end-date 2022-12-01 --name-tag assim_025deg_3h --output-dir prod/infer/assim_025deg_3h_20260710
```
### Assim prod
```bash
CUDA_VISIBLE_DEVICES=6 python prod/code/scripts/infer_output_daily_maps_stream.py --config prod/config/profiles/assim_prod.toml --checkpoint prod/train/canonical/assim/assim.pt --input-dir data/maps/output_daily_025 --cache-dir data/cachelg/na_2023_filled_h/ --mem-days 34 --bathy data/bathy/inputs_bathymetry.nc --eddy-data data/assets/dummy_eddy.npz --neighbor-pool data/pool/grid_pool_argo_2023.npz --neighbor-mode symmetric --assim-km 50 --assim-days 10 --sss-source sos --hours 0,3,6,9,12,15,18,21 --batch-size 2048 --overwrite --start-date 2023-02-01 --end-date 2023-03-01 --name-tag assim_prod_025deg_3h --output-dir prod/infer/assim_prod_025deg_3h_20260710
```

### Baseline
```bash
CUDA_VISIBLE_DEVICES=0 python prod/code/scripts/infer_output_daily_maps_stream.py --config prod/config/profiles/baseline.toml --checkpoint prod/train/canonical/baseline/baseline.pt --input-dir data/maps/output_daily_025 --cache-dir data/cachelg/na_2022_filled_h/ --mem-days 34 --bathy data/bathy/inputs_bathymetry.nc --eddy-data data/assets/dummy_eddy.npz -neighbor-pool data/pool/grid_pool_argo_2023.npz --no-neighbors --sss-source sos --hours 0,3,6,9,12,15,18,21 --batch-size 2048 --overwrite --start-date 2023-03-01 --end-date 2023-04-01 --name-tag baseline_025deg_3h --output-dir prod/infer/baseline_025deg_3h_20260710
```

### Baseline prod
```bash
CUDA_VISIBLE_DEVICES=2 python prod/code/scripts/infer_output_daily_maps_stream.py --config prod/config/profiles/baseline_prod.toml --checkpoint prod/train/canonical/baseline/baseline.pt --input-dir data/maps/output_daily_025_v2 --cache-dir data/cachelg/na_2023_filled_h/ --mem-days 34 --bathy data/bathy/inputs_bathymetry.nc --eddy-data data/assets/dummy_eddy.npz --neighbor-pool data/pool/grid_pool_argo_2022.npz  --no-neighbors --sss-source sos --hours 0,3,6,9,12,15,18,21 --batch-size 2048 --overwrite --start-date 2023-03-01 --end-date 2023-04-01 --name-tag baseline_prod_025deg_3h --output-dir prod/infer/baseline_prod_025deg_3h_20260717
```