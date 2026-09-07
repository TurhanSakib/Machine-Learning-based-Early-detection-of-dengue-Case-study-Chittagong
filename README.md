**Machine Learning based Early detection of dengue: Case study Chittagong**

Supervised machine learning models for detecting dengue from clinical, demographic, and NS1 antigen test data, trained on a primary dataset of 308 patients collected from hospitals in Chittagong and Cox's Bazar, Bangladesh.

Status: BSc thesis, Department of Computer Science and Engineering, International Islamic University Chittagong (IIUC). Currently being prepared for submission as a conference paper.

---


## Overview:

Dengue causes an estimated 400 million infections a year worldwide. Bangladesh recorded over 69,000 confirmed cases and 327 deaths between January and August 2023. Early and accurate diagnosis matters because it shapes treatment decisions and can prevent severe complications.

Most published machine learning work on dengue uses publicly available secondary data, and few studies combine a patient's personal information, clinical symptoms, and laboratory test results in a single model. This project addresses both gaps. We collected our own dataset directly from public and private hospitals, and we used all three categories of information together.

We trained and compared eight classifiers. Random Forest performed best, reaching 98.92% accuracy on the test set. The model is demonstrated through a web application built with Streamlit.





## Dataset:

The dataset contains 308 patient records with 20 attributes, covering both dengue-positive and dengue-negative patients. It was collected from public and private hospitals in Chittagong and Cox's Bazar. The attributes fall into three groups:

**Personal information** — age, sex, occupational activity level.

**Clinical symptoms** — headache, muscle pain, bleeding, skin rash, vomiting, diarrhoea, fatigue, rapid breathing, cough, fever.

**Test and treatment values** — systolic blood pressure, diastolic blood pressure, pulse, platelet level, IgG, IgM, NS1.

Preprocessing involved normalising attribute values to a 0–2 scale under clinical guidance, and imputing missing values by the mean. Missing values were present for platelet level (7 records), bleeding (11), and vomiting (13). The data was then split 70:30 into training and test sets, a ratio that gave the best performance in our experiments.


> **Note on data availability.** These are real patient records collected from healthcare institutions. The raw dataset is not included in this repository. Researchers interested in access should contact the authors.


## Methods:

Eight classifiers were trained and evaluated:

Support Vector Machine · Decision Tree · XGBoost · Gaussian Naive Bayes · Random Forest · K-Nearest Neighbours · Logistic Regression · Linear Discriminant Analysis

Evaluation used test accuracy, F1 score, a confusion matrix, and ROC/AUC curves.


## Results:

| Model | Test Accuracy |
|---|---|
| Random Forest | 0.9892 |
| XGBoost | 0.9892 |
| Gaussian Naive Bayes | 0.9892 |
| Linear Discriminant Analysis | 0.9785 |
| Support Vector Machine | 0.9677 |
| Decision Tree | 0.9677 |
| Logistic Regression | 0.9570 |
| K-Nearest Neighbours | 0.8280 |

Random Forest was selected as the final model. On the test set it produced 32 true negatives, 60 true positives, 1 false positive, and 0 false negatives.


### Limitations:

The dataset is small at 308 records, and the test set contains only 93 samples, so the reported accuracy carries a wide confidence interval. NS1 is included as an input feature while also being a direct diagnostic marker for dengue, which likely accounts for a substantial part of the model's performance. Results have not been validated on an external cohort. These points are the focus of ongoing work.


## Repository Structure:

```
paper/       Thesis document and figures
code/        Training scripts and notebooks
app/         Streamlit web application
figures/     Plots and visualisations
```


## Requirements:

Python 3.7 with NumPy, pandas, scikit-learn, Matplotlib, XGBoost, and Streamlit. Development was done in Google Colab.

```bash
pip install -r requirements.txt
```


## Future Work:

Collecting a larger and more varied set of patient records; adding geographical and climate data as predictors; validating the model on an external cohort; and extending the web application with a feedback mechanism and open-source contribution pathway.


## Authors:

**Nazmus Sakib Turhan** (SID: C191107)
**Md. Hasibul Hossain** (SID: C191093)
**Md. Reyad Hossain** (SID: C191083)

Supervised by **Dr. Shahidul Islam Khan**, Associate Professor, Department of Computer Science and Engineering, International Islamic University Chittagong.


## Citation:

```bibtex
@mastersthesis{turhan2024dengue,
  title  = {Dengue Detection Using Machine Learning Algorithms},
  author = {Turhan, Nazmus Sakib and Hossain, Md. Hasibul and Hossain, Md. Reyad},
  school = {International Islamic University Chittagong},
  year   = {2024},
  type   = {BSc thesis}
}
```


## License:

Code in this repository is released under the MIT License. The thesis document and its figures remain © the authors, all rights reserved.
