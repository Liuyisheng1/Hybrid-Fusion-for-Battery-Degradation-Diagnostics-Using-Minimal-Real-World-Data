# Code README

## Introduction

This repository contains the main code associated with the paper: 

***Hybrid Fusion for Battery Degradation Diagnostics Using Minimal Real-World Data: Bridging Laboratory and Practical Applications***

, which covers parameter space construction, simulated data generation, pre-trained model development, and transfer learning. The public code omits the specific electrochemical model code and retains it in the form of interfaces within the code. It fully demonstrates the model fusion framework based on the battery physics model and data-driven model as presented in the paper.

## Platform and Main Function

The code is implemented in MATLAB, with the main function called `Parameters_identification_and_data_generation.mlx`. The code employs a unified structure form to load raw laboratory aging experiment data into MATLAB for subsequent processing and application, which  includes current, voltage, and cumulative ampere-hour integrals data for each cycle.

## Parameter Identification and Simulated Data Generation

The first two sections of the main function utilize the electrochemical model and the adaptive particle swarm optimization algorithm `ASPO_FUN()` to obtain the reference set of aging parameters on the basis of the experimental data. The obtained parameter combinations are then expanded in the third section and converted into a large amount of simulated data by the interface function entiltled`Model_of_NMC_MSCC_data_generate()`. In this function, we demonstrate the application of the constrained current iterative solution method to convert a large number of battery parameter combinations into simulated data for arbitrary demanded working conditions.

## Data Processing and Model Pretraining

In the fourth section, the `data_generate_func_NMC()` function is used to perform a standard charge segmentation of the simulated data, which is then served as input to the pre-trained model. The model employs a convolutional neural network with residual connections. The specific network parameters and structure can be found in the detailed description in the paper.

## Data Fusion and Transfer Learning

In the final section, a randomly selected subset of the measured MSCC aging experiment data is presented as evidence to support the use of transfer learning. By combining a fixed proportion of simulated and actual data, a transfer learning dataset is created with the objective of fine-tuning the pre-trained model, thereby enabling precise estimation of the state of health (SOH) of the target batteries.
