Algorithms

1. One Hot Encoding

The first strategy we considered, for handling categorical variables was One Hot Encoding. A caveate we found was when we deal with the entire dataset 45 million samples, OHE fails because there are 28 million unique features. It becomes computationally intractible because OHE needs one single pass for the entire dataset in order to calculate how many unique features the dataset has. 

2. Features Hashing

Next our team explored another feature engineering method called features hashing, which allows us to avoid expensive computation, but by adjusting the number of features we want to use in our data analysis (features tables). This led us to develop more robust and powerful model because features hashing does not require a single pass for the entire 45 million dataset in order to calculate how many unique features the dataset has. 

3. Decision Tree, Random Forest

Finally we explored tree based methods including Decision Tree and Random Forrest. These algorithms reduce data preprocessing time because they natively handle categorical variables. One caveate here is that Spark's ML package does not accept string values in the input data so a pass over the data was required in order to label encode each categorical string value.

Model Comparison

|	Model	|	LR-FH-ML	|	LR-OHE-ML	|	LR-OHE-MLlib	|	DT-ML	|	RF-ML	|	LR-RDD	|
|	------------------	|	------------------	|	------------------	|	------------------	|	------------------	|	------------------	|	------------------	|
|	Accuracy	|	0.754	|	0.755	|	0.754	|	0.75	|	0.755	|	0.746	|
|	Precision	|	0.129	|	0.629	|	0.582	|	0.538	|	0.629	|		|
|	Recall	|	0.764	|	0.11	|	0.135	|	0.17	|	0.11	|		|
|	F1	|	0.221	|	0.187	|	0.219	|	0.258	|	0.187	|		|

The above table summarizes the results of each model. The models are listed in descending order of efficiency from left to right (most efficient model is on the left, least efficient is on the right). 

Conclusion

Throughout this project we considered, implemented and assessed multiple strategies for tackling click through rate prediction at scale. Additionally, we assessed the relative merits of the various Spark packages, as they relate to this problem, including: RDD's, DataFrames, MLlib and ML. Finally, we considered a variety of strategies to handle the categorical variables and high cardinality inherent in this dataset. Strategies included: Careful feature selection based on EDA (Unique value counts, correlation, Chi Square test), One Hot Encoding of Categorical Variables, Feature Hashing and Tree Based models that handle categorical variables natively. Ultimately, Logistic Regression with feature hashing implemented with the Spark Ml package was both the most efficient and produced the best results. 
