# HGCal common-mode (CM) DNN correction

Inputs for the CM DNN run by `HGCalRecHitsProducer` (`RecoLocalCalo/HGCalRecAlgos`) to fill
`energy_variations(CM_ALT)` of the HGCal RecHits. See
`RecoLocalCalo/HGCalRecAlgos/README_CMCalibration.md` for details.

| File | Used as |
|---|---|
| `cm_dnn_multimodule_zscore.pth` | TorchScript model (`HGCalRecHitsProducer.model`), z-score normalised inputs/outputs |
| `cm_dnn_multimodule_zscore_manifest.json` | feature order, module vocabulary (`HGCalCMMLParamESProducer.modelManifest`) |
| `cm_dnn_multimodule_zscore_preprocessing.json` | input mean/std and per-channel output mean/std (`HGCalCMMLParamESProducer.inputPreprocessing`) |
| `cellareas.json` | silicon cell area fractions (`HGCalCMMLParamESProducer.cellAreas`), DNN input `cell_area_fraction` |

The model has 254 input features, `Linear(254,256)-ReLU-Linear(256,256)-ReLU-Linear(256,256)-ReLU-Linear(256,32)-ReLU-Linear(32,1)`,
and was trained by A. Reimers on the September 2025 test-beam (runs 112044, 112050, 112060, 112073)
(`allchannels_multimodule_inputzscore_perchannel_F254__256-256-256-32__dr0`), then converted from the
PyTorch `state_dict` checkpoint to TorchScript.

`cellareas.json` is a copy of `HGCalCommissioning/LocalCalibration/data/cellareas.json`.
It is needed because `HGCalDenseIndexInfo::area()` comes from `HGCalGeometry::getArea`, which gives
the full-hexagon area for every connected cell: it does not include the calibration-cell cutout or
the cut/extended edge cells that the SF encodes (57 of 198 connected LD channels differ).
