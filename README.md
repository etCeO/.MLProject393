# Predicting Physical Activity Patterns From Wearable Health Metrics

- This project explored wearable device data with machine learning techniques to classify physical activities from Apple Watch and Fitbit users.
- Among 17 features trained, factors like heart rate, calories burned, step count, and distance traveled were applied in multi-classification models to identify physical activity patterns and distinctions.
- Comparing several baseline models, we tuned the strongest performers with hyperparameters and evaluated further with accuracy metrics, confusion matrices, ROC_AUC scores, and feature importance.

---

## SetUp Instructions

### Tools: 
- Google Colab → main coding platform (also works in VS Code)

The following libraries will be required to run the program: 
- Numpy → numerical operations, arrays
- Pandas → data importing, manipulations, dataframes
- Matplotlib → main graphs, visualizations
- Seaborn → advanced visuals
- Sci-Kit Learn → training datasets, evaluation metrics, model building
- Statsmodels → simple statistical models (linear regression)
- Ipykernel → for processing in VSCode

### Installation:
1. For VS Code Users:

- Install all dependencies in the terminal:
    - pip install numpy pandas matplotlib seaborn scikit-learn statsmodels ipykernel

- Alternatively, you can also use the ‘requirements.txt’ file provided:
    - pip install -r requirements.txt

- Ensure these are also installed for best results before running:
    - Python extension
    - Jupyter extension
    - Python interpreter / kernel

2. For Google Colab Users:

- You can disregard the previous installation steps.
- The libraries we require come automatically embedded in Colab’s virtual coding environment as a hosted service. 
- As such, you can simply run our program with the imports provided, and everything will function sufficiently.

--- 

## Dataset Information

Our dataset is freely accessible via the Kaggle website:
- https://www.kaggle.com/datasets/aleespinosa/apple-watch-and-fitbit-data/data/discussion

### Access Instructions
1. Click the link above to open the Kaggle dataset.
2. Find the file ‘aw_fb_data.csv.’
3. Download and place the data inside your immediate project directory or Colab notebook workspace.

For convenience, we also attached the raw .csv file to the repository.

---

## How To Run The Code

### Option 1: Google Colab (Recommended)
1. Download the interactive python notebook (.ipynb) file.
2. Open the notebook in Colab.
3. Upload the ‘aw_fb_data.csv’ file into your data files on the side panel.
4. Connect to a hosted runtime.
5. Select Run All to execute cells.

### Option 2: VS Code
1. Clone or download the code from the repository.
2. Check if the required libraries are installed (see SetUp Instructions).
3. Move the ‘aw_fb_data.csv’ into the folder / project directory.
4. Open the program in VS Code.
5. Select the appropriate Python kernel.
6. Click Run All to execute the notebook.

---

## Results
For our project, we tested six baseline models to classify physical activity categories and fine tuned the best two after initial metrics reporting.

#### Baseline Model Performance

| Model | Approximate Test Accuracy |
|---|---|
| SVM | ~43% |
| Decision Tree | ~43% |
| Logistic Regression | ~33% |
| LDA | ~32% |
| Naive Bayes | ~29% |
| kNN | ~68% (severe overfit) |

#### Tuned Model Performance

**1. Tuned SVC: ~67% test accuracy**
- Parameters → rbf kernel, C=100, gamma=0.01

**2. Tuned Decision Tree: ~76% test accuracy**
- Parameters → max_depth=25, min_samples_split=2, min_samples_leaf=1

### Key Findings:

1. Running and walking activities were classified most accurately in both baseline and tuning model performances (confusion matrices).
2. Sitting and lying activities were confused across all models likely due to their similar intensity levels, an external factor requiring more investigation in our future work.
3. Decision trees achieved the strongest performances overall, however, heavily overfit with increased complexity in the final model (training metrics reached almost 100% in tables).
4. This case was the same for SVMs / SVCs though they achieved slightly lower testing accuracies than decision trees.
5. kNNs demonstrated strong performances as well, but due to severe overfitting in baselines, we found these models too unstable to carry forward in our problem.
6. As a whole, tuning hyperparameters through grid search for our best models proved beneficial for cross validation and testing metrics, however, resulted in overfitting.
7. Decision trees were identified as the best classification models to use for labeling physical activities in health-related fitness data, though additional improvements could be made to advance stable reliability.

### Feature Importance:

We also compared the top 10 feature importance scores for both SVCs and Decision Trees utilizing visualization in horizontal bar charts.
Despite these models overfitting, consistent patterns were discovered.

**Best Physical Activity Classifiers and Key Health Measures:**
- Heart Rate
- Steps
- Calories
- Distance
- Weight
- Sd_norm_heart

Bringing a combination of body durability, motion indicators, and exercise outcomes, their predicting power could’ve been associated with activity intensity, fitness levels, and subject participation.

### Future Work:
- Potential improvements to be made from this project could include:
- Testing ensemble methods like Random Forests and Gradient Boosting
- Reducing overfitting through feature engineering and dimensionality reduction
- Expanding data size to allow a diverse set of activities besides the casual sit, walk, and run exercises
- Improving separation between sitting and lying classes or excluding one entirely for less overlap
- Applying additional research to our current feature importances to understand their biological influences and effects

Beyond this, applications could be developed from this model into LLM health coaches and personalized workout apps that suggest, report, and predict health effects for different physical activities.

## Contributors
- Ethan E. Lopez
- Greyson Chavez
- Khalid Al Mahmoud
