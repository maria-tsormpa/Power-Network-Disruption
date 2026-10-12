## Power Network Disruption Prediction

## Project Overview

This project investigates whether network structure can help predict later interruptions in electrical power substations.

## Data and Methods

The project uses a synthetic dataset containing substations and their physical connections. Network features were calculated using NetworkX, including degree and local clustering coefficient. Two logistic regression models were compared using the same training and test split.

- **Original model:** Load ratio and equipment age.
- **Network model:** Load ratio, equipment age, degree, and local clustering.

## Results

| Metric | Original Model | Network Model |
|---|---:|---:|
| Accuracy | 0.767 | 0.860 |
| F1 Score | 0.444 | 0.750 |
| ROC AUC | 0.828 | 0.949 |

The model with network features performed better on the test set and identified 9 of the 12 later interruptions, compared with 4 identified by the original model.

## Conclusion and Ethical Considerations

Network features provided useful predictive information in this experiment. However, the dataset is synthetic and the evaluation uses a single train/test split. Further testing is needed before applying the model to real power networks. False alarms and missed interruptions could affect inspection priorities, resources, and communities. Predictions should support expert decisions rather than replace them.

## Files

The completed Jupyter notebook contains the analysis, network visualisations, model comparison, and final interpretation.
