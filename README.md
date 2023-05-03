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
conda create -n challenge **#You can put the name you want for your environment**
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


## Testing