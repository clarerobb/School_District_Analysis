# City School District Analysis with Pandas

## Overview of the school district analysis
This analysis compares key metrics of student funding and standarized test scores across a city school district to showcase trends and preformance for the school board as they make budgets for the district. After the data was initally compiled, the school board notified the district of potential cheating with the ninth graders at Thomas High School. The data was removed and the analysis repeated.

## Data and Resources
Data source:
- schools_complete.csv  
- students_complete.csv <br /> 

Virtual Environment (PythonData) included some of the following packages: 
- anaconda 1.9.0
- conda 4.13.0
- ipykernel 6.9.1
- jupyter 1.0.0
- numpy 1.21.5
- pandas 1.3.5
- pip 21.2.2
- python 3.7.13

## Method
After importing the pandas dependency, loading the dataset, and cleaning the data, I ran the following code to change the math and reading grades from all Thomas High School ninth graders to NaN. 

~~~~
import numpy as np
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "reading_score"] = np.nan
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"] = np.nan
~~~~
I then created DataFrames to display the following: 
- district summary
- school summary
- top 5 performing schools
- bottom 5 performing schools
- average math and reading score for each grade level from each school
- scores based on school spending per student
- scores based on the size of the school
- scores based on the school type (charter or district)

## Results
The following results compare the requested metrics from the original analysis against the adjusted analysis. The original data contained the the math and reading scores for all **39,170 students** in the district. The adjusted analysis replaced the grades from the **461 Thomas High School ninth graders** to read as null data. While the total count of students did not change from the original to the adjusted analysis, the percentages of passing math, reading, and overall were recalculated by removing those students suspected of cheating from the total count for a total of **38,709 students in the district**.

#### District Summary 
As shown below, the district summary was not overly impacted by removing less than 500 test scores from an almost 40,000 student dataset. Differences in the average math score, passing math percentage, passing reading percentage, and overall passing percentage are all less than 1% and would round to the same whole number.

Original Analysis:
![Screen Shot 2022-07-03 at 2 51 24 PM](https://user-images.githubusercontent.com/106405775/177055236-8f76f0bc-d7e7-4d04-936f-4f35ba2aa75f.png)

Adjusted Analysis: 
![Screen Shot 2022-07-03 at 2 49 18 PM](https://user-images.githubusercontent.com/106405775/177055192-d6852e4e-9e01-4d26-b59b-2038edfda3e2.png)

#### School Summary 
The original analysis had Thomas High School at 90.9% overall passing rate which may have been too high. When recalculating the percentages after nullifying the data from the ninth graders, their overall passing rate lowered to 65%. However, this total is based off of 461 students with blank scores and thus skewed the data. To get a more accurate picture, THS's percentages needed to be calculated from the scores of the 10-12 grade students. After removing the THS 9th grade students from the total THS student count, their overall passing rate was only slightly lower at 90.6%. 

Original Analysis: 
![Screen Shot 2022-07-03 at 3 18 57 PM](https://user-images.githubusercontent.com/106405775/177055959-fcdd67dd-2d73-4ab8-b026-e603bf82d3ca.png)

Adjusted Analysis without removing the THS ninth graders from the total students:
![Screen Shot 2022-07-03 at 3 20 57 PM](https://user-images.githubusercontent.com/106405775/177056025-27b0efaa-74e2-416a-9669-b2731c7acb46.png)

Adjusted Analysis:
![Screen Shot 2022-07-03 at 3 19 55 PM](https://user-images.githubusercontent.com/106405775/177055992-f0df651f-3e72-4c91-a13b-16d8b3cd24e3.png)

#### Thomas High School’s performance relative to the other schools
After replacing the ninth graders' math and reading scores, Thomas High School still remains the second highest performing school in the district.

Original Analysis:
![Screen Shot 2022-07-03 at 3 31 26 PM](https://user-images.githubusercontent.com/106405775/177056355-69fbb973-1afd-41b9-9e04-1e20709b0146.png)

Adjusted Analysis:
![Screen Shot 2022-07-03 at 3 33 52 PM](https://user-images.githubusercontent.com/106405775/177056378-37a10e85-104e-41af-b320-17e6382cbc2c.png)

#### Math scores by grade
Prior to the adjustment, Thomas High School ninth graders were among the highest in the district with an average math score of 83.6.
| Original Analysis:    | Adjusted Analysis: |
|-----------------------|--------------------|
|![Screen Shot 2022-07-03 at 3 39 33 PM](https://user-images.githubusercontent.com/106405775/177056562-86f1be39-b8d0-4857-94f3-a9b011d1982f.png)|![Screen Shot 2022-07-03 at 3 37 17 PM](https://user-images.githubusercontent.com/106405775/177056525-3e5b643f-1c20-4965-851e-ccc6aa9bc55a.png)|

#### Reading scores by grade
Similarly, THS's ninth graders were also one of the highest in the district with the average reading score of 83.7 before those grades were replaced with NaN. 
| Original Analysis:    | Adjusted Analysis: |
|-----------------------|--------------------|
|![Screen Shot 2022-07-03 at 3 41 24 PM](https://user-images.githubusercontent.com/106405775/177056633-625ac4ee-56fb-40e6-99ea-e9e0a10bf0d8.png)|![Screen Shot 2022-07-03 at 3 42 17 PM](https://user-images.githubusercontent.com/106405775/177056662-ade5867f-a8ff-474f-b377-eb0255dd9b44.png)|

#### Scores by school spending
School spending per student was calculated by dividing the total school budget by the total number of students. School spending was sorted into four buckets: under $586, $586-$630, $631-$645, and $646-$675. Thomas High School is in the $631-$645 range. Removing the THS ninth graders scores did not affect the scores by school spending. 

Original Analysis: <br /> 
![Screen Shot 2022-07-03 at 3 59 01 PM](https://user-images.githubusercontent.com/106405775/177057121-f5fe39e1-a1c6-4ab5-b2b1-e5853bf75841.png)

Adjusted Analysis: <br /> 
![Screen Shot 2022-07-03 at 3 52 42 PM](https://user-images.githubusercontent.com/106405775/177056937-f91db53f-da33-44d6-aa11-02bed9f62e3b.png)

#### Scores by school size
School size was sorted into three categories: small (under 1,000 students), medium (between 1,000 to 1,999 students), and large (between 2,000 to 5,000 students). Thomas High School is included in the medium size school, and the adjustment did not affect the medium size school scores. <br /> 

Original Analysis: <br /> 
![Screen Shot 2022-07-03 at 4 11 23 PM](https://user-images.githubusercontent.com/106405775/177057384-ca235b55-838b-4891-bb74-c38fd6dc42be.png)

Adjusted Analysis: <br /> 
![Screen Shot 2022-07-03 at 4 06 14 PM](https://user-images.githubusercontent.com/106405775/177057272-b2795364-3183-4cd5-b3b3-7d48e22a173c.png)

#### Scores by school type
The City district has both charter and district schools. Thomas High School is a charter school, but removing their ninth grade scores did not impact the charter schools' grades or percentages. 

Original Analysis:<br /> 
![Screen Shot 2022-07-03 at 4 12 49 PM](https://user-images.githubusercontent.com/106405775/177057429-18e7c770-ac49-4757-8ea6-ff0f6ee80b73.png)

Adjusted Analysis:<br /> 
![Screen Shot 2022-07-03 at 4 13 52 PM](https://user-images.githubusercontent.com/106405775/177057439-b5876ad2-1d64-46eb-bf36-6dc5d4701fa9.png)


## Summary
Four changes after replacing the reading and math scores for the ninth grade at Thomas High School with NaNs:
1. The most obvious changes were seen in the math and reading scores by grade. In the original analysis, THS ninth graders were among the top preformers. After removing their grades though, they were out of the running entirely. 
2. In the school summary, Thomas High School went from an overall passing percent of 90.9% to a 65% when the grades were replaced. However, because that does not offer a complete picture of the school, their summary was recalculated by removing the 461 students from their total count which changed their overall passing rate to 90.6%. 
3. The district summary also showed nominal differences of less than 1% for the average math score, passing math percentage, passing reading percentage, and overall passing percentage.
4. While Thomas High School was still the second highest performing school in the district after removing the ninth grade scores, their overall percentage decreased to 90.63% bringing them much closer to the third performing school (Griffin High School at 90.59% overall passing).
