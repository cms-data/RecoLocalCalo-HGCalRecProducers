# HGCal test beam, H2, September 2025

Conditions for the relval workflow on run 112049 (era TB2025/v6, 10 LD modules). The input file already holds
`hgcalDigis`, so the unpacker configuration is not needed.

| File | Use | Source (gitlab hgcal-dpg/calibrations, 1055265) |
|---|---|---|
| `modulelocator_v6.txt` | module map (`customise_hgcalmapper(modules=...)`) | `TB2025/maps/modulelocator_v6.txt` |
| `level0_calib_params_v5.json` | pedestals, CM, MIP scale (`HGCalCalibrationESProducer` `filename`) | `TB2025/calib/level0_calib_params_v5.json` |
| `hgcal_energyloss_setup2_v1.json` | dEdx and thickness SF (`filenameEnergyLoss`) | `TB2025/calib/hgcal_energyloss_setup2_v1.json` |
| `config_econds_v1.json` | ECON-D configuration (`HGCalConfigurationESProducer` `modjson`, needed by the DQM harvester) | `TB2025/config/config_econds_v1.json` |

The Si cell map is the default one in Geometry-HGCalMapping. The FED configuration is `testbeam/config_feds_v1.json`,
identical to `TB2025/config/config_feds_v1.json`.
