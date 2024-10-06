# Water Quality Prediction Model Report

## Group –7 Structure and Task Allocation

- **Kevin Nyiringango**:  Data Handler
- **Caroline Gyireh**: Vanilla Model Implementor
- **Elvis Guy Bakunzi**: L1 Regularization
- **Fidel Chrétien Impano**: L2 Regularization
- **All Members**: Error Analysis

## Summary of the Implementation Process

### Data Loading
- The water quality dataset was loaded using the Pandas library.
- Missing values were handled by filling them with the mean of the respective columns.

### Data Preprocessing
- The dataset was split into feature matrix (X) and target variable (Y).
- Features were scaled using StandardScaler to standardize the input data.

### Data Splitting
- The dataset was divided into training (80%) and testing (20%) sets.

### Model Architecture
- A neural network was constructed using Keras.
- Three variations of the model were created:
  1. Vanilla Model (no regularization)
  2. L1 Regularization Model
  3. L2 Regularization Model

### Regularization Techniques
- L1 and L2 regularization were implemented in their respective models to prevent overfitting.

### Early Stopping
- Early stopping was applied to monitor the model’s performance during training.

### Model Training
- Each model was compiled and trained using the training data. 
- Training and validation accuracy were monitored.

### Model Evaluation
- Models were evaluated using loss and accuracy metrics on the testing set.
- Confusion matrices and classification reports were generated for insights.

## Outcome of Different Variations of The Implementations

### Vanilla Model
- **Loss**: 1.8906
- **Accuracy**: 0.599

**Observations**:
 
The vanilla model demonstrated a moderate performance with a loss of 1.8906 and an accuracy of approximately 59.9%.
Given the loss is relatively high, this model may not be capturing the complexity of the data well, indicating potential **UNDERFITTING**.

### L1 Regularization Model
- **Loss**: 0.6640
- **Accuracy**: 0.6281
- **Confusion Matrix**: 

- **Classification Report**: 


**Observations**:

The L1 regularization model shows improved loss compared to the vanilla model, suggesting that it helps in reducing some overfitting.
However, the accuracy decreased slightly, indicating that while the model is less complex, it may be losing important features of the data.

### L2 Regularization Model
- **Loss**: 0.6301
- **Accuracy**: 0.6662
- **Confusion Matrix**: 

- **Classification Report**: 

- **Observations**:

The L2 regularization model shows the best performance with the lowest loss and the highest accuracy (66.62%),
showing that the L2 regularization effectively reduces overfitting by penalizing large weights while
maintaining a better balance in the model's complexity.
  

## Comparing All The Models
- **Accuracy Comparison**:

***Vanilla Model:*** 63.87%

***L1 Regularization Model:*** 62.81%

***L2 Regularization Model:*** 66.62%

**Observation:**

The L2 regularization model outperformed both the vanilla and L1 models,
indicating that it was the most effective in capturing the underlying patterns in the data.


- **Loss Comparison**:
  
***Vanilla Model:*** 0.7812

***L1 Regularization Model:*** 0.6640

***L2 Regularization Model:*** 0.6301
  
**Observation:** 

The L2 regularization model also achieved the lowest loss, 
suggesting it had the best fit among the three models.


## **Conclusion**:

The L2 Regularization Model performed the best with the lowest loss and highest accuracy 0.6301 and 0.6662 respectively.

**Possible Reasons;**

The L2 regularization's ability to penalize large weights which likely helped the model generalize better to unseen data.

The L1 regularization model, while helping with some overfitting, may have overly simplified the model, leading to a drop in accuracy.

