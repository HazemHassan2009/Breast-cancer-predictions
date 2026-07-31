# Project: Breast cancer prediction

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Model Details](#model-details)
- [Results](#results)
- [Bias and Ethics](#bias-and-ethics)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project aims to develop a machine learning model to predict breast cancer based on cytological measurements. It covers data loading, cleaning, feature selection, dimensionality reduction using PCA, clustering with K-Means and DBSCAN for outlier detection, patient similarity recommendations, and finally, neural network model training and evaluation. The goal is to build an accurate model while also addressing important considerations around bias and ethics in healthcare AI.

## Project Structure
The notebook is structured into several tasks:
- **Task 1: Data Loading & Initial Overview**: Loads the dataset and provides initial statistics.
- **Task 2: Data Cleaning and Preprocessing**: Handles missing values, duplicates, and prepares the data for analysis.
- **Task 3: Feature Selection**: Identifies the most impactful features for prediction.
- **Task 4: PCA and K-Means Clustering**: Reduces dimensionality and groups data into clusters.
- **Task 5: DBSCAN Clustering for Outlier Detection**: Identifies outliers in the dataset.
- **Task 6: Find the Most Similar Patients**: Implements a cosine similarity-based patient recommendation system.
- **Task 7: Neural Network Model Training**: Builds and trains a simple neural network for classification.
- **Task 8: Model Evaluation, Bias Check, and Ethics**: Assesses model performance and discusses ethical implications.

## Installation
To run this notebook, you need to have Python and several libraries installed. It is recommended to use a virtual environment.

1.  **Clone the repository (if applicable):**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required libraries:**
    ```bash
    pip install pandas numpy scikit-learn tensorflow matplotlib seaborn
    ```

## Usage
To execute the code and reproduce the results, simply open and run the Jupyter Notebook in a Jupyter environment (e.g., Jupyter Lab, Jupyter Notebook, or Google Colab).

1.  **Open the notebook:**
    ```bash
    jupyter notebook breast_cancer_prediction.ipynb
    ```
    or upload it to Google Colab.

2.  **Run all cells:** Execute each cell sequentially from top to bottom. The notebook will:
    -   Load and preprocess the breast cancer dataset.
    -   Perform feature selection and dimensionality reduction.
    -   Apply clustering techniques (K-Means, DBSCAN).
    -   Train and evaluate a neural network model.
    -   Analyze model performance and discuss ethical considerations.

## Model Details
### Neural Network Architecture
The model uses a simple Sequential Keras model:
-   Input Layer: `Dense` layer with 16 units, `relu` activation, `input_shape` matching the selected features.
-   Hidden Layer: `Dense` layer with 8 units, `relu` activation.
-   Output Layer: `Dense` layer with 1 unit, `sigmoid` activation for binary classification.

### Training Configuration
-   **Optimizer**: Adam
-   **Loss Function**: Binary Crossentropy
-   **Metrics**: Accuracy
-   **Epochs**: 15
-   **Batch Size**: 16

## Results
After training for 15 epochs, the model achieved the following performance on the test set:
-   **Accuracy**: 0.9710

### Classification Report
```
              precision    recall  f1-score   support

      Benign       0.98      0.98      0.98        94
   Malignant       0.95      0.95      0.95        44

    accuracy                           0.97       138
   macro avg       0.97      0.97      0.97       138
weighted avg       0.97      0.97      0.97       138
```

### Confusion Matrix
(Visualized as a heatmap in the notebook)

## Bias and Ethics
Evaluating this breast cancer diagnosis model reveals critical ethical considerations regarding misclassification errors and dataset bias. A technical bias check indicates a disparity in class distributions:
-   Benign cases in test set: 94
-   Malignant cases in test set: 44
-   Imbalance Ratio: 2.14x

If the model trains on skewed historical data, it risks optimizing for the majority class, leading to severe clinical consequences. Not all diagnostic errors are equal. A False Positive error (predicting a tumor is malignant when it is benign) is bad, causing extreme patient anxiety and unnecessary invasive procedures. However, a False Negative error (misclassifying a malignant tumor as benign) is the worst possible outcome. It grants a false sense of security while a life-threatening disease goes untreated, potentially causing irreversible harm or death.

Therefore, deploying AI in healthcare requires rigorous human oversight. The model must strictly serve as a decision-support tool rather than an independent diagnostic authority, ensuring medical professionals continuously audit predictions to safeguard patient welfare.

## Contributing
Feel free to fork the repository, open issues, or submit pull requests. Any contributions are welcome!

## License
This project is licensed under the MIT License - see the `LICENSE` file for details.
