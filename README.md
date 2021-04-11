# Eluvio_Challenge
### Data propocessing
In this CSV file, there are 8 columns: ['time_create','date_create'，'up_votes', 'down_votes','title', over_18,'author','category']
After went through the whole dataset, I decided to create predictive model between title and up_votes. I removed few of columns since I don't see much relationship between each other. for example, all the down_votes is 0, all the category is worldnews, time and date are not related with either title or up_votes. In my predictive model, I wish I can predict if there is up_votes base on title. 


I used nltk stopwords to remove words with 2 or less character, such as is, a, an, etc., then I add the results to a new column 'clean'. Then join the words into a string and add it to new column 'clean_joined'. I also used nltk countVectorizer to convert text to a matrix of toekn counts. I convert every none zero value in up_votes to 1, and add it to the 'new' column.

### Split data for train and test
I split data into train and test, by 8/2 ratio.

### Logistic Regression
In logistic regression, I also use k-fold cross-validation to avoid overfitting since we have too much dataset in this file. But after compare with RMSE before and after K-fold. I notice that the RMSEs are similar. since the RMSE is 0.4417 for train set and 0.441 for test set. They are both between 0.2 to 0.5, it means that the model can r elatively predict the data accurately. And accuracy for logistic regression is 0.805.

![image](https://user-images.githubusercontent.com/60521234/114318929-04385400-9ac4-11eb-8b61-9405bc6ed956.png)



### Multinomail NB
In Multinomail NB, I also use k-fold cross-validation to avoid overfitting as well. and RMSEs are very similar too. The RMSE is 0.4417 for train set and 0.441 for test set. and accuracy is 0.8057.

![image](https://user-images.githubusercontent.com/60521234/114318283-56c44100-9ac1-11eb-8ff1-132cf9b68442.png)

### Random Forest
in Random Forest, I set n_estimators = 10, max_features = 1, and min-impurity_split = 0.01. Since RMSE is similar after cross validation in the first models, so I decide not to create another cross validation for random forest. So the accuracy is 0.8045. 

![image](https://user-images.githubusercontent.com/60521234/114318516-2c26b800-9ac2-11eb-8761-02f6e19abfce.png)

### RNN - LSTM model
In the RNN model, I create a LSTM (Short-Term Memory network). There are embeeding layer, bidirectional layer, and other two hidden layers. After fit the model, I got the accuracy 0.8057.

I also create a report summary:

![image](https://user-images.githubusercontent.com/60521234/114318681-09e16a00-9ac3-11eb-8fc4-ab9141c8bab7.png)
The only concern I have is I noticed the data is unbalanced. The '1' is about 310000 and '0' is about 75000 in 'new' column. and I should use up or down sample minority class technique before split the train and test set.
