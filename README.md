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

2: Compiling, Training, and Evaluating the Model

I build the first model with the following parameters with low computation time in mind:

•	2 hidden layers with 80, 30 neurons split (the input (node) feature was 43, 80 was chosen as the first layer as it is almost double the input feature). With an hidden layer activation function of rely as this our go to for first model.

•	Output node is 1 as it was binary classifier model with only one output: was the funding application successful yes or no. And an output layer activation of sigmoid as the model output is binary classification between 0 and 1.

I then increased the hidden layers to 3 and set the third hidden layer at 30 as the model prediction accuracy was below 75%:
![image](https://user-images.githubusercontent.com/105611668/209470726-2456966f-0b86-4aed-8102-46b1af7894ad.png)

For the second model I decided to use tanh activation and 3 hidden layers with 90, 30, 20 neurons split and a sigmoid activation for output as the output doesn't change.
![image](https://user-images.githubusercontent.com/105611668/209470745-37c683d8-e931-4992-a5e7-12a71da47924.png)

I experimented with increasing nodes and neurons, the accuracy of the first model is over 75%. 

3: Optimize the Model

I decided to use an automated model optimizer to get the most accurate model possible by creating method that creates a keras Sequential model using the keras-tuner library with hyper-parameters options.
![image](https://user-images.githubusercontent.com/105611668/209470782-d12423f7-99ad-4a25-9bf7-d6939c452c7b.png)

Which will automatically tune the hyper-pyrometers until it gets the most accurate model.
![image](https://user-images.githubusercontent.com/105611668/209470795-b60ac75f-3bc6-4937-a8e8-00087ede97e0.png)

The best model from the keras tuner method achieved 73% prediction accuracy using a sigmoid activation function with input node of 46, 6 hidden layers at a 51, 81, 71, 6, 41, 91 neurons split and 100 training epochs.
![image](https://user-images.githubusercontent.com/105611668/209470812-2eba8193-6f9a-491f-842f-a2e3af3e88f6.png)

4. Final Optimization

I kept the Name column for my final Optimized Model as I still hadn't reached the goal of 75% accuracy. Keping the keras-tuner the same apart from lowering the epochs from 100 to 50 for time optimization.
![image](https://user-images.githubusercontent.com/105611668/209470832-24f61dc4-12a7-4a6c-a50b-4f3df63ed32d.png)

Final and best optimized model achieved 80% accuracy , which exceeds the 75% goal and is our best model.
![image](https://user-images.githubusercontent.com/105611668/209470846-0346e479-dae8-497a-8106-d7d1ad06e6b1.png)

All Top 3 Models were around the 80%.

All had a sigmoid activation with different number of input nodes and hidden layers:
![image](https://user-images.githubusercontent.com/105611668/209470878-1ae2c8b0-1c90-4b47-bf96-109bed895c9f.png)

Summary:

The final automatically optimized neural network trained model from the keras tuner method achieved 80% prediction accuracy with a 0.45 loss, using a sigmoid activation function with input node of 76; 5 hidden layers at a 16, 21, 26, 11, 21, neurons split and 50 training epochs. Performing better than the non automized model. Keeping the Name column was crucial in achieving and going beyond the target. This shows the importance of the shape of your datasets before you preprocess it.


