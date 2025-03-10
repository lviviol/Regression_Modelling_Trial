### Regression Modelling (1st Trial)
* This exercise trial attempts to predict public housing prices using regression model based on historical data.   

### Purpose
* To practice applying data science libraries and making use of suitable models to predict housing prices results.  
* To present insightful information that enable buyers, policy makers and investors towards making informed decisions.


### Data Science
<details> 
  <summary>Libraries</summary>  
Python, Pandas, Matplotlib, Plotly, Scikit-Learn
</details>

### Dataset
<details> 
  <summary>Variables & Source</summary>  
  
* Dataset comprises of variables such as period, town, housing type, storey range, floor area, lease and prices.
* Data sources is Singapore's Open Data Portal
</details>

### Scope
<details> 
  <summary>Period & Predictions</summary>  
  
* Period: Historical housing prices spans between 2017-01 & 2025-02 (YYYY-MM)
* Prediction: Up to 2026-12
* Selected Variables: We begin this data modelling exercise with 1 variable, prices.
</details>

### Methodology & Implementation
<details> 
  <summary>Experimental</summary>  
  
* We examine all data, including outliers.
* We check and exclude missing data to minimize bias in the analysis
* Data is split into training (2017-01 - 2024-10) and testing (2024-11 - 2025-02), i.e. using quarterly data to test the model.
* Random Forest Regression Model is selected since housing price is a time series data.
* The model predicts housing prices.
</details>

### Results & Visualization
  
  1. OOB = 13.2% & R-Square = -0.026
  2. This means the model accurately predicts prices only 13.2% of the time.  This is somewhat an undesirable result.
  3. Negative correlation shows the model is performing worse than a simple mean predictions.  This is undesirable.
  4. Excluding outliers resulted in poorer OOB = 1.6% & R-Square = -0.023, signifying that outlier points plays an unignorable role in the overall resale housing prices.
  5. This is reasonable since there is significantly large variation in housing price within the time series, plus other unstudied variables that have potential effect on resale prices.
  6. At this point, the modelling results shows that time horizon is not the only factor affecting housing prices.

<a href="https://lviviol.github.io/Regression_Modelling_Trial/Regression1stTrial.html" target="_blank">Regression Modelling Chart (Click this link to View Interactive Chart)</a>

<img src="https://github.com/lviviol/Regression_Modelling_Trial/blob/main/RandomForestRegression_Trial1.png?raw=true" width="800">
<img src="https://github.com/lviviol/Regression_Modelling_Trial/blob/main/No_Outlier_Model.png?raw=true" width="800">


### Observations A
1. Random Forest Regression was selected due to it's ability to handle outliers and robust in reducing risk of overfitting.
2. However, this case of lower OOB and poor R-Square suggest there are other factors to consider, especially when housing prices can be influenced by various factors.
3. We attempted to vary the n_estimators from default 100 up to 5000, but the result remains stable, suggesting the n_estimators is appropriate/sufficient for the averaging effects in this dataset.
4. We attempted to vary the ratio between train data & test data by increasing the test data to 6 months and 12 months.  It is observed that OOB becomes worse as the train data decreases and test data increases, which is within expectations due to dynamic housing transactions prices in the later range of the time series.  (This dynamism can be seen with the higher density of the green chart after 2022, which also coincides with post pandemic opening up of the nation where this dataset belongs to.)

### Observations B
1. We went back to basics and investigate into the aggregate data using a line plot and observed that the Max Price values are beyond general concensus of typical housing prices range.
<img src="https://github.com/lviviol/Regression_Modelling_Trial/blob/main/LinePlot.png?raw=true" width="800">

### Observations C
1. To deepen our understanding of the dataset, BoxPlot was deployed and our assumption about extensive outliers in the dataset was valid.
2. We suspect higher freqency of transactions and wider distribution of outlier from 2022 onwards may have affected the effectiveness of the Random Forest Model.
3. However, we also observed that mean value of the Predicted Prices is somewhat close to Actual Median Prices by the BoxPlot.
<img src="https://github.com/lviviol/Regression_Modelling_Trial/blob/main/BoxPlot.png?raw=true" width="800">


### Observations D - Correlation Check
1. Investigating into correlation between Model Predicted vs historical Mean & Median prices shows R-Square>90%.
2. Predicted prices are also closely following historical Mean prices.
3. Above 2 points suggest this Random Forest Regression analysis is somewhat behaving properly since the model takes average of predictions as output in it's calculation.
4. However, forward Predicted Prices, i.e. 2025-03 onwards, repeats the pattern of 2024, which is not as expected.  We expect a flat or rising trend and plan to investigate further.
5. Special Observation: Spike in transactions and rising prices after 2021, signifying investor confidence, is highly likely due to the country's robust management, coherent actions and open response to the pandemic.  Higher disposable income of local residents due to limited spending during pandemic period could be another source of drivers for high demand.  Catalyst effect of low interest rates should not be under estimated too. 
<a href="https://lviviol.github.io/Regression_Modelling_Trial/CorrelationCheck.html" target="_blank">  
Regression Modelling Chart (Click this link to View Interactive Chart)</a>
<img src="https://github.com/lviviol/Regression_Modelling_Trial/blob/main/CorrelationCheck.png?raw=true" width="1200">

 
### Future Improvements
<details> 
  <summary>Ideas & Plan</summary>  

* We plan to check correlation between Boxplot Actual Median Price & Predicted Price.  Our Hypothesis is, if the correlation is positive, perhaps one idea is to select a regression model that models median instead of mean. (Done: See Observation D)
* We plan to compare model output with full dataset and dataset without outliers.  Purpose is to investigate outlier effect on OOB and R Square.  We also note that the disadvantage of removing outlier is it's impact on summary and distribution of the aggregate data, resulting in a biased output.  (Done: See Results & Visualization)
* We plan to include more variables into the modelling.
* We plan to research on other regression models that are more robust at modelling dataset with higher outliers.  (Huber?  Others?)
* We continue to use OOB > 80% and R-Square > 0.8 as guiding criteria for verifying the model's predicted prices.
</details>


### Appendix
<details> 
  <summary>Disclaimer</summary>
This project is currently in early stage of development and analysis.  The predictions and insights generated are preliminary and should not be used for financial, investment and policy decisions.  Contributions and feedback are welcome as this analysis evolves. 
</details>


<details> 
  <summary>Credits & Acknowledgements</summary>

* Model Selection
  1. IBM, https://www.ibm.com/think/topics/random-forest
  2. Berleley, https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf
  3. ZiZheng Li, https://www.researchgate.net/publication/383112591_A_Comparative_Study_of_Regression_Models_for_Housing_Price_Prediction

* Learning Tutorial
  1. Rob Mulla, https://www.youtube.com/watch?v=vV12dGe_Fho
  2. Om Pramod, https://medium.com/@ompramod9921/random-forests-32be04c8bf76
  
* Data Source
  1. Open data portal, https://data.gov.sg

* Meaningful Events
  1. Singapore Opening Up after covid.  https://www.reuters.com/world/asia-pacific/singapore-pm-says-covid-19-new-normal-could-take-up-6-months-2021-10-09/

</details>










