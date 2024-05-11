This code was downloaded from https://www.neuroimaging.at/pages/qsm.php and adapted to run on newer versions of python, nibabel by yanarof

QSM reconstruction using Total Generalized Variation (TGV-QSM)
Kristian Bredies and Christian Langkammer
Version from June 2016
www.neuroimaging.at

## NEW
- It is a python package now which simplifies installation
- Orientation fixed: image data does NOT have to be transversal any longer (thx Daniel!)


## Installation

Linux requirements:
```bash
sudo apt install python3.12-dev build-essential
```

Python requirements:
```bash
pip install nibabel numpy Cython
```

Compile the Cython
```bash
cd src ; python setup.py build_ext --inplace ; cd ..
```


## Command line options

usage:
```bash
tgv_qsm [-h] -p PHASE -m MASK [-o OUTPUT_SUFFIX]
               [--alpha ALPHA ALPHA | --factors FACTORS [FACTORS ...]]
               [-e EROSIONS] [-i ITERATIONS [ITERATIONS ...]]
               [-f FIELDSTRENGTH] [-t ECHOTIME] [-s] [--ignore-orientation]
               [--save-laplacian] [--output-physical] [--no-resampling]
               [--vis] [-v]
```


remarks for options:
	-t TE in seconds
	-f fieldstrength in Tesla
	-s autoscaling for SIEMENS phase data



test data:
```bash
python src/qsm_tgv_main.py -p test_data/epi3d_test_phase.nii.gz -m test_data/epi3d_test_mask.nii.gz -f 2.89 -t 0.027 -o epi3d_test_QSM
```


## bet brain masking
- for high res data (~0.5 mm iso) this does quite a good job:
- bet magni.nii.gz mask -n -m -R -f 0.1 -g 0.0
- (in case something is lost, vary parameter g minimally)


This code was run and tested with the following
```
Ubuntu 24.04 LTS
python-3.12
nibabel==5.2.1
numpy==1.26.4
Cython==3.0.10
```
