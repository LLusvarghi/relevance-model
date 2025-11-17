# Relevance Model
This is the official repository of the paper entitled _"Self-Supervised Relevance Modelling in Autonomous Driving via Counterfactual Analysis"_ submitted for presentation to the IEEE IV 2026 conference.\

A relevance model is an AI-based tool able to estimate the relevance of objects for an autonomous vehicle. In this paper, we developed and openly released a relevance model trained on a causal dataset generated through counterfactual analysis on a selected urban T-shaped intersection extracted from CARLA's Town01 map, considering an autonomous vehicle running [Autoware](https://github.com/autowarefoundation/autoware_universe)'s open-source autonomous driving stack.\

The selected intersection is shown in the screenshot below.\
<img width="355" height="300" alt="CARLA Town01 map - selected intersection" src="https://github.com/user-attachments/assets/8139b4a2-b4fa-4718-b018-aa387c1ab7be" />

The __data__ folder contains the causal dataset employed to train the relevance model.\
Objects are simulated through SUMO.
Each entry of the causal dataset is encoded as follows: 
The __net__ folder contains SUMO netfile employed to export
