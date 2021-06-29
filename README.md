# svmcausal-data
Replication data for ["Estimating Average Treatment Effects with Support Vector Machines"](https://arxiv.org/abs/2102.11926) by Alexander Tarr and Kosuke Imai.

## Repository Layout
This repository is split into several folders: code, data, figures and results.

- ``code``: This folder contains all scripts needed to be run in order to generate all data to be used in creating figures.
- ``data``: This contains both the simulation data and the right heart catheterization data used in the empirical analysis in the paper.
- ``figures``: All python code for replicating the eight figures in the paper, as well as the resulting PDFs.
- ``results``: Intermediary data created by scripts in the ``code`` folder. Data in this folder is used to create the figures.

## Installation
Recreating all figures and data provided in this repository requires working installations of [Python](https://www.python.org/downloads/), [R](https://cran.r-project.org/src/base/R-4/), and [Gurobi](https://www.gurobi.com/downloads/). All code in this repo was tested under Python version 3.7.1, R version 4.0.5, and Gurobi version 9.1.2 on a Windows 10 machine.

### Gurobi License
The Gurobi Optimizer requires a license to use, which is free for academics. Instructions for acquiring a license can be found [here](https://www.gurobi.com/academia/academic-program-and-licenses/).

### Python Dependencies
All Python code uses the following packages: ``gurobipy, matplotlib, numpy, pandas, scipy, scitkit-learn``.

### R Dependencies
All R code uses the following packages: ``designmatch, ipred, iWeigReg, randomForest, rdist, rpart, sandwich, stats, survey, tidyverse, twang``.

## Execution

### Figures
All figures in the paper can be recreated by executing the Python scripts in the ``figures`` folder using the provided results in the repo. For example, typing the following into terminal or command prompt

    python figures\fig1.py
  
will recreate a PDF for Figure 1.

### Results
The intermediary data computed by our algorithm and those we compare against can be replicated with the scripts provided in the ``code`` folder. There are are four separate scripts:

1. ``validation.py``: This script computes SVM paths for a single dataset taken from Simulation A in the paper. Given the computed path, the script then computes the SVM-QIP solution at each breakpoint in the path. This code can be executed via

       python code\validation.py -k <KERNEL>

    where ``<KERNEL>`` specifies the kernel type. Choices are ``linear``, ``poly``, and ``rbf``. The results generated by this script are used in creating Figure 1 and Figure 2.
    
2. ``simulations.py``: This script computes SVM paths and the Kernel Optimal Matching (KOM) solution for Simulation A and Simulation B. This script also creates the simulation data found in the ``data\simulations`` folder. The syntax for executing this code is
    
       python code\validation.py -k <KERNEL> -s <SIMULATION>
    
    where ``<KERNEL>`` specifies the kernel type, with choices ``linear``, ``poly``, and ``rbf``, and ``<SIMULATION>`` specifies the simulation, with choices ``G`` (Simulation A) and ``cw`` (Simulation B).
