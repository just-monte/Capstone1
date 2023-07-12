![cover_photo](https://github.com/just-monte/Capstone/blob/756e9783d615090908e119220c66c5f51b3359dd/README_files/cover_photo.png)
# Capstone: Predicting Student Success 
According to the Education Data Initiative, [EDI](https://educationdata.org/college-dropout-rates#:~:text=In%20the%20United%20States%2C%20the,college%20dropout%20rate%20at%2054%25), about 40% of undergraduates drop out. First-year undergraduates have a 12-month dropout rate of 24%. College dropouts on average make 32% less than those with bachelor's degrees and are 19% more likely to be unemployed than someone with a degree. In 2020, 39 million Americans dropped out of college, and only 944,200 re-enrolled during the fall.

The recent national fluctuation of college dropouts has caused more focus on student retention. By identifying the most at-risk population, a university would be able to provide resources and create specified plans for students who are struggling. Ultimately, decreasing the university drop-out rate.
## 1. Data
The dataset consisted of 2 datasets. The main dataset from UC Irvine Machine Learning Respiratory, “ Predict students' dropout and academic success”, and Kaggle Dataset as supplement. To view the dataset clink on the links below: 
> * [UC Dataset](https://archive-beta.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

> * [Kaggle Dataset](https://www.kaggle.com/datasets/andrewmvd/global-education-statistics)
> * * Specifically CVS: EdStatsData

## 2. Data Wrangling 
[Data Wrangling](https://github.com/just-monte/Capstone/blob/0b23bba128f8dc644f2ca3cbf4b96be5453e3007/Capstone%202-%20Data%20Wrangling.ipynb)

The final dataframe was a merger between 2 datasets (‘Graduate Rate’ and ‘Ed Stats Data’) using ‘graduate rate' as the bases of the dataframe and ‘ed stats' for additional features needed. Once exploring both datasets, I noticed that ‘Ed Stats’ only went up to the year 2014. Due to this, I used 2014 as the stat data since it was the most recent year. The datasets were merged by a left join using nationality as the common feature. The two features of interest added were “adj net enrollment of lower secondary” and “ tertiary educ enrollment(all programs)”. 

After the mergers were completed, I checked for any null values. “Adj net enrollment of lower secondary” had 66 null values and “tertiary education enrollment(all programs)” had 19 null values. To fill in these null values I imputed the mean from each column. 

## 3.EDA 
[EDA](https://github.com/just-monte/Capstone/blob/0b23bba128f8dc644f2ca3cbf4b96be5453e3007/Capstone%202-%20EDA.ipynb)

Once I began to explore the data, I noticed a discrepancy that the majority of the participants were from Portugal. This could have been due to a few possible reasons: the location of the institute the data was sourced from, the institute’s international outreach, or the educational resources in Portugal. 

In lower secondary enrollment, Lithuania came first with 99.41%, the United Kingdom second with 96.08%, and Spain in third with 94.08%. When analyzing tertiary education enrollment, Brazil had the highest enrollment with 8,072,146 students. Turkey came second with an enrollment of 5,472,521 students, and Mexico with the third highest enrollment of 3,419,391 students. Not surprised to see Portugal on the lower end of tertiary education enrollment due to the majority of the participants being from Portugal. Reinforcing the idea that most students in Portugal seek tertiary education outside of the country. 

Based on the graduate data, students from Germany, Italy, and Dutch had the highest graduate percentage. Spain had the lowest graduate percentage with 30%. Note these percentages may not be a true indicator as the majority of the participants of this dataset were from Portugal. 

No particular trend was noted in the age of enrollment. In regards to gender, females showed a higher graduation rate of 62.2% compared to males which had 37.8%.

When analyzing admission grades, no pattern was noted. Indicating admission grades may not be an affecting factor for graduates. This possessed the question, “Are grades a deciding factor whether or not a student graduates”. To further investigate this I choose to look into the curricular units 2nd semester grades. No relationship was shown between the graduate’s grades in the 2nd semester. 


![](https://github.com/just-monte/Capstone/blob/aa0b742604f37b91ccadbc03d0588aad1afa157c/README_files/Admission_n_2nd.png)


## 4. Algorithms & Modeling 
[Model](https://github.com/just-monte/Capstone/blob/0b23bba128f8dc644f2ca3cbf4b96be5453e3007/Capstone%202%20-%20Modeling%20.ipynb)

I choose to work with the Python Scikit-Learn library for training. I used 2 algorithms: Random Forest Classifier and Decision Tree to test the model. 
![](https://github.com/just-monte/Capstone/blob/aa0b742604f37b91ccadbc03d0588aad1afa157c/README_files/Testing.png)
After hyperparameter tuning, the best model was the Random Forest Classifier with a testing accuracy of 76.8 %.  

## 5. Model Predications 
[Predications](https://github.com/just-monte/Capstone/blob/0b23bba128f8dc644f2ca3cbf4b96be5453e3007/Capstone%202%20-%20Modeling%20.ipynb)


Based on the Random Forest model, the feature with the most importance was feature 30, "Curricular units 2nd sem (approved)". Feature 24, " Curricular units 1st sem (approved)", and feature 31, "Curricular units 2nd sem (grade)", tied for second. All of these features indicated semester grades as a major indicator.

![](https://github.com/just-monte/Capstone/blob/756e9783d615090908e119220c66c5f51b3359dd/README_files/Model_1.png)

These findings were not surprising as grades typically do play an important role in whether or not someone will  graduate. I decided to take a closer look at the data without the semester grades included to see what other driving factors play a role. Based on the new model, feature 12 “Admission grade” was highest in importance. Feature 6, "Previous qualification (grade)", and feature 19, "Age at enrollment", were also of high importance. With feature 6 edging out feature 19 by 0.00112. Other features worth noting were feature 3, "Course", and feature 16, "Tuition fees up to date". From these findings, one can see that whether a student graduates is based on more than just grades but also other external factors. 

![](https://github.com/just-monte/Capstone/blob/aa0b742604f37b91ccadbc03d0588aad1afa157c/README_files/%20Model_2.png)


## 6. Future Improvements 
* In the future, I would love to spend more time analyzing the relationship between semester grade and class credits in regards to graduate rate. 
* More diverse dataset in regards to race/ethnicity to exam the relationship between race and graduate further 


