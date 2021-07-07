# Pandas 
## PyCitySchools

![Education](Images/education.png)

Well done! Having spent years analyzing financial records for big banks, you've finally scratched your idealistic itch and joined the education sector. In your latest role, you've become the Chief Data Scientist for your city's school district. In this capacity, you'll be helping the  school board and mayor make strategic decisions regarding future school budgets and priorities.

As a first task, you've been asked to analyze the district-wide standardized test results. You'll be given access to every student's math and reading scores, as well as various information on the schools they attend. Your responsibility is to aggregate the data to and showcase obvious trends in school performance.

Your final report should include each of the following:

### District Summary

* Create a high level snapshot (in table form) of the district's key metrics, including:
  * Total Schools
  * Total Students
  * Total Budget
  * Average Math Score
  * Average Reading Score
  * % Passing Math (The percentage of students that passed math.)
  * % Passing Reading (The percentage of students that passed reading.)
  * % Overall Passing (The percentage of students that passed math **and** reading.)

```
# Count Unique School Names
total_schools = school_data_complete['school_name'].nunique()

# Count Total Students
total_students = school_data_complete['student_name'].count()

# Sum Budget Column
total_budget = school_data['budget'].sum()

# Average math score
average_math_score = school_data_complete['math_score'].mean()

# Average reading score
average_reading_score = school_data_complete['reading_score'].mean()

#Calculate the percentage of students with a passing math score (70 or greater)
#find all the sutdents with math socre at passing levels
passing_math = school_data_complete.loc[(school_data_complete['math_score'])>=70]
# of students passing math 
count_passing_math = passing_math['math_score'].count()
# the calculation of % passing math
percent_passing_math = (count_passing_math / total_students)*100

#Calculate the percentage of students with a passing reading score (70 or greater)
#find all the sutdents with read socre at passing levels
passing_reading = school_data_complete.loc[(school_data_complete['reading_score'])>=70]
# of students passing math
count_passing_reading = passing_reading['reading_score'].count()
# the calculation of % passing read
percent_passing_reading = (count_passing_reading / total_students)*100

#Calculate the percentage of students who passed math and reading (% Overall Passing)
#find all students with both passing scores in math and read
overall_passing = school_data_complete.loc[(school_data_complete['math_score']>=70) & 
                                           (school_data_complete['reading_score']>=70)]
#count the number of students passing both
overall_passing_count = overall_passing['student_name'].count()
#the calculation of % overall passing
percent_overall_passing = (overall_passing_count / total_students) * 100

# new DF Dictionary and creating DF
district_summary = pd.DataFrame({'Total Schools' : [total_schools],
                                        'Total Students' : [total_students],
                                        'Total Budget' : [total_budget],
                                        'Average Math Score' : [average_math_score],
                                        'Average Reading Score' : [average_reading_score],
                                        '% Passing Math' : [percent_passing_math],
                                        '% Passing Reading' : [percent_passing_reading],
                                        '% Overall Passing' : [percent_overall_passing]
                                       })
#making a copy of the df without formating
district_summary_df = district_summary
#formatting the DF
district_summary['Total Budget'] = district_summary['Total Budget'].map('${:.2f}'.format)
district_summary['Average Math Score'] = district_summary['Average Math Score'].map('{:.2f}'.format)
district_summary['Average Reading Score'] = district_summary['Average Reading Score'].map('{:.2f}'.format)
district_summary['% Passing Math'] = district_summary['% Passing Math'].map('{:.2f}%'.format)
district_summary['% Passing Reading'] = district_summary['% Passing Reading'].map('{:.2f}%'.format)
district_summary['% Overall Passing'] = district_summary['% Overall Passing'].map('{:.2f}%'.format)
district_summary
```

### School Summary

* Create an overview table that summarizes key metrics about each school, including:
  * School Name
  * School Type
  * Total Students
  * Total School Budget
  * Per Student Budget
  * Average Math Score
  * Average Reading Score
  * % Passing Math (The percentage of students that passed math.)
  * % Passing Reading (The percentage of students that passed reading.)
  * % Overall Passing (The percentage of students that passed math **and** reading.)

### Top Performing Schools (By % Overall Passing)

* Create a table that highlights the top 5 performing schools based on % Overall Passing. Include:
  * School Name
  * School Type
  * Total Students
  * Total School Budget
  * Per Student Budget
  * Average Math Score
  * Average Reading Score
  * % Passing Math (The percentage of students that passed math.)
  * % Passing Reading (The percentage of students that passed reading.)
  * % Overall Passing (The percentage of students that passed math **and** reading.)

### Bottom Performing Schools (By % Overall Passing)

* Create a table that highlights the bottom 5 performing schools based on % Overall Passing. Include all of the same metrics as above.

### Math Scores by Grade\*\*

* Create a table that lists the average Math Score for students of each grade level (9th, 10th, 11th, 12th) at each school.

### Reading Scores by Grade

* Create a table that lists the average Reading Score for students of each grade level (9th, 10th, 11th, 12th) at each school.

### Scores by School Spending

* Create a table that breaks down school performances based on average Spending Ranges (Per Student). Use 4 reasonable bins to group school spending. Include in the table each of the following:
  * Average Math Score
  * Average Reading Score
  * % Passing Math (The percentage of students that passed math.)
  * % Passing Reading (The percentage of students that passed reading.)
  * % Overall Passing (The percentage of students that passed math **and** reading.)

### Scores by School Size

* Repeat the above breakdown, but this time group schools based on a reasonable approximation of school size (Small, Medium, Large).

### Scores by School Type

* Repeat the above breakdown, but this time group schools based on school type (Charter vs. District).



