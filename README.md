# Power Network Disruption Prediction

## Project Overview

This project investigates whether the structure of an electrical power network can help predict which substations will experience an interruption later. The analysis focuses on initially functioning substations and examines whether network information improves prediction beyond basic equipment characteristics.

## Data and Methods

The project uses two synthetic datasets: `power_substations.csv` and `power_links.csv`. The first contains information about substations, including load ratio, equipment age, initial interruption status, and later interruption status. The second describes the physical links between substations.

The analysis was completed in Python using Pandas, NetworkX, Matplotlib, and Scikit-learn.

The workflow included:

1. Exploring the data and examining later interruption outcomes.
2. Building an undirected network of substations and physical links.
3. Calculating two network features:
   - **Degree:** the number of direct connections a substation has.
   - **Local clustering coefficient:** how interconnected a substation's direct neighbours are.
4. Visualising the network and comparing the distributions of network features.
5. Comparing two logistic regression models using the same observations and stratified train/test split.

The original model used `load_ratio` and `equipment_age_years`. The network model added `degree` and `local_clustering`.

## Exploratory Data Analysis

Of the 144 substations, 143 were initially functioning and eligible for prediction. Among these, 39 experienced a later interruption.

The initial exploration compared later interruption outcomes with load ratio and equipment age. The boxplots suggested differences between the two outcome groups, although the distributions overlapped.

<img width="1089" height="300" alt="Later outcomes , Load ratio and Equipment age" src="https://github.com/user-attachments/assets/e18ca485-1809-431e-aabf-86e7bade69fb" />


## Network Visualisation

The physical network contains 144 substations and 344 links. The observed degree values range from 2 to 8.

The network visualisation distinguishes the initially interrupted substation from the others. The accompanying scatter plot compares degree with the local clustering coefficient.

A high local clustering coefficient means that a substation's neighbours are well connected to one another. Degree and local clustering describe different aspects of network structure: the number of direct connections and the interconnectedness of those neighbours.

<img width="1089" height="440" alt="Physical links and Local network features" src="https://github.com/user-attachments/assets/ca1b9753-0e36-4901-9206-e80b31dba354" />


## Model Comparison and Results

The two logistic regression models were evaluated on the same test set using accuracy, F1 score, ROC AUC, and confusion matrices.

| Metric | Original Model | Network Model |
|---|---:|---:|
| Accuracy | 0.767 | 0.860 |
| F1 Score | 0.444 | 0.750 |
| ROC AUC | 0.828 | 0.949 |

The network model identified 9 of the 12 substations that experienced later interruptions, compared with 4 identified by the original model. However, the number of false positives increased from 2 to 3.

<img width="678" height="320" alt="Original features and with network" src="https://github.com/user-attachments/assets/5f522cf3-79d6-4c3f-a99a-65e7f5d9b5c2" />


## Conclusion and Ethical Considerations

In this experiment, adding network features improved all three evaluation metrics on the test set. The higher F1 score and ROC AUC suggest that the additional information helped the model distinguish between substations that did and did not experience later interruptions.

However, the dataset is synthetic and the evaluation uses a single train/test split. Further validation on realistic, independent data would be necessary before applying the model to an actual power network.

False alarms could lead to unnecessary inspections and inefficient use of resources, while missed interruptions could leave communities without electricity. Engineers and relevant authorities should review predictions before prioritising inspections or repairs. Predictions should support, rather than replace, expert judgement.

## Reflection and Future Improvements

The project demonstrates how network structure can provide useful information beyond individual equipment characteristics. An important limitation is that better performance on one test set does not guarantee the same results in real-world conditions.

Future work could evaluate the models using additional train/test splits or cross-validation, test them on real power-network data, and investigate how prediction thresholds affect false alarms and missed interruptions.


