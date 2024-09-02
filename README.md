# PM2.5 level prediction

This repository contains the code and steps taken to solve a predictive modeling problem using neural networks for the AirQo Climate Hackathon. The main objective of this project was to predict PM2.5 air quality levels from the provided training and testing datasets.

## Dataset
- **Training Dataset**: Includes various features like id, site_id, city, country, date, and pm2_5 values.
- **Test Dataset**: Contains similar features but excludes the pm2_5 column, which needs to be predicted.

### Dataset Preprocessing
1. **Feature Selection**:
   - Removed unnecessary columns such as `id`, `site_id`, `city`, `country`, and `date` from both the training and test datasets.
   - `pm2_5` column was separated from the training set as the target variable.

2. **Handling Missing Data**:
   - Any missing values in the training and testing data were replaced with the mean value of the respective columns.

### Model Building
Several neural network models were experimented with to predict PM2.5 levels:

1. **Model 1**: 
   - A simple feedforward neural network with two hidden layers of 5 neurons each.
   - Trained for 250 epochs.

2. **Model 2**: 
   - Same architecture as Model 1 but with a learning rate scheduler callback.
   - Experimented with finding the optimal learning rate by visualizing loss versus learning rate.

3. **Model 3**: 
   - Utilized the optimal learning rate found from Model 2 (0.01).
   - Trained for 40 epochs.

4. **Model 4**: 
   - Preprocessed the data by normalizing the features but left the labels (`pm2_5`) unnormalized.
   - Used the same architecture and trained for 250 epochs.

5. **Model 5**: 
   - Normalized both features and labels.
   - Trained for 10 epochs.

6. **Model 6**: 
   - Same as Model 5 but split the training data into training and validation sets for better model evaluation.
   - Trained for 10 epochs and evaluated on the validation set.

### Model Evaluation and Visualization
- After training, the performance of the models was visualized using loss and RMSE metrics.
- Both training and validation losses were plotted to evaluate the performance of the models.

### Predictions and Submission
- The final model (Model 6) was used to make predictions on the test dataset.
- Predictions were normalized during model training and later unnormalized to get the actual PM2.5 values.
- The predictions were rounded to 1 decimal place and prepared for submission in the required format.

### Submission File
- A CSV file named `submission.csv` was created, containing two columns:
  - `id`: The identifier from the test dataset.
  - `pm2_5`: The predicted PM2.5 values.

### Files Included
- **Code**: Python script with the preprocessing, model building, training, and evaluation code.
- **submission.csv**: The final submission file containing predictions.
- **Train.csv** and **Test.csv**: The training and testing datasets used in the project.

### Requirements
- Python 3.x
- Libraries: `tensorflow`, `pandas`, `numpy`, `matplotlib`, `sklearn`

### Future Work
- Further experimentation with deeper architectures or different hyperparameter tuning methods.
- Try other machine learning models or ensemble techniques to enhance prediction accuracy.

---

**Author**: Paul Turyahabwa

Feel free to explore the code and adjust the parameters for further optimization!
