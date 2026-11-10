# HGCal test beam, PS and H2, May-June 2026

Conditions for the relval workflow on run 118713 (era TB2026/v2, 11 LD modules and one tileboard). The input file
already holds `hgcalDigis`, so the unpacker configuration is not needed.

| File | Use | Source (gitlab hgcal-dpg/calibrations, 1055265, unless noted) |
|---|---|---|
| `modulelocator_v2.txt` | module map (`customise_hgcalmapper(modules=...)`) | `TB2026/maps/modulelocator_v2.txt` |
| `WaferCellMapTraces.txt` | Si cell map (`sicells=...`) | `P5/maps/WaferCellMapTraces.txt` |
| `channels_sipmontile_tb.hgcal.txt` | SiPM tileboard cell map (`sipmcells=...`) | `TB2026/maps/channels_sipmontile_tb.hgcal.txt` |
| `level0_calib_params_relay117136.json` | pedestals, CM, MIP scale (`HGCalCalibrationESProducer` `filename`), valid from run 117136 | `/eos/cms/store/group/dpg_hgcal/tb_hgcal/2026/TestBeam/Calibrations/pedestal/Relay117136/level0_calib_params.json` |
| `hgcal_energyloss_trivial.json` | dEdx and thickness SF (`filenameEnergyLoss`) | `P5/calib/hgcal_energyloss_trivial.json` |
| `config_econds_v1.json` | ECON-D configuration (`HGCalConfigurationESProducer` `modjson`, needed by the DQM harvester) | `TB2026/config/config_econds_v1.json` |

The FED configuration is `testbeam/config_feds_v1.json`, identical to `P5/config/config_feds_v1.json`.
