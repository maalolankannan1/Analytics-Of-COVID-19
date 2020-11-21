# Analytics-Of-COVID-19 with respect to Environmental Conditions
Data analytics based project.

**Done BY:**
1.  Maalolan K  (https://github.com/maalolankannan1)
2.  Nikita Rath (https://github.com/nikita9604)
3.  Yeshwanth R (https://github.com/Yeshwanthr002)

The pandas library of Python was majorly used to help work with the datasets and perform tasks on it. All the stages of Data Analytics Life Cycle are a part of this project.
<p align="center">
  <img src="https://user-images.githubusercontent.com/42891566/99869198-1f76f580-2bef-11eb-8ca6-b6b9c3ed4c4d.png?raw=true" alt="Data Analytics Life Cycle"/>
  <br>
  Fig. 1 The Data Analytics Life Cycle
</p>

**I.	Objective:**

The Objectives were clearly defined. To analyse the spread of COVID-19 disease with respect to environmental conditions of a particular region and check whether using the data of weather conditions of a particular place, we can predict the total number of Confirmed Cases on that particular day.

**II.	Understanding the Data:**

The 2 datasets were loaded into the workspace and the variables of each were observed. The COVID-19 Cases Dataset has 8 variables and 98252 row entries. There are 3 Float types , 1 integer and 4 object type columns. The weather dataset has 45 variables and 30688 row entries. There are 26 Floats ,13 integer and 6 object type columns. Using the to_datetime() function of pandas, the string values for time in the dataset were converted to a Datetime object for easy navigation.

**III.	Data Cleaning and Data Transformation:**

While going through the datasets, a lot of structural errors were observed which might lead to loss of data while merging the datasets. For example, it was observed that the Country/Region for a few provinces was named as China in the weather dataset but for the same provinces it was named as ‘Mainland China’ in the COVID 19 dataset. Similarly for Hong Kong State, the country name was China in the weather dataset whereas it was ‘Hong Kong’ in the COVID 19 dataset. Another Country ‘Macau’ also had the same issue. Thus the other country strings were updated to the name ‘China’ in the COVID 19 Dataset. 
Then the missing data was plotted using ‘missingno’ library of Python. It was observed that the ‘precipAccumulation’ column had around 80% missing values. Considering this variable in the dataset will lead to bad results. Hence this variable was dropped.

**IV.	Data Enhancement:**

All the rows that had an NA value for the State/Province value were removed as in those countries, they have taken an average weather for the whole country and thus those results cannot be relied upon. For example, For the country of India there is only 1 set of weather values per day. But the weather variation within India is very high. This might skew the results a lot and so they have to be removed. The most important variables like Temperature, humidity, pressure, wind speed, precipitation intensity and dewpoint were kept in the front of the merged data frame for better understanding.  

**V.	Data Analytics:**

Observing the plot of total confirmed cases per day vs Days, it was decided to split the dataset into 2 sets - one before March 15 and the other After March 15. March 15 was an elbow point in the graph plotted. The data before and after March 15 were grouped by the Country name and it was observed that for the dataset before March 15, China had a very huge number of Confirmed Cases than the rest. Including the rest hinders our prediction as even with the same environmental conditions there weren't any cases there only because the Virus was concentrated in China mostly till then. Thus we had only China before March 15. For the after March 15 dataset, Netherlands and Denmark were removed on the same grounds.
Correlation matrix was shown for the 2 split datasets and also for the whole dataset. Then different Machine Learning models were used to try and fit the data to it. The following models were performed:
  1.	Linear regression:
    a.	With combination of max correlated features.
    b.	Simple Linear regression with a weather parameter.
    c.	With all the weather parameters.
  2.	XGboost:
    a.	Simple
    b.  Multiple
  3.	SVM
  4.	Decision Tree based
  5.	Considering only China (more number of cases):
    a.	Linear regression
    b.	Xgboost

**VI.	Data Visualization:**

Descriptive Analysis was done with the use of different types of plots. These plots helped us to make decisions on which way to take forward. A plot on Confirmed cases per day vs Days helped us find the elbow point of March 15. After splitting up based on this point the results improved as this reduced a lot of hidden factors that might have skewed the model. Plots between Confirmed cases grouped by only pressure or only precipitation Intensity was not fruitful as the graph showed no trend in this manner. Using the correlation values obtained, pairs of variables that had good correlation with each other and with the Confirmed Cases were taken and plotted. For this plotly.express graphs were used. Each graph had one weather parameter each in the x-axis and y axis, and the intensity of colour of the data circles and their size corresponded to the Confirmed Cases count. All these plots did not follow any specific trend. Very minute trends were observed when graphs were plotted only for a particular month, that too for months till March as till then the virus was concentrated in China alone.     
