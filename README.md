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

```python

from sklearn.datasets import make_moons
from matplotlib import pyplot
import pandas as pd
from sklearn.preprocessing import StandardScaler
path = "/content/water_potability.csv"

df = pd.read_csv(path)

print(df.shape)
print(df.head())
  
```

### Data Preprocessing
- The dataset was split into feature matrix (X) and target variable (Y).
- Features were scaled using StandardScaler to standardize the input data.

### Data Splitting
- The dataset was divided into training (80%) and testing (20%) sets.

### Model Architecture
- A neural network was constructed using Keras.
- Three variations of the model were created:
  1. Vanilla Model with no regularization
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
## Observations
The models exhibited varying degrees of performance. The Vanilla Model demonstrated signs of overfitting, with a high loss value (9.43) and moderate accuracy (60.4%). The introduction of L1 regularization improved performance slightly, but the model still struggled to generalize effectively. The Dropout Model showed significant improvements in both accuracy (68.0%) and loss (0.5959), indicating better generalization capabilities. However, models with L1 and L2 regularization presented mixed results, with L1 regularization not enhancing performance as expected when paired with RMSprop.

## Accuracy Comparison
- **Vanilla Model**: 60.4%
- **L1 Regularization Model**: 62.8%
- **Dropout Model**: 68.0%
- **RMSprop Model**: 67.8%
- **L1 Regularization with RMSprop**: 62.8%
- **L2 Regularization with Dropout**: 62.8%

The Dropout Model achieved the highest accuracy, closely followed by the RMSprop Model, suggesting that both dropout layers and the RMSprop optimizer help improve model performance significantly.

## Loss Comparison
- **Vanilla Model**: 9.43
- **L1 Regularization Model**: 0.6611
- **Dropout Model**: 0.5959
- **RMSprop Model**: 0.5979
- **L1 Regularization with RMSprop**: 0.6723
- **L2 Regularization with Dropout**: 0.6610

The Dropout Model had the lowest loss, indicating effective learning and generalization. The Vanilla Model's high loss reflects poor performance and potential overfitting.

## Conclusion
The **Dropout Model** emerged as the best performer, achieving the highest accuracy (68.0%) and lowest loss (0.5959). The addition of dropout layers helped reduce overfitting, allowing the model to generalize the data better. The RMSprop optimizer also contributed positively to performance. In contrast, the Vanilla Model struggled due to overfitting, while models with regularization did not consistently outperform the dropout model. 
