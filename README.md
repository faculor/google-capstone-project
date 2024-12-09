# **Google Advanced Data Analytics Capstone Project**

## **Salifort Motors HR Department**

This is my capstone project for the Google Advanced Data Analytics course from Google and Coursera. The project includes an analysis  of a dataset and the construction of predictive models that can provide insights to the Human Resources (HR) department of a large industrial firm.
---

### **Business scenario and problem**

The HR department at Salifort Motors wants to take some initiatives to improve employee satisfaction levels at the company. They collected data from employees, and now they need to extract useful insights from it. They want data-driven in order to answer the following question: what’s likely to make the employee leave the company?

The goals set to accomplish this project are:
 - Analyze the data collected by the HR department
 - Build a model that predicts whether or not an employee will leave the company.

The logic behind the project is that if the resignation of employees can be predicted, it might be possible to identify factors that contribute to they leaving. Because it is time-consuming and expensive to find, interview, and hire new employees, increasing employee retention will be beneficial to the company.

### **The data used in the project**

The dataset contains data about employees with 15,000 rows and 10 columns. In the following table, a summary of the variables with the corresponding description

Variable  |Description |dtype |
-----|-----|-----|
satisfaction_level|Employee-reported job satisfaction level [0&ndash;1]|float64|
last_evaluation|Score of employee's last performance review [0&ndash;1]|float64|
number_project|Number of projects employee contributes to|int64|
average_monthly_hours|Average number of hours employee worked per month|int64|
time_spend_company|How long the employee has been with the company (years)|int64|
Work_accident|Whether or not the employee experienced an accident while at work|int64|
left|Whether or not the employee left the company|int64|
promotion_last_5years|Whether or not the employee was promoted in the last 5 years|int64|
Department|The employee's department|object|
salary|The employee's salary (U.S. dollars)|object|

An Exploratory Data Analysis is conducted to find, correct an structure the possible deficiencies in the dataset configuration (ex. null or duplicated values).

Initiating the analysis from the level of satisfaction expressed by the workers, and setting and arbitrary division at 0.5 points (in a scale from 0 to 1) to separate satisfied from unsatisfied employees, a first view shows that a 71.78% (8607 cases) expresses a satisfaction > than 0.5, and 28.22% (3384 cases) a satisfaction below that level, as the following visualization shows:

![Figure 1 - Satisfaction Distribution Count](./images/01_satistaction_level_count.png)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>satisfaction_level</th>
      <th>count</th>
      <th>percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>low</td>
      <td>3384</td>
      <td>28.221166</td>
    </tr>
    <tr>
      <th>1</th>
      <td>high</td>
      <td>8607</td>
      <td>71.778834</td>
    </tr>
  </tbody>
</table>
</div>

From this point, the analysis ivestigates the possible variables that may influence the level of satisfaction of the staff. This task is achieved using the tools provided by the packages explored during the course

Upon further analysis, the focus shifts to employees who have departed, and the satisfaction level they expressed:

![Figure 2 - Level of satisfaction of the departed employees](./images/01_left.png)

- The visualization satisfy parcially what could be expected: those less satisfied tends to leave more than those whose satisfaction is greater.
- But some odd information appears: in the *left* graphic, a departure of employees with 0.7 or more points of satisfaction arise, about 500 cases (eyballing the graphic)

![Figure 3- Satisfied workers who left](./images/03_left_satisfaction_level.png)

Left total number | High satisfactied (> 0.7)| Proportion|
-----|-----|-----|
1991 |530 |26.62%|

The staff who left, despite manifesting high levels of satisfaction, present some characteristics that warrant a review by the company:
1. All of them received performance ratings of 0.5 or higher, with a significant portion receiving 0.8 or higher. This indicates that they were all medium to high-performing employees.
2. On average, they worked more hours than the rest of the staff. The average monthly hours for all employees is approximately 200, while these employees averaged around 243 monthly hours.
3. Similarly, they were involved in more projects. The average number of projects for all employees is 3.8 (standard deviation: 1.16), while these employees averaged 4.5 (standard deviation: 0.6). Over half of these satisfied departed employees were involved in five projects (297 employees).
4. Regarding tenure, the average tenure for all company staff is 3.36 years, but for this group, it's 5.06 years. Most of these employees had five or six years of tenure in the company (5 years: 395; 6 years: 101). They represent 95.58% of this group and 24.91% of the total departing employees.
5. Only an average of 0.37% of the employees in this analysis received a promotion in the last five years, compared to the company-wide average of 1.69%.

Some questions arise from these results:

- Are we dealing with employees who have reached a plateau in their career development within the company?
- How are these employees distributed across the company's hierarchy?
- Where do these employees go after leaving the company?
- What incentives do they receive in their new roles outside the company?

### **Tools**

The task have been done in a Jupyter Notebook, using the following pacjages for the Python language:
- **Numpy** and **Pandas** for data analysis and manipulation
- **Matplotlib** and **Seaborn** for data visualizations
- **Scikit-learn** is used to machine learning model construction

### **Model**

A Logistic Regression model is constructed, due to the binary characterization of the target variable (`left` column). The objective of the model is to predict the departure of employees based on the relevant features contained in the dataset.

### **Deliverables**

The process produced two deliverables:
1. A Jupyter Notebook with all the work done
2. A executive summary with the most important results to comunicate to the stakeholders in the project