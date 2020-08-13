# Data-Validation-Methods
This data library was created to help people determine how similar two data sets are. It was designed for a machine learning application but was generalized so that it can be applied to all kinds of quantitative data. The way this program works is an original data set is entered which creates an object that initializes parameters for all the tests (these parameters can be manually changed by the user later). The user can then run all the tests by entering the comparison data. There is a function to do all at once or it can do each test individually for each variable. Below are all the functions in this library and how to use them. 

*This library requires the pandas, os, matplot, and statistics libraries 

__init__(self,Original_set)
	First thing that needs to be done is the initialization function to create the object. The only parameter that needs to be included is the original data. What this function does is it stores the data values of the original data set and also runs tests to create default parameters for all the tests. Each of these parameters will be explained for each test. 

******* Every function will contain a ‘self’ parameter, this means to use dot notation******* 

The next four functions are the main functions that run the comparison tests. If an alert is raised in any of these functions they return true and if not, they return false. 

domain_check(self,Comparison_set,variable)
	This first function simply checks to make sure all the values in the comparison data set are contained within the range of the original data set. When the object is initialized the cutoffs for acceptable values are four standard deviations away from the mean of each variable but this can be manipulated by the user as seen fit. The variable parameter represents the index of what variable you want to run the test one incase there are multiple variables in the array and only one needs to be tested. 

momentum_check(self,Comparison_set,variable)
	This function checks to make the variables in the original data have similar momentums to the corresponding variables in the comparison data. The momentum of a variable is its tendency to move in the same direction whether that is increasing or decreasing. Each time a variable moves in the same direction as it did previously, its score increases. Momentum scores can be anywhere from 0 to 1 where the more closer to 1 the more momentum it has. To use it the user must enter in the comparison data set and then the variable that needs to be tested. 

agreement_check(self,Comparison_set)
	This function checks to see whether all the variables are moving in the same direction. Similar to the momentum check it considers whether a variable increases or decreases but this time compares it to the other variables. This works well for variables that are positively related to each other. The user can choose how many variables most agree for it to be considered a success. Agreement scores can be between 0 and 1 where the closer to 1 it is the more the variables agree. This function only works when there are multiple variables in a data set. 

distribution_check(self,Serve_List,variable)
	This function checks to see whether the variables have similar distributions. It finds the mean and standard deviation of the original data and then creates bins and counts how many variables fall within these bins. It takes the comparison data and counts how many of the data points fall within the bins and the difference between the number of data points in the bins between the original and comparison data points is the distribution score. The distribution score ranges from 0 to 2 where the closer it is to 0 the closer the distributions are. Similar to some of the other functions, the user can choose for which variables to run the test. 

The following functions all allow the user to change the parameters of all the tests.

assign_domain(self,lower,upper,variable)
	This allows the user to assign an upper and lower bound to any variable's acceptable range.

assign_agreement(self,lower,upper,agree)
	This allows the user to assign an upper and lower bound to any variable’s acceptable level of agreement. 

assign_distribution_limit(self,limit,variable)
	This allows the user to assign the limit to how similar any variable’s distribution must be.

assign_distribution(self,dists,variable)
	This allows the user to assign the percentage of variables that should be in each bin of the distribution.

assign_distribution_cutoffs(self,cutoffs,variable)
	This allows the user to assign what the cutoffs for each of the bins in the distribution are.

assign_momentum(self,lower,upper,variable)
	This allows the user to assign an upper and lower bound on what the momentum score of each variable must be. 

assign_variable_name(self,name,variable)
	This allows the user to assign names to each of the variables. The names of all the variables default to variable 1, variable 2, variable 3, etc. 

display_parameters(self)
	This function can be called to display what all the current parameters all for all the tests. 

display_data(self,Comparison_set)
	This function displays graphs for all the data. 

raise_alert(self,Comparison_set)
	This funcion runs all the rests at once with all the current parameters and displays the data when an alert is raised. 
