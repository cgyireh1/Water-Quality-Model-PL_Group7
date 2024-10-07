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

### Model Evaluation
- Models were evaluated using loss and accuracy metrics on the testing set.
- Confusion matrices and classification reports were generated for insights.

## Outcome of Different Variations of The Implementations


