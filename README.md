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
git clone https://github.com/Opeiz/DataChallenge2023_Stage_IMT.git
cd DataChallenge2023_Stage_IMT
conda install -c conda-forge mamba
conda create -n challenge           # You can put the name you want for your environment
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
outputs/YYYY-MM-DD/HH-MM-SS/base/...
```
There you will find the .ckpt file containing the best values obtained in the training phase.

For simplicity during practice, and for speed in learning and testing the different parameters, the above-mentioned command is a quick version. To train in a more complex way you should add the `bigger_model.yaml` file which will overwrite the parameters in order to obtain an even better result.
```
python main.py xp=base +params=bigger_model
```

## Testing
Now for the testing, the following command will be used
```
python main.py xp=domains_metrics_osse xpd='outputs/YYYY-MM-DD/HH-MM-SS' ckpt='outputs/YYYY-MM-DD/HH-MM-SS/base/checkpoints/val_rmse=...'
```
For the ckpt parameter select the one of all the outputs in the folder.

## Results
The difference with the other git is that this version has the `act.yaml` file, which allows you to change the activation layer through the command line, as follows

```
python main.py xp=base +params=act acti=tanh # Here you choose the new layer
```



### Using Relu
Now to establish a basis for comparison and that we are working in the same way with Ala, we performed in 3 ways in parallel a quick learning of the model using Relu, and the results were as follows

|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
|Bacca |gf    |8.819|1.189|[-65 , -55]   |[33 , 43]    |0.93774|
|**DataChall** |**gf**    |**9.033**|**1.211**|**[-65 , -55]**   |**[33 , 43]**    |**0.93463**|
|Opazo |gf    |9.288|1.194|[-65 , -55]   |[33 , 43]    |0.93668|

### Using LeakyRelu
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
|Bacca| gf	|8.482	|1.218	|[-65 , -55]	|[33 , 43]	|0.93685|
| Opazo    | gf       | 8.902 | 1.201 | [-65 , -55]    | [33 , 43]     | 0.9318 |


### Using Hardswish
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
| DataChall    | gf       | 8.331 | 1.19  | [-65 , -55]    | [33 , 43]     | 0.93705 |

### Using Sigmoid
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
| DataChall    | gf       | 9.59  | 1.201 | [-65 , -55]    | [33 , 43]     | 0.92841 |
|Bacca-Xavier	|gf|	10.729|	1.234|	[-65 , -55]|	[33 , 43]	|0.92744|


### Using Tanh
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
|Bacca-Xavier|	gf|	7.997	|1.192|	[-65 , -55]|	[33 , 43]	|0.93846|

### Using Sin
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
|rec_ssh    | qnatl    | 9.822 | 1.26  | [-76.0 | -1.0] | [28.0 | 63.0] | 0.94288 |
| rec_ssh    | gf       | 9.871 | 1.262 | [-65 | -55]    | [33 | 43]     | 0.94288 |


### Using Cos
|Who|domain|lt   |lx   |LON           |LAT          |mu     |
|:--------|:------:|-----|-----|--------------:|-------------:|-------|
|rec_ssh    | qnatl    | 10.277 | 1.251 | [-76.0 | -1.0] | [28.0 | 63.0] | 0.93905 |
| rec_ssh    | gf       | 10.337 | 1.248 | [-65 | -55]    | [33 | 43]     | 0.93905 |


### Data Visualization
For comparing the 2 methods to the satellite images interpolation, 4DVarNet and Miost, in the folder notebooks are the .csv with the values of the results and the jupyter notebooks with the data science process.


## Useful links:
- [Hydra documentation](https://hydra.cc/docs/intro/)
- [Pytorch lightning documentation](https://pytorch-lightning.readthedocs.io/en/stable/index.html#get-started)
- 4DVarNet papers:
	- Fablet, R.; Amar, M. M.; Febvre, Q.; Beauchamp, M.; Chapron, B. END-TO-END PHYSICS-INFORMED REPRESENTATION LEARNING FOR SA℡LITE OCEAN REMOTE SENSING DATA: APPLICATIONS TO SA℡LITE ALTIMETRY AND SEA SURFACE CURRENTS. ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences 2021, V-3–2021, 295–302. https://doi.org/10.5194/isprs-annals-v-3-2021-295-2021.
	- Fablet, R.; Chapron, B.; Drumetz, L.; Mmin, E.; Pannekoucke, O.; Rousseau, F. Learning Variational Data Assimilation Models and Solvers. Journal of Advances in Modeling Earth Systems n/a (n/a), e2021MS002572. https://doi.org/10.1029/2021MS002572.
	- Fablet, R.; Beauchamp, M.; Drumetz, L.; Rousseau, F. Joint Interpolation and Representation Learning for Irregularly Sampled Satellite-Derived Geophysical Fields. Frontiers in Applied Mathematics and Statistics 2021, 7. https://doi.org/10.3389/fams.2021.655224.
