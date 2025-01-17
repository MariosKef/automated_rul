# Automated Machine Learning for Remaining Useful Life Estimation of Aircraft Engines

![MIT License](https://img.shields.io/github/license/MariosKef/automated_rul?style=plastic) 
[![Python 3.6.9](https://img.shields.io/badge/python-3.6.9-green.svg?style=plastic)](https://www.python.org/downloads/release/python-369/)

## Introduction

This repository holds the source code used for the work on the paper *Automated Machine Learning for Remaining Useful Life Estimation of Aircraft Engines*
(currently under review).

The work focuses on the difficulty of the estimation of the remaining useful life (RUL), emphasizes on the importance of careful pre-processing of the raw data
and recommends the usage of AutoML (in this case *TPOT*) to perform the estimation task, by suggesting optimal pipelines. The proposed methodology is validated on the widely used CMAPSS dataset.

This repository is the work of Marios Kefalas, PhD candidate at the Leiden Institute of Advanced Computer Science (LIACS), Leiden University, Leiden, The Netherlands.

## Installation
To install the pipeline you can do the following:
* Clone the repository 

```git clone https://github.com/MariosKef/automated-rul.git ~/auto_rul```

* cd to the directory of the cloned repository

``` cd ~/auto_rul```

* Create the environment and install the requirements 

With conda:

``` conda create --name auto_rul --file requirements.txt ```

to activate it:

```conda activate auto_rul```

With pip:

``` python3 -m venv auto_rul``` or ```virtualenv auto_rul```

to activate it:

```source auto_rul/bin/activate``` (Linux/Unix)

```source auto_rul/Scripts/activate``` (Windows)

to install the requirements:

```python3 -m pip install -r requirements.txt```

## Usage
To run the pipelines you can do the following:
* For the proposed methodology run the *rul_pipeline.py* as

``` python3 rul_pipeline.py a```, where a is an integer that can be used to track experiments and is used as to set the random seed for reproducibility.

* For the baseline run the *rul_baseline.py* as 

``` python3 rul_baseline.py a ```, where a is an integer that can be used to track experiments and is used as to set the random seed for reproducibility.

**Note:** To reproduce the work in the paper use the following seeds (which are passed into *TPOT*):
* For the proposed methodology: 2016, 2013, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025 (e.g., ```python3 rul_pipeline.py 2016```)
* For the baseline: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
* The current source code uses ```n_jobs=multiprocessing.cpu_count()```. If needed, please modify this at [rul_pipeline.py](https://github.com/MariosKef/automated-rul/blob/d0408445483af7ad1d1be176ee1379b53d4265b3/rul_pipeline.py#L219) and [rul_baseline.py](https://github.com/MariosKef/automated-rul/blob/d0408445483af7ad1d1be176ee1379b53d4265b3/rul_baseline.py#L155).

**Update:** For the proposed methodology, the random seeds **do not** return the same results as in the paper. The reason has not been found yet.
Some possible reasons include:
  * A different source of stochasticity in the source code of the proposed methodology (apart from *TPOT*), which has not been identified yet.
  * An internal mechanism of *TPOT* which might alter the final pipelines, despite the same seed, due to the submitted dataset.
  
The seeds on the baseline, return the same results as in the paper.

## Acknowledgements 
This work is part of the research programme Smart Industry SI2016 with project name CIMPLO and project number 15465, which is partly financed by the Netherlands Organisation for Scientific Research (NWO).

## Citation
If this was useful for your work, we would appreciate a citation of our [ICPHM-IEEE paper](https://ieeexplore.ieee.org/document/9486549).

```
@INPROCEEDINGS{9486549,
  author={Kefalas, Marios and Baratchi, Mitra and Apostolidis, Asteris and van den Herik, Dirk and Bäck, Thomas},
  booktitle={2021 IEEE International Conference on Prognostics and Health Management (ICPHM)}, 
  title={Automated Machine Learning for Remaining Useful Life Estimation of Aircraft Engines}, 
  year={2021},
  volume={},
  number={},
  pages={1-9},
  doi={10.1109/ICPHM51084.2021.9486549}}
  ```
