# DataChallenge2023_Stage_IMT
It contains the codes and the process that was carried out in the practice performed by **Ala Baccar** and **Joaquin Opazo**. The idea of this repository is to show the results as well as the procedure, implementations and codes used. 

## Prerequisite
- git
- conda

## Install / Setup
### Conda Install
For installing conda [here is the guide](https://conda.io/projects/conda/en/stable/user-guide/install/linux.html). 

### Environment
```
https://github.com/Opeiz/DataChallenge2023_Stage_IMT.git
cd DataChallenge2023_Stage_IMT
conda install -c conda-forge mamba
conda create -n challenge # You can put the name you want for your environment
conda activate challenge
mamba env update -f environment.yaml
conda deactivate
conda activate challenge
```

### Download Example Data
```
mkdir data
wget https://s3.eu-central-1.wasabisys.com/sla-data-registry/6d/206c6be2dfe0edf1a53c29029ed239 -O data/natl_gf_w_5nadirs.nc
```

## Training
The following command will be used to train the model
```
python main.py xp=base
```
Important to mention, as hydra is configured, the output of the above command will look like this
```
outputs/YYYY-MM-DD/HH-MM-SS/...
```
There you will find the .ckpt file containing the best values obtained in the training phase.

For simplicity during practice, and for speed in learning and testing the different parameters, the above-mentioned command is a quick version. To train in a more complex way you should add the `bigger_model.yaml` file which will overwrite the parameters in order to obtain an even better result.
```
python main.py xp=base +params=bigger_model
```

## Testing





## Useful links:
- [Hydra documentation](https://hydra.cc/docs/intro/)
- [Pytorch lightning documentation](https://pytorch-lightning.readthedocs.io/en/stable/index.html#get-started)
- 4DVarNet papers:
	- Fablet, R.; Amar, M. M.; Febvre, Q.; Beauchamp, M.; Chapron, B. END-TO-END PHYSICS-INFORMED REPRESENTATION LEARNING FOR SA℡LITE OCEAN REMOTE SENSING DATA: APPLICATIONS TO SA℡LITE ALTIMETRY AND SEA SURFACE CURRENTS. ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences 2021, V-3–2021, 295–302. https://doi.org/10.5194/isprs-annals-v-3-2021-295-2021.
	- Fablet, R.; Chapron, B.; Drumetz, L.; Mmin, E.; Pannekoucke, O.; Rousseau, F. Learning Variational Data Assimilation Models and Solvers. Journal of Advances in Modeling Earth Systems n/a (n/a), e2021MS002572. https://doi.org/10.1029/2021MS002572.
	- Fablet, R.; Beauchamp, M.; Drumetz, L.; Rousseau, F. Joint Interpolation and Representation Learning for Irregularly Sampled Satellite-Derived Geophysical Fields. Frontiers in Applied Mathematics and Statistics 2021, 7. https://doi.org/10.3389/fams.2021.655224.
