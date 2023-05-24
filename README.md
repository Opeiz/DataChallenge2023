# SSH Mapping Data Challenge 2023
It contains the codes and the process that was carried out in the practice performed by **Ala Baccar** and **Joaquin Opazo**. The idea of this repository is to show the results as well as the procedure, implementations and codes used. 

This repository contains codes and sample notebooks for downloading and processing the SSH mapping data challenge.

The starter version can be found [here](https://github.com/CIA-Oceanix/4dvarnet-starter)

## Motivation
The goal is to investigate the best method for SSH (Sea Surface Height) reconstruction in different situations such as, varying the domain or testing in different periods of the year.
For this purpose, satellite observations were used to train the model and then to compare with the real data. 

### Data sequence

The dates of the totality of the information provided is between 01-07-2009 and 31-07-2010. So it was divided as follows for the models:
 
- Spin-up: 01-07-2009 to 31-07-2009
- Evaluation: 01-08-2009 to 01-10-2009
- Training: 01-01-2010 to 31-07-2010

**Add image**

## Leaderboard by Season
### January-February ("2010-01-01", "2010-02-28")
|Method|domain|mu|lt|lx|
|:----:|:--:|:-:|:--:|:--:|
|4DVarNet|gf|123|123|123|
|Miost|gf|123|123|123|

### April-May ("2010-04-01", "2010-05-31")
|Method|domain|mu|lt|lx|
|:----:|:--:|:-:|:--:|:--:|
|4DVarNet|gf|123|123|123|
|Miost|gf|123|123|123|

### Octobre-Novembre ("2009-10-01", "2009-11-30")
|Method|domain|mu|lt|lx|
|:----:|:--:|:-:|:--:|:--:|
|4DVarNet|gf|123|123|123|
|Miost|gf|123|123|123|

## Leaderboard for the whole year
### Year (""2010-01-01", "2010-07-31"")
|Method|domain|mu|lt|lx|
|:----:|:--:|:-:|:--:|:--:|
|4DVarNet|gf	|123|123|123|
|Miost|gf		|123|123|123|
|4DVarNet|canaries	|123|123|123|
|Miost|canaries		|123|123|123|
|4DVarNet|osmosis	|123|123|123|
|Miost|osmosis		|123|123|123|
|4DVarNet|NATL	|123|123|123|
|Miost|NATL		|123|123|123|
|4DVarNet|eNATL	|123|123|123|
|Miost|eNATL		|123|123|123|