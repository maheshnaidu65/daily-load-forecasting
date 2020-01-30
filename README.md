# daily-load-forecasting
This forecasting model predicts daily load based on past load sequences. 
Demand-supply management is a crucial task in the hands of utilities. This is because load-supply miss-match can lead to big problems like power failures and outages. Hence, utilities should be able to predict demand including peak demand as well as the energies coming from various sources like solar, wind and thermal in order to optimize load dispatch. 
This project focuses on the time-series nature of load data of a group of households to make predictions about future load. The original data was procured from ISSDA (Irish Social Science Data Archive) and was collected for the Irish Smart Meter Trials project. URL: http://www.ucd.ie/issda/data/commissionforenergyregulationcer/.

 It consists of hourly consumption readings of 2000 households collected over a period of 536 days which is equivalent to 12864 hours. Thus, we have a dataset of size 12864 X 2000 to begin with. The hourly consumption readings of all 2000 households, for each hour is added to give the total system load for that hour. This is done for all the 12864 hours, resulting in an array of size 12864 consisting of hourly system load data. For this project, I am predicting daily load hence, I have successively added hourly system load values of every 24 hours representing a day. This results in an array of size 536. This array representing 536 days, contains daily net load (system) of the 2000 households (in MW).  The input data set is prepared from this array. Each input data point is a vector of 30 values which are nothing but 30 successive daily net load values (in MW) and the output is the next load in the sequence. The groups of 30 load values are also created in a serial order with the first element of each vector being each successive value of the array representing daily net load. As a result, we obtain an input dataset of length 536-30 = 506 and feature size 30. 
 
 A GRU model is trained on this dataset which learns the relation between the input features and the output. The model is scored and evaluated using a test dataset. The evaluation metric chosen is rms (root mean square). RMS value for the model is 0.74 thus the model is an efficient one. 

 A graph depicting predicted values and actual values has been plotted. It can be observed that the predicted values closely follow the actual values.   

 An important point here is to note how I arrived at feature size of 30. I arrived at this value after training and testing the GRU network with feature sets of different sizes like 15,30,45 and 60. The feature set of size 30 gave the best result. 

    
