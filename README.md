# Healthcare-Resource-Optimizer
This notebook utilizes a machine learning algorithm to pinpoint the best US counties to allocate healthcare resources to. These counties are chosen based on the projected improvement in the county's overall health. 



**First, data cleaning is performed.** This is done by: 
1. Standardardizing the data(basing the scale on standard deviations(roughly from 0-10))
2. Filling in missing values in the data with a reasonable estimate(the average value across all counties)


**Next, the prediction algorithm is created.** This is done by:
1. Looping through each metric(we want a prediction algorithm for each metric)
2. Splitting the data into training and test data(70% training, 30% testing)
3. Creating and training the kernel ridge regression using the sklearn package
4. Testing the accuracy of each prediction algorithm using an explained variance score

**Next, the Health Score Algorithm is created.** This is done by averaging the quality of life metrics and the length of life metrics, and summing them up to get one aggregate score. 

**Next, the counties with the largest and least improvement are found** by: 
1. Calculating current(actual) health scores of each county
2. Creating hypothetical counties with an improved metric(by .5)
3. Using the kernel ridge regression to predict new health score metrics using the improved metric.
4. Using the new predicted health score metrics, calculate a improved health score for each county
5. Comparing the improved health score to the actual health score, and find the counties with the largest and least improvement.

**Finally, the possible reasons for why one county is benefitted more than another are found** by: 
1. Averaging the values of each metric for the top 5 counties and bottom 5 counties
2. Comparing the average values of the top 5 and bottom 5 counties
The metrics with the biggest difference in average value are the most probably reasons for why one county is affected more than another.
