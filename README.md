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

 ### Handling the missing data

```python
# Handling missing data

df['ph'] = df['ph'].fillna(df['ph'].mean())
df['Sulfate'] = df['Sulfate'].fillna(df['Sulfate'].mean())
df['Trihalomethanes'] = df['Trihalomethanes'].fillna(df['Trihalomethanes'].mean())

```

### Data Splitting
- The dataset was divided into training (80%) and testing (20%) sets.

```python
    
    from sklearn.model_selection import train_test_split
    
    # Features (X) and target variable (y)
    X = df_scaled[columns_to_scale]
    y = df['Potability']
    
    # Split the dataset into 80% training and 20% testing
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
    
    # Output the shapes of the training and testing sets
    print(f"X_train shape: {X_train.shape}")
    print(f"X_test shape: {X_test.shape}")
    print(f"y_train shape: {y_train.shape}")
    print(f"y_test shape: {y_test.shape}")
  
```

### Model Architecture
- A neural network was constructed using Keras.
- Three variations of the model were created:
  1. Vanilla Model with no regularization

```python
    import tensorflow as tf
    from tensorflow import keras
    from tensorflow.keras.models import Sequential
    from tensorflow.keras.layers import Dense, Dropout, Activation
    from tensorflow.keras.optimizers import Adam
    
    model = Sequential()
    model.add(Dense(64, activation='relu', input_shape=(X_train.shape[1],)))
    model.add(Dense(32, activation='relu'))
    model.add(Dense(16, activation='relu'))
    model.add(Dense(8, activation='relu'))
    model.add(Dense(1, activation='sigmoid'))
```

![Screenshot from 2024-10-07 11-53-39](https://github.com/user-attachments/assets/92a8ee38-3b17-491d-b51f-ae5918186277)

  2. L1 Regularization Model and Adam
     
![Screenshot from 2024-10-07 11-57-24](https://github.com/user-attachments/assets/eaa930c8-292f-4250-bfdd-bdadcd9a4ede)

  4. Plain Model with RMSprop

![Screenshot from 2024-10-07 11-54-26](https://github.com/user-attachments/assets/a6c4f8e3-51e3-4d89-8429-b01a4652b811)

  5. L2 Regularization Model with Dropout
     
![Screenshot from 2024-10-07 11-58-01](https://github.com/user-attachments/assets/92987c8b-09b3-4cc1-8220-2400f282e038)

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
- **Vanilla Model**: 64.4%
- **L1 Regularization Model**: 62.8%
- **Dropout Model**: 67.0%
- **RMSprop Model**: 69.5%
- **L1 Regularization with RMSprop**: 62.8%
- **L2 Regularization with Dropout**: 62.8%

The Dropout Model achieved the highest accuracy, closely followed by the RMSprop Model, suggesting that both dropout layers and the RMSprop optimizer help improve model performance significantly.

## Loss Comparison
- **Vanilla Model**: 5.57
- **L1 Regularization Model**: 0.6611
- **Dropout Model**: 0.5959
- **RMSprop Model**: 0.596
- **L1 Regularization with RMSprop**: 0.6723
- **L2 Regularization with Dropout**: 0.6610

The Dropout Model had the lowest loss, indicating effective learning and generalization. The Vanilla Model's high loss reflects poor performance and potential overfitting.

## Conclusion
The **RMSprop Model** emerged as the best performer, achieving the highest accuracy (69.5%) and lowest loss (0.596). The addition of dropout layers helped reduce overfitting, allowing the model to generalize the data better. The RMSprop optimizer also contributed positively to performance. In contrast, the Vanilla Model struggled due to overfitting, while models with regularization did not outperform other models. 
