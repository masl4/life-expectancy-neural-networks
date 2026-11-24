# Life Expectancy Prediction with Neural Networks

Regression project developed as part of the **Master's in Deep Learning at Universidad Politécnica de Madrid (UPM)**. The goal is to predict life expectancy from health, demographic, and socioeconomic indicators using artificial neural networks and classical machine learning models.

## Project overview

- **Dataset:** [Life Expectancy (WHO) — Kaggle](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who), covering country-level observations from 2000 to 2015.
- **Task:** Regression — predict life expectancy in years.
- **Data preparation:** Exploratory data analysis, missing-value imputation, encoding, and feature scaling.
- **Evaluation strategy:** Train/validation/test split by **country**, so the same country does not appear across splits; preprocessing is fitted on training data only.
- **Models explored:** Linear Regression, Random Forest, and different Multilayer Perceptron (MLP) configurations.
- **Experiments:** Network width and depth, activation functions, loss functions, L2 regularization, Dropout, Batch Normalization, SGD/Adam/RMSprop optimizers, and KerasTuner hyperparameter search.
- **Further analysis:** Residuals, permutation feature importance, performance by country development status, and group-based cross-validation.

## Results

The final neural network was selected using **validation performance**, without using the test set to choose its configuration.

| Model | Validation MAE (years) | Test MAE (years) | Test RMSE (years) | Test R² |
| --- | ---: | ---: | ---: | ---: |
| **Selected MLP** — 64 tanh neurons, Adam, MAE loss | 1.945 | 2.682 | 3.750 | 0.806 |
| **Random Forest** — 100 trees (benchmark) | 1.908 | 2.304 | 2.912 | 0.883 |

**Key finding:** The MLP achieved competitive validation results, although Random Forest performed better on the held-out test set. The results also show why choosing a model based on test performance would be misleading.

### Example prediction

For a previously unseen observation corresponding to **Algeria, 2015**:

- Actual life expectancy: **75.60 years**
- MLP prediction: **75.28 years**
- Absolute error: **0.32 years**

This example illustrates one prediction; overall performance should be assessed using the full test metrics above.

## Tech stack

**Python · TensorFlow/Keras · scikit-learn · KerasTuner · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook**

## Run locally

1. Download the original `Life Expectancy Data.csv` dataset from the [Kaggle dataset page](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who).
2. Place `Life Expectancy Data.csv` in the same folder as the Jupyter notebook.
3. Install dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Open `life_expectancy_neural_networks.ipynb` in Jupyter and run the cells in order. Training all experimental models can take some time.

The notebook includes explanations, results and plots from the experiments. The dataset is **not included** in this repository; download it from the original source.

## Author

**Miguel Ángel Sánchez López**  
Software Engineering Graduate — Universidad Politécnica de Madrid  
Master's in Deep Learning (in progress) — Universidad Politécnica de Madrid
