# Estimating Solubility

## Abstract

A large fraction of pharmaceutical drugs developed never make it passed all clinical trials. With the exorbitant costs of bringing these drugs to market, estimated to be anywhere between hundreds of millions to billions, there is a huge financial drive to increase the success rate of these drug projects. One of the major factors that can cause these drug development projects to fail is how well these drugs dissolve in water. The more soluble they are, the more bioavailable they will be to the body. In this paper, we will explore different modelling methods to predict solubility using machine learning and linear regression. 

## Introduction

Approximately 40% of all drug development projects are terminated due to low aqueous solubility [1]. This has resulting in numerous methods for modelling solubility using the field of cheminformatics. One of the first models developed for solubility, discovered by Jarmo Huuskonen and published in 2000, used 30 electronic and topological attributes in a linear regression model [2].  Another model, published by John Delaney in 2004, narrowed down the model to 4 attributes, molecular weight, number of rotatable bonds, cLogP, and aromatic proportions [3]. Exploration outside of linear models have also been tested. In 2013, researchers utilized deep learning methods to estimate solubility using similar attributes, but results were also within the expected experimental uncertainties [4]. 

It is still not fully understood which chemical attributes of a molecule impact it’s solubility. Many attributes have been found to correlate well with it, such as melting point and cLogP, but these attributes are also difficult to calculate based on molecular structure alone. Experimentation is often required to obtain these values, which requires synthesis of the compounds in question, leading to increased costs. An accurate estimation model would be highly valuable to these drug manufacturing companies since failures would be caught early in the development stage, mitigating the financial risk.

For this paper, we will be utilizing the data provided in the publication “Aqueous Solubility Prediction Based on Weighted Atom Type Counts and Solvent Accessible Surface Areas” [5], which is a collection of several different datasets from Delaney, Huuskonen and the Solubility Challenge. This dataset contains a total of 3664 molecules with their associated Sybyl notation (SLN) as well as their experimental solubility measurement. We will be converting the Sybyl notation into the simplified molecular-input line-entry system, SMILES, using the Python chemistry library, rdkit. 
SMILES codes are strings that describe the molecular structure. Using these SMILES, we can generate attributes that describe the chemicals. The rdkit library has hundreds of different descriptors to choose from that describe the chemicals topography, atomic content, charge, number of bonds, and several more. 

