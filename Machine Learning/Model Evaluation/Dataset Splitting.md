## Train-test split

| Data     | %  | Description | Notation |
|:---------|:--:|:------------|:--------:|
| Training | 70 | Data used to tune model parameters $w$ and $b$ in training or fitting | $\begin{gathered}(x^{(1)},y^{(1)})\\\vdots\\(x^{(m_{train})},y^{(m_{train})})\end{gathered}$ |
| Test     | 30 | Data used to test the model after tuning to gauge performance on new data | $\begin{gathered}(x^{(1)}_{test},y^{(1)}_{test})\\\vdots\\(x^{(m_{test})}_{test},y^{(m_{test})}_{test})\end{gathered}$ |

### Selection procedure

1. Fit parameters by minimizing [[Regularization Parameter#Cost function|cost function]]
   - [[Regression]]:
    $J(\vec{w},b)=\frac{1}{2m_{train}}[\sum_{i=1}^{m_{train}}(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})^2+\frac{\lambda}{2m_{train}}\sum_{j=1}^nw_j^2]$
   - [[Classification]]:
    $J(\vec{w},b)=-\frac{1}{m_{train}}\sum_{i=1}^{m_{train}}[y^{(i)}\log(f_{\vec{w},b}(\vec{x}^{(i)}))+(1-y^{(i)})\log(1-f_{\vec{w},b}(\vec{x}^{(i)}))]+\frac{\lambda}{2m_{train}}\sum_{j=1}^nw_j^2$
2. Compute training error
   - [[Regression]]: 
    $J_{train}(\vec{w},b)=\frac{1}{2m_{train}}[\sum_{i=1}^{m_{train}}(f_{\vec{w},b}(\vec{x}^{(i)}_{train})-y^{(i)}_{train})^2]$
   - [[Classification]]:
    $J_{train}(\vec{w},b)=\text{fraction of misclassified train set}$
3. Compute test error
   - [[Regression]]:
    $J_{test}(\vec{w},b)=\frac{1}{2m_{test}}[\sum_{i=1}^{m_{test}}(f_{\vec{w},b}(\vec{x}^{(i)}_{test})-y^{(i)}_{test})^2]$
   - [[Classification]]:
    $J_{test}(\vec{w},b)=\text{fraction of misclassified test set}$
5. Select model with lowest test error $J_{test}(\vec{w}^{<d>},b^{<d>})$
6. Report estimated generalization error with $J_{test}(\vec{w}^{<d>},b^{<d>})$
   - $J_{test}(\vec{w}^{<d>},b^{<d>})$ is likely to be an optimistic estimate of generalization error
   - Because an extra parameter $d$ (degree of polynomial) was chosen using the test set

> Note: no regularization term in error computation

## Train-validation-test split

| Data       | %  | Description | Notation |
|:-----------|:--:|:------------|:--------:|
| Training   | 60 | Data used to tune model parameters $w$ and $b$ in training or fitting | $\begin{gathered}(x^{(1)},y^{(1)})\\\vdots\\(x^{(m_{train})},y^{(m_{train})})\end{gathered}$ |
| Validation | 20 | Data used to tune other model parameters like degree of polynomial, regularization or the architecture of a neural network| $\begin{gathered}(x^{(1)}_{cv},y^{(1)}_{cv})\\\vdots\\(x^{(m_{cv})}_{cv},y^{(m_{cv})}_{cv})\end{gathered}$ |
| Test       | 20 | Data used to test the model after tuning to gauge performance on new data | $\begin{gathered}(x^{(1)}_{test},y^{(1)}_{test})\\\vdots\\(x^{(m_{test})}_{test},y^{(m_{test})}_{test})\end{gathered}$ |

### Selection procedure

1. Fit parameters by minimizing [[Regularization Parameter#Cost function|cost function]]
   - [[Regression]]:
    $J(\vec{w},b)=\frac{1}{2m_{train}}[\sum_{i=1}^{m_{train}}(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})^2+\frac{\lambda}{2m_{train}}\sum_{j=1}^nw_j^2]$
   - [[Classification]]:
    $J(\vec{w},b)=-\frac{1}{m_{train}}\sum_{i=1}^{m_{train}}[y^{(i)}\log(f_{\vec{w},b}(\vec{x}^{(i)}))+(1-y^{(i)})\log(1-f_{\vec{w},b}(\vec{x}^{(i)}))]+\frac{\lambda}{2m_{train}}\sum_{j=1}^nw_j^2$
2. Compute training error
   - [[Regression]]:
    $J_{train}(\vec{w},b)=\frac{1}{2m_{train}}[\sum_{i=1}^{m_{train}}(f_{\vec{w},b}(\vec{x}^{(i)}_{train})-y^{(i)}_{train})^2]$
   - [[Classification]]:
    $J_{train}(\vec{w},b)=\text{fraction of misclassified train set}$
3. Compute validation error
   - [[Regression]]:
    $J_{cv}(\vec{w},b)=\frac{1}{2m_{cv}}[\sum_{i=1}^{m_{cv}}(f_{\vec{w},b}(\vec{x}^{(i)}_{cv})-y^{(i)}_{cv})^2]$
   - [[Classification]]:
    $J_{cv}(\vec{w},b)=\text{fraction of misclassified cross validation set}$
4. Select model with lowest test error $J_{cv}(\vec{w}^{<d>},b^{<d>})$
5. Compute test error
   - [[Regression]]):
    $J_{test}(\vec{w}^{<d>},b^{<d>})=\frac{1}{2m_{test}}[\sum_{i=1}^{m_{test}}(f_{\vec{w},b}(\vec{x}^{(i)}_{test})-y^{(i)}_{test})^2]$
   - [[Classification]]:
    $J_{test}(\vec{w}^{<d>},b^{<d>})=\text{fraction of misclassified test set}$
7. Report estimated generalization error $J_{test}(\vec{w}^{<d>},b^{<d>})$
   - $J_{test}(\vec{w}^{<d>},b^{<d>})$ is a fair estimate of generalization error
   - Because no parameters ($w,b,d$) had been fit using the test set

> Note: no [[Regularization|regularization]] term in error computation

## Data scaling in split sets

- Data in training set, validation set and test set can be [[Feature Scaling|scaled]] to help the model converge faster

### Important note

- When using the [[Z-Score Normalization]], you have to 
  - Use the mean and standard deviation of the **training set** to scale the **validation set** and **test set**
  - This is to ensure that input features are transformed as expected by the model

### Intuition

- Scenario: your training set has an input feature equal to `500` which is scaled down to `0.5` using the z-score
- After training, your model is able to accurately map this scaled input `x=0.5` to the target output `y=300`
- Now let's say that you deployed this model and one of your users fed it a sample equal to `500`
- If you get this input sample's z-score using any other values of the mean and standard deviation, then it might not be scaled to `0.5` and your model will most likely make a wrong prediction (i.e. not equal to `y=300`)

### Code examples

```python
from sklearn.preprocessing import StandardScaler

# Initialize the class
scaler = StandardScaler()
# Compute the mean and standard deviation of the training set then transform it
X_train_scaled = scaler.fit_transform(x_train)
# Scale the validation set and test set using the mean and standard deviation of the training set
# Use transform instead of fit_transform
X_cv_scaled = scaler.transform(x_cv)
X_test_scaled = scaler.transform(x_test)
```
