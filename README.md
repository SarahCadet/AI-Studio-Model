# Heartbeat Stress Prediction with 1D CNN

This repository contains the code and resources for a 1D Convolutional Neural Network (1D CNN) model designed to predict stress levels using Photoplethysmogram (PPG) data. This project was developed as part of the AI Studio for Embolden Associates LLC.

---

## Project Overview

The goal of this project is to predict whether a person's stress is caused by physical activity/exercise-induced activity vs. harmful stress, enabling better emotional intelligence decisions. The model leverages PPG data, which measures changes in blood flow using a light sensor.

---

## Dataset

The model was trained and evaluated on the **PPG Heartbeat for Cognitive Fatigue Dataset**. The dataset includes time-series data collected from five gamers during a 22-hour gaming session and contains:

- **Time-series data**: Fatigue labels with PPG red light data.  
- **Diary annotations**:
  - *Sleep-2-Peak* reaction time per hour.
  - Caffeine and food intake logs.
  - Self-assessment using the Stanford Sleepiness Scale (1-7) each hour.

The dataset required extensive cleaning and alignment of the time-series data. Features extracted using the Neurokit2 library include:

- `PPG_Raw`
- `PPG_Clean`
- `PPG_Rate`
- `PPG_Peak`
- `PPG_Quality`

---

## Model Architecture

The 1D CNN model includes the following layers:

1. **Convolutional 1D Layer**:  
   - Detects patterns in time-series data using 32 filters.
2. **Flatten Layer**:  
   - Converts the output of the convolutional layer to a 1D vector for dense layers.
3. **Dense Layer (64 units)**:  
   - Learns complex patterns using the ReLU activation function.
4. **Dropout Layer**:  
   - Prevents overfitting by randomly dropping 2% of the connections.
5. **Output Dense Layer**:  
   - Uses the softmax activation function to output probabilities for each sleepiness level (class).

---

## Time Series Splitting and Windows

- **Data Splitting**: The dataset was split into training and testing sets using a windowing approach.
- **Window Size**: Each window contains 10 data points.
- **Balanced Distribution**: Windows were alternated between training and testing to ensure balanced data distribution.

---

## Model Performance

The 1D CNN achieved an overall accuracy of **97.29%**. Performance observations:

- **High accuracy**: Classes 1, 2, 3, and 7.
- **Moderate accuracy**: Class 5.
- **Low accuracy**: Classes 4 and 6, indicating a need for more data for these classes.

---

## Overfitting and Mitigation

The model initially exhibited overfitting. A **dropout layer** was introduced to improve generalization and reduce the complexity of learned patterns.

---

## Future Work

Possible enhancements include:

1. Collecting additional data for Classes 4 and 6 to improve model accuracy.
2. Further hyperparameter tuning to optimize performance.
3. Combining the 1D CNN with other models, such as LSTM or Logistic Regression, for improved predictions.
4. Launching the model as a mobile app for platforms like the App Store.
5. Integrating the model into wearable devices like Apple Watches and Fitbits.

---

## Acknowledgements

This project was completed as part of the AI Studio portion of the MIT Break Through Tech AI program with guidance from:

- **TA**: Andrii Zahorodnii  
- **Challenge Advisors**: Dr. Sarai Koo and Alfredo Reina Corona  

We are grateful for their support and expertise.

---

For detailed instructions on running the model, please refer to the individual scripts and files.
