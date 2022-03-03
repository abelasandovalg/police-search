# Texas State Patrol: Traffic Stop Analysis/Search Classification

## Project Motivation 
One of the most common ways that the public interacts with the police is through traffic stops which can lead to racial profiling, a discriminatory practice that often targets individuals based on race, ethnicity, religion, or national origin. To combat racial profiling in Texas, the state passed a law that requires each police agency to file an annual online racial profiling report as well as a comparative analysis to a governing body. However, these analyses have not been produced at all. Therefore, the motivation for this project was to analyze the data and pull insights from it as well as create a model that predicts whether or not someone will be searched based on traffic stop data. 

## Code
**Languages**: Python <br>
**Packages**: pickle, numpy, pandas, sklearn, matplotlib, imblearn

## Data 
The analysis contains Texas State Patrol data obtained from [The Standford Open Policing Project (OPP)](https://openpolicing.stanford.edu/). The dataset contains over 27 million data points. More information on the dataset can be found [here](https://github.com/stanford-policylab/opp/blob/master/data_readme.md).

### Data Cleaning 
Data cleaning for the datset includes: 
- Removing unnecessary data (e.g., columns of data collected after a search) 
- Removing empty rows of data 
- Recoding time data into time period (e.g., morning, afternoon, evening, night)
- Removing incorrect data (e.g., nonexistent regions)
- Oversampling and undersampling data 
- Collapsing Race/Sex data into one column 

## File Descriptions
`finalized_model.sav`: Final .sav model created using tree-based classifiers <br>
`texas_statewide.csv`: Texas State Patrol statewide data <br>
`tx_state_patrol.ipynb`: Jupyter notebook containing code used to analyze data and create classification algorithm 

## Results 
### Exploratory Data Analysis 
The data analysis revealed insights based on both race and sex data. From solely looking at race data, Black and Hispanic people are 1.90 and 1.39 times more likely to be searched during a traffic stop, respectively: 

**Searches per 100,000 Traffic Stops by Race:**

**Black**:                  3431.6 Searches per 100,000 Traffic Stops <br>
**Hispanic**:               2504.2 Searches per 100,000 Traffic Stops <br>
**Other**:                  1904.0 Searches per 100,000 Traffic Stops <br>
**White**:                  1797.8 Searches per 100,000 Traffic Stops <br>
**Asian/pacific islander**:  956.4 Searches per 100,000 Traffic Stops <br>

Now, when combining both race and sex into a single column, there are a lot more interesting insights: 

**Searches per 100,000 Traffic Stops by Race/Sex:**

**BM**: 4325.5 Searches per 100,000 Traffic Stops <br>
**HM**: 2993.4 Searches per 100,000 Traffic Stops <br>
**WM**: 2135.0 Searches per 100,000 Traffic Stops <br>
**OM**: 2033.3 Searches per 100,000 Traffic Stops <br>
**BW**: 1655.5 Searches per 100,000 Traffic Stops <br>
**OW**: 1590.8 Searches per 100,000 Traffic Stops <br>
**HW**: 1235.6 Searches per 100,000 Traffic Stops <br>
**WW**: 1128.4 Searches per 100,000 Traffic Stops <br>
**AM**: 1126.8 Searches per 100,000 Traffic Stops <br>
**AW**:  510.2 Searches per 100,000 Traffic Stops <br>

One of the most notable insights from the data is that Black men are searched at least twice as much as any other demographic, followed by Hispanic men. Additionally, most men are searched more often than women are with the exception of Asian men, who are searched less often than white women. 

### Model Building
To successfully build the model, the data was both oversampled and undersampled in order to achieve class balance and yet not lose as much data. Additionally, the data was one-hot encoded to deal with categorical variables.

The three models used to train on the data were all three-based ensemble models including, **Decision Tree Classifier**, **Random Forest**, and **AdaBoost**. These models are robust against overfitting, outliers, noise, and are computationally relatively inexpensive, which works well with the dataset. 

### Model Performance
All of the models performed about the same, however, the Decision Tree Classifier was chosen for the final model since it was the quickest. 

**Decision Tree Classifier**: Accuracy = 0.71 <br>
**Random Forest**: Accuracy = 0.71 <br>
**AdaBoost**: Accuracy = 0.70 <br>

### Confusion Matrix
![Confusion Matrix](https://github.com/abelasandovalg/police-search/blob/main/images/confusion_matrix.png)

## Future Improvements 
1. Using Texas Commision on Law Enforcement Regions (TCOLE) to classify counties with missing or incorrect region information. 
