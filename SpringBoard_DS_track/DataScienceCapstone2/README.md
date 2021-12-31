<img src="cardiovascular_data.jpg" width="1500" height=300><br>
# Cardiovascular Disease Prediction
*<p align='left'> Cardiovascular diseases (CVD) is the leading cause of death in the United States and it is estimated that 659,000 Americans die from CVD each year. The cause of CVD is complicated and risk factors that contribute to CVD are still unclear. Thus it is imperative to identify the direct indicators for cardiovascular disease in order to facilitate CVD diagnosis and treatment. In this project, I explored the relationship among a few potential cardiovascular risk factors, then checked on their predictibility against CVD through various machine learning models.</p>*
## 1. Data Source
I utilized Kaggle [Cardiovascular Disease Dataset](https://www.kaggle.com/sulianova/cardiovascular-disease-dataset) which contains 70,000 medical exam records of 11 potential risk factors for CVD and the diagnostic result (1: has CVD, 0: normal). Those 12 variables are Age, Height, Weight, Gender, Systolic/Diastolic blood pressures, Cholesterol levels, Glucose, Smoking, Alcohol intake and Physical activity. </p>
## 2. Data Wrangling
### Part 1. Indentify the hottest topics in the recent CVD research<br>
<b>Method:</b> I utilized the NCBI API to request all the publications between 2020 and 2021 with 'cardiovascular' in the title, scraped in total 64,801 keywords from 17,632 records, obtained frequecy of each unique keywords, grouped similar keywords through fuzzy match and visualized Top 100 most frequeny keywords with word cloud.<br>
<b>Result:</b><br><img src="word_cloud.png" width="400" height=200><br>
Based on the word cloud above, it seems latest cardiovascular researches are focused on COVID (which is obvious but not included in the Kaggle dataset), as well as hypertension, diabetes, atherosclerosis, obseity, which correspond to CVD risk factors Systolic/Diastolic blood pressures, Glucose, Cholesterol, Height/Weight, respectively.<br>
<b>Script:</b> {LINK TO IPYTHON NOTEBOOK}<br>
### Part 2. Exploration on Kaggle [Cardiovascular Disease Dataset](https://www.kaggle.com/sulianova/cardiovascular-disease-dataset)<br>
<b>Method:</b><br>
1. Check missing values, range of each variable and correlations among features and balance of positive (1) and negative (0) labels through pandas-profiling.<br>
2. Filtering out records with features of abnormal values.
3. Feature engineering includes combining body and weight into a new variable BMI and applying catboost encoder to all categorical variables.<br>
<b>Results:</b><br><img src="eda_correlation.png" width="50%" height="50%"><br>
After preprocessing, the trimmed dataset shape is (68588 X 11). As shown in the heatmap above, there are no correlation among features except for a few apparent relationships: 1) Positive correlation between high (ap_hi) and low (ap_lo) blood pressures; 2) Gender bias in those who smoke or drink (likely more men than women); 3) Those who consume alcohol tend to smoke as well (Strong positive correlations);<br>
<b>Script:</b> {LINK TO IPYTHON NOTEBOOK}<br>
## 3. Exploratory Data Analysis (EDA)
<b>Method:</b> I performed PCA and t-SNE to see whether the positive (1) and negative (0) samples can be separated in 2 dimensions. In addition, I checked if any of the features are significantly different between healthy and diseased groups.<br>
<b>Results:</b><br>
<img src="eda_PCA.png" width=300 height=250>  <img src="eda_tSNE.png" width=300 height=250><br>
Both PCA and t-SNE are not able to separate normal (0) and diseased (1) samples in 2D space.
<img src="eda_barplot_ap.png" width=300 height=250>  <img src="eda_barplot_cat.png" width=300 height=250><br>
High and low blood pressure (ap_hi and ap_lo) as well as cholestrol level appear to be different between normal and diseased groups.
<b>Script:</b> {LINK TO IPYTHON NOTEBOOK}<br>


