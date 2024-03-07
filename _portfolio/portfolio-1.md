# Diabetes in Pima women
![Diabetes](/images/image_1.jpg)
collection: portfolio
---
<h3> Introduction </h3>
This report presents data analysis work on patients with diabetes or at risk of developing diabetes belonging to the Pima people, a Native American people. The objective of this analysis is to obtain information about the health of these people, to find the relationship between risk factors and diabetes, as well as to estimate the probability of developing health complications.
<br></br>
<h3> Methodology </h3>
To perform this analysis, data were extracted from the <a href="https://www.kaggle.com/datasets/ashishkumarjayswal/diabetes-dataset?rvi=1">Kaggle website</a>, using a CSV (Comma Separated Values) file. The data were loaded into a database hosted in Google Cloud's BigQuery, using the test space of this platform and cleaned through different SQL queries.
The values to be taken for the analysis were the following:
<ul>
<li>Pregnancies: Number of times the woman has been pregnant.</li>
<li>Plasma glucose concentration in an oral glucose tolerance test.</li>
<li>Blood Pressure: Diastolic blood pressure (mm Hg).</li>
<li>SkinThickness: triceps skinfold thickness (mm).</li>
<li>Insulin: 2-hour serum insulin (mu U/ml).</li>
<li>BMI: Body mass index (weight in kg / (height in meters)^2).</li>
<li>DiabetesPedigreeFunction: Function that scores the probability of having diabetes based on family history.</li>
<li>Age: Age in years.</li>
<li>Outcome: The target variable; 0 for no diabetes, 1 for diabetes.</li>
</ul>
<br></br>
Data from 768 individuals were analyzed.
During data cleaning, 0 values were found in the Glucose, BloodPressure, SkinThickness, Insulin and BMI columns, in order to continue with the data cleaning process, these values were filled with null values. <br></br>
In order to perform the probability calculation, a Bayesian hypothesis was used that takes elements housed in a SQL View called rates, which houses the proportion of people with certain conditions in relation to the total sample, the calculated values are the following:
<ul>
    <li>total_diabetes: Total proportion of patients with diabetes in relation to the total sample.</li>
    <li>total_diabetesp: Total proportion of patients with diabetes who have ever had a pregnancy in relation to the total sample.</li>
    <li>total_diabetesnp: Total proportion of patients with diabetes who have not had a pregnancy in relation to the total sample.</li>
    <li>total_diabetes_high_bp: Total proportion of patients with diabetes and with a blood pressure greater than 90 mm/hg in relation to the total sample.</li>
    <li>total_diabetes_high_bmi: Total proportion of patients with diabetes and a body mass index greater than 30 in relation to the total sample.</li>
    <li>total_diabetes_high_st: Total proportion of patients with diabetes and triceps skinfold thickness greater than 20 mm in relation to the total sample.</li>
    <li>total_diabetes_dp: Total proportion of patients with diabetes and a high probability of diabetes due to family history greater than 0.30 relative to the total sample.</li>
    <li>total_diabetesg: Total proportion of patients with diabetes and a glucose greater than or equal to 140 relative to the total sample.</li>
    <li>total_nodiabetes: Total proportion of patients without diabetes in relation to the total sample.</li>
    <li>total_nodiabetes_p: Total proportion of patients without diabetes who have had at least one pregnancy in relation to the total sample.</li>
    <li>total_nodiabetes_np: Total proportion of patients who do not have diabetes and have not had a pregnancy in relation to the total sample.</li>
    <li>total_nodiabetes_high_bp: Total proportion of patients without diabetes and with blood pressure greater than 90 mm/hg in relation to the total sample.</li>
    <li>total_nodiabetes_high_bmi: Total proportion of patients without diabetes and body mass index greater than 30 relative to the total sample.</li>
    <li>total_nodiabetes_high_st: Total proportion of patients without diabetes and triceps skinfold thickness greater than 20 mm in relation to the total sample.</li>
    <li>total_nodiabetes_dp: Total proportion of patients without diabetes and a high probability of diabetes due to family history greater than 0.30 relative to the total sample.</li>
    <il>total_nodiabetes_glucose_prediabetes: Total proportion of patients without diabetes and a glucose between 140 and 199 relative to the total sample.</li>
</ul>
<br></br>
For the calculation of the probabilities the following formula P(A|B)=P(A)-P(B|A)/P(B) of Bayes' theorem was used in order to be realized, where:
<ul>
    <il>P(A|B) is the probability of event A given that event B has already occurred (posterior probability).</il>
<br>
    <il>P(A) is the prior probability of event A.</il>
<br>
    <il>P(B|A) is the probability of event B given that event A has already occurred (prior probability or likelihood).</il>
<br>
    <il>P(B) is the prior probability of event B (marginal probability).</il>
</ul>
<br></br>
In the consultation, the following probabilities are calculated:
<h4>Probability of developing diabetes:</h4>
<h5>Based on high BMI:</h5>
<ul>
    <li>P(diabetes | high BMI) = (P(High BMI | Diabetes) * P(Diabetes)) / P(High BMI).</li>
</ul>
<h5>Based on no previous pregnancies:</h5>
<ul>
    <li>P(Diabetes | No Pregnancies) = (P( No Pregnancies | Diabetes) * P(Diabetes)) / P( No Pregnancies).</li>
</ul>
<h5>Based on family history of diabetes:</h5>
<ul>
    <li>P(Diabetes | DiabetesPedigreeFunction > 0.30) = (P(DiabetesPedigreeFunction > 0.30 | Diabetes) * P(Diabetes)) / P(DiabetesPedigreeFunction > 0.30).</li>
</ul>
<h5>Based on prediabetic blood glucose levels:</h5>
<ul>
    <li>P(Diabetes | Glucose between 140 and 199) = (P(Glucose between 140 and 199 | Diabetes) * P(Diabetes)) / P(Glucose between 140 and 199).</li>
</ul>
<h4>Probability of developing health complications in people with diabetes:</h4>
<h5>Based on high BMI:</h5>
<ul>
    <li>P(Complications | Diabetes, High BMI) = (P(High BMI | Diabetes, Complications) * P(Diabetes, Complications)) / P(High BMI).</li>
</ul>
<h5>Based on triceps skinfold thickness greater than 20 mm:</h5>
<ul>
    <li>P(Complications | Diabetes, SkinThickness) = (P(SkinThickness | Diabetes, Complications) * P(Diabetes, Complications)) / P(SkinThickness).</li>
</ul>
<h5>Based on high blood pressure:</h5>
<ul>
    <li>P(Complications | Diabetes,Blood Pressure) = (P(Blood Pressure | Diabetes, Complications) * P(Diabetes, Complications)) / P(Blood Pressure).</li>
</ul>
<h3>Comments:</h3>
<h4>Glucose levels:</h4>
Here we find a problem with the congruence of the data, apparently the values of the glucose tolerance test to give diabetes is above 200, but in the data set has been recorded as diabetic people who have these values below 200, in a real case would have to rethink the modeling of the data to obtain more accurate results.
<h3>Results:</h3>
<ul>
    <li>Of the 768 people in the data set, 34.89% (268 people) have diabetes and 65.11% (500 people) do not have diabetes.</li>
    <li>33.58% of the people with diabetes (90 people) have a blood pressure greater than 80 mm/hg, which is conducive to developing health complications.</li>
    <li>81.71% of people with diabetes (219 people) have a high BMI, this favors developing health complications.</li>
    <li>61.56% of people with diabetes (165 people) have a triceps skinfold thickness greater than 20 mm, this favors developing health complications.</li>
    <li>85% of people with diabetes (230 people) have had at least one pregnancy.</li>
    <li>15% of people with diabetes (37 people) have not had any pregnancies.</li>
    <li>23% of people without diabetes (115 people) have a blood pressure greater than 80 mm/hg, which is conducive to developing health complications.</li>
    <li>50.6% of people without diabetes (253 people) have a BMI greater than 30, which is conducive to developing health complications.</li>
    <li>53% of people without diabetes (265 people) have a triceps skinfold thickness greater than 20 mm, this favors developing health complications.</li>
    <li>85.4% of people without diabetes (427 people) have had at least one pregnancy.</li>
    <li>14.6% of people without diabetes (73 people) have not had any pregnancy.</li>
    <li>12.4% of people without diabetes (62 people) have a glucose level between 140 and 199, which indicates that they are at risk of developing diabetes.</li>
    <li>55.4% of people with diabetes (277 people) have a Diabetes Pedigree Function greater than 0.30, which favors the development of diabetes.</li>
    <li>The probability of developing diabetes based on a BMI greater than 30 is 68.307%.</li>
    <li>The probability of developing diabetes based on whether you have had a pregnancy is 23.117%.</li>
    <li>The probability of developing diabetes based on Diabetes Pedigree Function is 73.604%.</li>
    <li>The probability of developing diabetes based on high blood glucose is 46.144%.</li>
    <li>The probability of developing health problems in diabetic persons based on a BMI greater than 30 is 31.692%.</li>
    <li>The probability of developing health problems in diabetic persons based on a triceps skinfold thickness greater than 20 mm is 25.022%.</li>
    <li>The probability of developing health problems in diabetic persons based on a blood pressure greater than 80 mm/hg is 33.396%.</li>
</ul>
<br></br>
<h3>Conclusions</h3>
<ul>
    <li>There are probabilities of developing diabetes based on different factors: The calculated probabilities show that certain factors, such as a high BMI, a history of pregnancy, and a high Diabetes Pedigree Function, are associated with an increased risk of developing diabetes.</li>
    <li>Diabetes Pedigree Function and diabetes: More than half of people with diabetes have a Diabetes Pedigree Function greater than 0.30, which may indicate a genetic predisposition to diabetes.</li>
    <li>High BMI and diabetes: 82% of people with diabetes have a high body mass index (BMI), suggesting an increased risk of developing health complications associated with obesity.</li>
    <li>Pregnancy: No clear association was found between the number of pregnancies and the development of diabetes.</li>
</ul>
<br></br>
<h3>Recommendations</h3>
<ul>
<li>Expand the sample to have greater precision when analyzing the data and thus be able to make better predictions.</li>
<li>Develop strategies for diabetes prevention and control, taking into account risk factors, constantly monitoring BMI and blood pressure.</li>
<li>Access to health resources to inform people about risk factors and information about diabetes screening.</li>
<li>Emotional and psychological support for people with diabetes to cope with the disease.</li>
</ul>
<br></br>
<h3>Limitations:</h3>
<ul>
    <li>Additional data and correction of glucose data are needed for better results to understand the complexity of diabetes.</li>
</ul>
<br></br>
<h3>Dashboard:</h3>
<div class='tableauPlaceholder' id='viz1709676426907' style='position: relative'><noscript><a href='#'><img alt='Diabetes in Pima Indian Women ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;DI&#47;DIabetesINPimaIndianWomen&#47;DiabetesinPimaIndianWomen&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='DIabetesINPimaIndianWomen&#47;DiabetesinPimaIndianWomen' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;DI&#47;DIabetesINPimaIndianWomen&#47;DiabetesinPimaIndianWomen&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='es-ES' /></object></div>                
<h3>Files:</h3>
<ul>
    <li><a href="https://drive.google.com/file/d/19xyw9k81XFa283AHHy9EP_RDdEpihJgH/view?usp=drive_link"> Queries</a>
    <li><a href="https://drive.google.com/drive/folders/1xKLRWmAmULszkv0TGYEHN6jlNcq1Bg4i?usp=sharing"> Data</a>
