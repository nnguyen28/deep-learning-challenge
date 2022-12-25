deep-learning-challenge

Report on the Neural Network Model

Deep Learning Charity Funding Outcome Predictor Project using hyper-tuned Neural Networks.

Overview:

I've created a tool for the nonprofit foundation Alphabet Soup that can help it select applicants for funding with the best chance of success in their ventures. Using my knowledge of machine learning and neural networks, I have used the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup. We were set a target of 75% accuracy for our model. From Alphabet Soup’s business team, I received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

EIN and NAME—Identification columns

APPLICATION_TYPE—Alphabet Soup application type

AFFILIATION—Affiliated sector of industry

CLASSIFICATION—Government organization classification

USE_CASE—Use case for funding

ORGANIZATION—Organization type

STATUS—Active status

INCOME_AMT—Income classification

SPECIAL_CONSIDERATIONS—Special consideration for application

ASK_AMT—Funding amount requested

IS_SUCCESSFUL—Was the money used effectively

Steps Taken:

1: Data Preprocessing

•	Dataset was checked for null and duplicated values 
![image](https://user-images.githubusercontent.com/105611668/209470508-e1068f6e-7070-4f69-a455-af078524268c.png)

•	EIN and NAME—Identification columns removed from the input data because they are neither targets nor features 
![image](https://user-images.githubusercontent.com/105611668/209470586-4b759c71-de59-4085-8d87-0e49011e7665.png)

•	Created cutoff point to bin "rare" categorical variables together in a new value, Other for both CLASSIFICATION and APPLICATION_TYPE  
![image](https://user-images.githubusercontent.com/105611668/209470595-efe38f54-f3c3-4267-9040-ce2a92bd351d.png)
![image](https://user-images.githubusercontent.com/105611668/209470600-d782d5e1-bd13-4ca0-8d16-84b3f2a03001.png)
![image](https://user-images.githubusercontent.com/105611668/209470618-a87581a6-5030-4720-aef6-e9d6c79ec91b.png)
![image](https://user-images.githubusercontent.com/105611668/209470624-3b6b132c-f6c4-4dc2-9d0e-64d5feb9c85a.png)

•	Converted categorical data to numeric with pd.get_dummies, split the preprocessed data into features and target arrays, then lastly split into training and testing datasets 
![image](https://user-images.githubusercontent.com/105611668/209470649-7a02c4da-db82-451a-b8df-571993aaf9e0.png)
![image](https://user-images.githubusercontent.com/105611668/209470653-ec515772-8c26-4e65-b70f-cecafdf47a6f.png)

Target Variable for the model:

•	IS_SUCCESSFUL

Feature Variables for the model:

•	APPLICATION_TYPE

•	AFFILIATION

•	CLASSIFICATION

•	USE_CASE

•	ORGANIZATION

•	STATUS

•	INCOME_AMT

•	SPECIAL_CONSIDERATIONS

•	ASK_AMT





