# Relevance Model
This is the official repository of the paper entitled _"Self-Supervised Relevance Modelling in Autonomous Driving via Counterfactual Analysis"_.

A relevance model is an AI-based tool able to estimate the relevance of objects for an autonomous vehicle. We developed and openly released a relevance model trained on a causal dataset generated through counterfactual analysis on a selected urban T-shaped intersection extracted from CARLA's Town01 map, considering an autonomous vehicle running [Autoware](https://github.com/autowarefoundation/autoware_universe)'s open-source autonomous driving stack.\
The trained relevance model is available as a pickle file: __relevance-model.pkl__

The __data__ folder contains the causal dataset employed to train (and test) the relevance model. For each analysed object, the causal dataset encodes the following information (in the specified order):
- Ego-vehicle's position, heading, speed, and goal destination;
- Object's ground-truth dimensions, class, position, heading, speed, predicted trajectory;
- Object's relevance.

The objects mobility is simulated using SUMO. The __net__ folder contains the SUMO net file representing CARLA's Town01 road network (including the selected intersection).\
Note: currently, the causal dataset includes only one object type (5 m x 2.1 m passenger vehicle).

## Implementation Details
In the causal dataset, the ego-vehicle’s position and goal destination and each object’s position and predicted trajectory are encoded in a polar coordinate system centered on the intersection. The intersection center in SUMO coordinates is (x: 336.7, y: 197.0).\
The angular component is discretized into three categorical values representing the top (0), left (1), and bottom (2) sides of the intersection. Similarly, the ego-vehicle and objects’ heading is discretized into four distinct values representing the 45°-135° (0), 135°-225° (1), 225°-315° (2), and 315°-45° (3) ranges. 

The selected intersection considered in this work is shown in the screenshot below.\
<img width="355" height="300" alt="CARLA Town01 map - selected intersection" src="https://github.com/user-attachments/assets/8139b4a2-b4fa-4718-b018-aa387c1ab7be" />

The relevance model was trained using an 80/20 train-test split. Hyperparameters were optimized via Bayesian search, resulting in a LightGBM configuration with 75 leaves, 0.05 learning rate, maximum tree depth equal to 19, and L2 regularization with λ_2  = 1.7. Training was monitored with Root Mean Square Error (RMSE-)based early stopping over 50 rounds. Model evaluation on the test set yielded excellent results, with mean RMSE = 0.5 m and R2 = 0.79. 

## Contact
For any further details or information please contact Luca Lusvarghi (llusvarghi@umh.es).
