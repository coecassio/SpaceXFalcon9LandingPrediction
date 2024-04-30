## SpaceX Falcon 9 Landing Prediction
Analysing and Predicting if SpaceX's Falcon 9 Fist Stage Boosters Will Successfuly Land


### Project Overview:

This was developed as the capstone project for the IBM Data Science Course. The goal was to predict if SpaceX Falcon 9 first stage boosters would land successfully, while making use of most topics explored during the course. 
It is divided as follows:
1. Data Collection and Wrangling - data collection using SpaceX API, data collection by webscraping the wikipedia launch list, data wrangling
2. Exploratory Data Analysis (EDA) - EDA using python dataviz packages, basic EDA using sqlite3
3. Interactive Visual Analytics and Dashboard - basic dashboard building with plotly's Dash package, map visualizations with folium
4. Predictive Analysis (Classification) - predictive modeling with sklearn using 4 models (logistic regression, support vector machines, decision tree, k-nearest neighbors)

In the end all 4 models shared the same 83.3% Test Accuracy, likely due to the limited size of the dataset.

### Business Understanding:

The Falcon 9 Boosters are [advertised](https://www.spacex.com/vehicles/falcon-9/) by SpaceX as being the first orbital class rockets capable of reflight, meaning if they can successfully land after a mission their most expensive parts can be reutilized in the future, driving down their cost considerably. While other providers can offer launches for upwards of $ 165M, this technology allows SpaceX to offer Falcon 9 launches for around $ 62M, giving them a massive advantage in bids over their competition. Still, since their lower prices are tied to rocket recovery, missions with high chance of landing failure might drive their prices up and allowing their competitors a bidding chance.

### Data Understanding:

This project collects data from 2 sources, the oficial SpaceX API (api.spacexdata.com/v4) and the Falcon 9 launch list from [wikipedia](https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches), but only the API data is used for EDA and model building. The original dataset is small, with only 90 observations, but it has 18 variables, including the target. After ADE, 5 of those variables were considered irrelevant in determining the success rate of landings and dropped, resulting in 12 features + target.

### Modeling and Evaluation:

A total of 4 models were built to evaluate which would best fit the dataset, using GridSearchCV with 10 fold cross validation to tune their hyperparameters. 
Since the dataset was so small, all 4 models had the same confusion matrix and metrics for the test set, as follows:
|Algorithm|TrainAccuracy|Test Accuracy|
|--|--|--|
|LR|0.846429|0.833333|
|SVM|0.848214|0.833333|
|Tree|0.862500|0.833333|
|KNN|0.848214|0.833333|

### Conclusion:

Since all 4 models had the same results in all metrics for the test set, choosing the best among them seems to be a difficult task. Going by train set accuracy doesn’t seem to be a good option, considering the possibility of overfitting, but if chosen as an alternative, the Decision Tree Classifier had the highest train accuracy, with 86.2% and Logistic Regression had the lowest, with 84.6%.

Given the limited size of available data, getting an accuracy score of 83.3% on all 4 models built seems like a good result, considering the target has a mean value of only 0.67.

While metrics show the models had a total of 0 false negatives, they seem to struggle with false positives, with 50% of failed landings in the test set being predicted as successful. One could argue this is the better scenario since having no false negatives makes failed landing predictions more trustworthy.


