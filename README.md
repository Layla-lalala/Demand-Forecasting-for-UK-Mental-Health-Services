# Demand-Forecasting-for-UK-Mental-Health-Services
Predicting depression treatment demand in England using NHS data and Leslie Matrix modeling. Includes full project report and presentation for data-driven policy planning.


# Introduction
Depression and mental illness have become pressing public health issues in the UK. The latest research shows that over 50% of UK workers have symptoms of depression, highlighting the wide prevalence of this problem. This project is a data science application practice aimed at social well-being, which intends to predict future trends in depression prevalence and treatment in England by using real medical and health data. Our goal is to provide forward-looking references for public resource allocation and policy intervention through modeling and analyzing the occurrence and recovery of depression, helping relevant stakeholders (such as the NHS or the government) to be well-prepared in advance, thereby improving the overall mental health level.


# Dataset
The analysis is based on NHS England mental health data (2017–2023). The dataset includes yearly aggregated figures on key metrics:
New Referrals to mental health services (annual count of new cases seeking help)
Patients in Hospital Treatment for mental illness (annual count)
Patients in NHS Talking Therapy (annual count in the NHS Talking Therapies program)
Patients Prescribed Antidepressants (annual count of individuals on medication)
Reliable Recovery Rate (proportion of patients who achieved recovery, as defined by NHS criteria)
Reliable Deterioration (Relapse) Rate (proportion of cases where patients’ conditions reliably worsened)

All the data are sourced from the official digital portal of NHS, ensuring their authority and timeliness. It is particularly noted that we strictly follow the NHS's standard definitions of "recovery" and "recurrence", for instance, mild improvement will not be counted as recovery to enhance the prediction accuracy. All the original data have been cleaned and aggregated by year.


# Methodology
Our approach combined exploratory data analysis with a predictive modeling technique to forecast depression trends:

Exploratory Analysis: First, we conducted exploratory data analysis, including the calculation of the correlation matrix among variables. The results showed a reasonable positive correlation. For instance, years with a higher number of referrals usually had a greater use of antidepressant drugs. Additionally, we calculated the annual growth rate of referrals and found that the average annual growth rate was approximately 8.5%, which became an important basis for model setting.

Model Development: We built a dynamic systems model based on a modified Leslie Matrix approach. The Leslie matrix, traditionally used for population dynamics, allowed us to model transitions of individuals through different states of mental health. We defined four key states in the context of depression:

Clinically Depressed (C): Individuals experiencing clinically significant depression symptoms (the pool of people who need help).

Under Treatment (T): Individuals receiving treatment for depression (e.g., therapy or hospital care).

On Medication (A): Individuals prescribed antidepressant medication.

Recovered (R): Individuals who have recovered (achieved reliable improvement).

The model is essentially a set of linear equations that move a cohort of individuals through these states year by year, using a transition matrix. Each cell in the matrix represents a rate of moving from one state to another (for example, a certain fraction of the untreated depressed group will enter treatment each year, some fraction of those in treatment will recover, etc.). We estimated these transition rates from the data and literature. The model also includes new entries each year (new cases of depression) as an input vector. By iterating this model, we can simulate how the numbers in each state evolve over time.

Implementation & Validation: The model is written in Python, and the core uses NumPy for matrix operations. We calibrated the model using historical data and used a certain year (such as 2020) to predict the following year (such as 2023), and compared the predicted results with the actual 2023 data to verify the prediction accuracy. The error between the predicted results and the actual values is small, and the model has been verified to be applicable for future trend prediction.

Forecasting: Using the validated model, we projected the depression-related metrics up to five years into the future. This produced yearly forecasts for how many people will be depressed, in treatment, on medication, and recovered, given current trends.


# Key Findings

From the model and analysis, we derived several important findings:
1. Rising Depression Prevalence:
The total number of individuals suffering from depression in England is projected to increase significantly in the coming years. Our model estimates the depressed population could reach about 7.4 million people by 2029 (up from ~5.1 million in 2023), underscoring a growing demand for mental health services if current trends continue.

2.Treatment Dynamics: 
The number of patients receiving treatment is expected to peak and then decline around 2025, possibly due to service bottlenecks or insufficient resources. This indicates that if no additional investment is made, the treatment capacity will lag behind the disease trend.

3. Recovery and Relapse Trends:
Although more and more patients will achieve recovery, the challenges of maintaining the recovery still exist. It is necessary to strengthen the follow-up and support services after rehabilitation. The model indicates that the "recovery group" will become the fastest-growing group, reflecting the importance of subsequent follow-up and psychological follow-up services.


# Business Implications

This project’s findings carry important implications for healthcare policy and resource planning in the UK. In a business or policy context, the data-driven insights can guide decision-makers to act proactively:

Strategic Healthcare Planning: The model's predictions can provide a quantitative basis for the NHS and the government to plan resources. For instance, increasing the investment in training and treatment channels for psychotherapists and enhancing the coverage of Talking Therapies by 2025.

Resource Allocation & Cost Efficiency: By predicting trends to optimize budget allocation and reduce resource waste, "on-demand supply" can be achieved. The model can help prevent the mismatch between service capabilities and demands, and save costs.

Policy Simulation: Another implication is the ability to use this model as a sandbox for policy testing. We can simulate “what-if” scenarios – for example, What if the NHS introduces a new community counseling program or a digital therapy app? Using the model, we can project how such an intervention would affect overall treatment and recovery rates in the next few years. This helps policymakers predict the impact of innovations or reforms before implementing them. By comparing scenarios (with vs. without a new intervention), leaders get data-backed evidence to support decisions on mental health initiatives.

In summary, this project quantifies mental health challenges through a data-driven approach and proposes response strategies through modeling analysis. It is an exemplary application of data science in the field of social well-being. Through predictions and intervention suggestions, we demonstrate how data can contribute value in actual policies and public services.
