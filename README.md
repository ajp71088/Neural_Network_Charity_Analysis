# Neural_Network_Charity_Analysis

### Overview of the analysis
The purpose of this analysis was to help create a binary classifier that is capable of predicting whether applicants to a charity foundation will be successful in their projects if the foundation, Alphabet Soup, were to fund them. Doing so would allow the foundation to be more precise in their donations and see fewer instances of donated funds not amounting to a successful project by their recipients.

To accomplish this, a CSV dataset with more than 34,000 organizations that have received funding from the foundation was provided. A model is then built utilizing the features (columns) in this dataset and tested to see how accurate it is in predicting the outcome (if the organization was successful with the project for which the funds were donated). Then changes are made to the model to attempt to optimize it to an accuracy rating of 75% or better.

#### Results

##### Data Preprocessing
- The variable used as the target for the model is the IS_SUCCESSFUL column.
![image](https://user-images.githubusercontent.com/107162310/196731062-5aa2fda0-f102-49a6-a51d-44c8d12d7878.png)
- The variables used as the features for the model went through multiple iterations during my attempts at optimization. The dataset includes the following features:
  - EIN, NAME, APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT, IS_SUCCESSFUL
- EIN & NAME were dropped during Deliverables 1 & 2 due to being non-beneficial ID columns

##### Compiling, Training, and Evaluating the Model
For Deliverable 3 (the optimization process), my first attempt at optimization led me to drop the SPECIAL_CONSIDERATIONS & STATUS columns, due to their being just two categories in each column and with how often one category appeared versus the limited appearance of the other:
![image](https://user-images.githubusercontent.com/107162310/196734087-bc506fcb-d0dc-46a6-b56b-83624e6382ba.png)

I then binned the ASK_AMT columns values to further improve the first attempt at optimization:
![image](https://user-images.githubusercontent.com/107162310/196782450-8a108262-1118-4e81-a285-343d6e3db6ea.png)

- Here's how I defined the model for the first attempt:
![image](https://user-images.githubusercontent.com/107162310/196839307-001aa1d9-3fa6-4277-bf19-74ae205f8235.png)

- This first optimization attempt resulted in worse accuracy than before "optimizing":
![image](https://user-images.githubusercontent.com/107162310/196837423-430032f9-ee14-4215-8041-81023a33506e.png)

For my second attempt at optimization, I chose not to drop the additional two columns that I did the first time (SPECIAL_CONSIDERATIONS & STATUS) and I increased the layers and neurons of the model.

- The second attempt was defined this way:
![image](https://user-images.githubusercontent.com/107162310/196839393-2b0a0ec6-44af-44c2-80a7-80a5b7705312.png)

- The second optimization attempt resulted in slightly worse accuracy than the first attempt:
![image](https://user-images.githubusercontent.com/107162310/196839480-8582a43a-e3ca-470e-9996-e7d0ba0bb327.png)

So for the third attempt, I decided to combine the two approaches into one. I cut out the SPECIAL_CONSIDERATIONS & STATUS columns again, and used the same increased number of layers and neurons.

- The third attempt was defined this way:
![image](https://user-images.githubusercontent.com/107162310/196839696-bf8a775e-9ed4-4830-a1e5-e312d857ebf6.png)

- This time, the accuracy on the third optimization attempt jumped although it failed to hit the original metric prior to my optimization attempts:
![image](https://user-images.githubusercontent.com/107162310/196839786-4c9a99c9-7930-4681-84ff-26c55a36423a.png)

Unfortunately, I was unable to achieve the target performance of 75%+ accuracy. 

#### Summary
My three attempts at optimizing this deep learning model led to just 68% accuracy. Further attempts could try reducing the epochs of the model, in the event that it's overfitting to the data. Failing that, adjusting the activation functions or moving to a Random Forest Classifier may be warranted.
