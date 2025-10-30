
| Data                   | Variable                                  | Reader                       | Coverage | Status                           |
| ---------------------- | ----------------------------------------- | ---------------------------- | -------- | -------------------------------- |
| L3 LR SSH Unsmoothed   | Sigma0 detrended (Roughness)              | To check                     | Samples  | To check if errors with ingestor |
| L3 LR SSH Unsmoothed   | SSHA_unedited hi pass filtered            | To check                     | Samples  | To check if errors with ingestor |
| L3 LR SSH Unsmoothed   | SSHA_unedited (SLA)                       | To check                     | Samples  | To check if errors with ingestor |
| L2 HR PIXC             | Roughness                                 |                              |          | Optional                         |
| L2 HR PIXC             | SSHA                                      |                              |          | Optional                         |
| L3 LR 2km Expert       | ssha_unedited (SLA)                       | OK                           | NRT      | OK                               |
| L3 LR 2km Expert       | SSH (ssha_unedited + MDT)                 | to check                     | NRT      |                                  |
| L3 LR 2km Expert       | ugos_unfiltered, vgos_unfiltered          | check filtered vs unfiltered | NRT      |                                  |
| L2 LR Wind Wave        | swh_karin                                 | OK               | Samples  |                                  |
| L2 LR Wind Wave        | wind_speed_karin                          | OK                | Samples  |                                  |
| L3 LR Wind Wave Expert | Efxfy_SWOT (SWOT)                         | OK                | Samples  |                                  |
| L3 LR Wind Wave Expert | H18, L18, theta18 (Partition as firework) | OK               | Samples  |                                  |
|                        |                                           |                              |          |                                  |
 Test cases:
 Tropical Storm Erin: End of August, early September 2025
 => 25-26-27 aug, add more ? potential fireworks. 
 
 Storm Eddy with very long wavelength: December 2024
21 - 29 decembre

fireworks : syntool converter -> branch sarwave, sarwave_s6_ffsar
SWOT_L3_LR_SSH_Expert_016_510_20240616T091632_20240616T100759_v1.0
SWOT_L3_LR_SSH_Unsmoothed_016_320_20240609T142218_20240609T151303_v2.0.1_p1_336
Data
 [https://www.aviso.altimetry.fr/en/data/products/windwave-products/swot-karin-level-3-wind-wave-product.html](https://www.aviso.altimetry.fr/en/data/products/windwave-products/swot-karin-level-3-wind-wave-product.html)