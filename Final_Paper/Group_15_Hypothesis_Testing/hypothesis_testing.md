# Introduction to Hypothesis Testing
---
## Table of Contents
---
1. [What is Hypothesis Testing?](#1)  
    1.1 [Creating a Null and Alternative Hypothesis](#2)  
    1.2 [Gathering data](#3)  
    1.3 [Test Statistic](#4)  
    1.4 [P-value](#5)  
    1.5 [Making a decision based off of the P-value](#6)  
2. [Considerations when chosing the significance threshold](#7)
3. [Applications of Hypothesis Testing to DESeq2](#8)
4. [Conclusion](#9)
---
## What is Hypothesis Testing? Why is it important? <a name="1"></a>

Hypothesis Testing is the use of statistical analysis on data to evaluate the validity of a hypothesis. It allows researchers to make evidence-based conclusions. 

The use of hypothesis testing expands beyond bioinformatics. It allows researchers in all fields to make informed predictions as well as decisions based on quantifiable evidence. Hypothesis testing allows people to systematically and objectively ensure quality, assess risk, validate research, as well as complete countless other tasks. 

The 5 steps of Hypothesis Testing:  
      Form a Null and Alternative Hypothesis  
      Gathering Data  
      Generate a Test Statistic  
      Generate P-value  
      Interpret P-value and Make a Decision  

To illustrate the steps of hypothesis testing, we will be looking at a hypothetical case study. Our example case study will look at whether or not smoking causes lung cancer. 

---

## Creating a Null and Alternative Hypothesis <a name="2"></a>

A hypothesis is a proposed statement that makes a prediction on the outcome of a study, based on past evidence. It must be testable, measurable, falsifiable, and be written in a clear, understandable way. When hypothesis testing, we need two hypotheses that compete against each other: null hypothesis and alternative hypothesis. These two cannot be both true or false at the same time. 

A null hypothesis is typically the simpler of the two statements, and would hypothesize that there is no significant difference between the measured variables. It hypothesizes that any observed change is due to experimental or testing error. The null hypothesis is usually assumed true. 

An alternative hypothesis hypothesizes that there is a significant difference between the different measurements, and that there is a low possibility that the difference is due to chance. The alternative hypothesis needs to be proven true at the end of the hypothesis testing. 

Hypothesis tests can be split into one-tailed and two-tailed tests. One-tailed tests mean that the variable is known to be either bigger or smaller than the value specified in the null hypothesis. These can be represented as $H_0: \mu= 0, H_1: \mu > 0$, or  $H_0: \mu=0, H_1: \mu < 0$, where $H_0$ represents the null hypothesis, $H_1$ represents the alternative hypothesis, and $\mu$ represents the value. 

Two-tailed tests mean that the variable is not equal to the value specified in the null hypothesis, however it is unknown whether it is bigger or smaller than the value. These can be represented as $H_0: \mu=0, H_1: \mu \neq  0$. 

**Knowledge Check**

What could be the possible null hypothesis for our case study?

<details>
    <summary>Answer: </summary>
    There is no significant difference between the variables smoking and lung cancer. Smoking is not associated with lung cancer. 
</details>

What could be the possible alternative hypothesis for our case study?

<details>
    <summary>Answer: </summary>
    There is a significant difference between the variables smoking and lung cancer. Smoking is associated with lung cancer.  
</details>

---

## Gathering data <a name="3"></a>
Generating data is the most important step for testing the hypothesis. It consists of running experiments to manually get the data, or using previous sources of data.

Data should be relevant to the hypothesis and able to be used as an argument for any of the two hypotheses. The data generated should be free of confounding variables and must be quantifiable in some aspect. It is important to try and be as thorough in gathering the data as to not let any bias change the results of the testing.

**Case Study**

We want to gather data about smokers and lung cancer. 

**Knowledge Check**

Based on the hypotheses we created in the previous step and the questions we want to answer, how would we gather and put the data together?

<details>
    <summary>Answer: </summary>
    We could interview lung cancer patients and ask them if they have smoked before or not. We can then count the number of patients in these categories. 
</details>

What is another way of gathering this data?

<details>
	<summary>Answer: </summary>
	We could also follow a group of smokers and nonsmokers through the years, and record if they got diagnosed with lung cancer or not. There are also other ways to collect this data. 
</details>

**Case Study**

We've gathered this data from interviewing lung cancer patients and asking them if they are a smoker or a non-smoker. 

<img src="data_table.png"  width="50%" height="50%" />

---

## Test Statistic <a name="4"></a>
A test statistic is a single number, generated by a statistical test such as the t-test, z-test, or Wald test, that summarizes the data into one single variable. There are various methods for generating test statistics, and each is ideal for different situations. It is important to choose the appropriate test beforehand as this ensures any bias from the results of data gathering are removed.

There are countless amounts of statistical tests, each providing a use in different situations. In order to simplify choosing a statistical test, there are three main criteria to look out for: 

1. The types of variables: binary, categorical, or continuous
	- a binary variable means there are only two possible values (e.g. "yes or no")
	- a categorical variable means there are predefined names or labels the variable can take on (e.g. "below average", "average", "above average")
	- a continuous variable means the variable can take on any value within a range (e.g. any real number between 0 and 1)
2. The type of data: paired or unpaired
	- the data is paired if there is a relation between the two datasets that one is comparing
 	- the data is unpaired if the two datasets are not related or are independent
3. The study design: parametric or non-parametric, one-tailed or two-tailed
	- A study is parametric when there are assumptions made about the shape or parameters of the data (e.g. assuming the data follows a normal distribution)
 	- A study is non-parametric when there are no assumptions made about the shape or parameters of the data
	- A one-tailed test is suitable when the parameter of interest only changes in one direction (i.e. it either increases or decreases)
	- A two-tailed test is suitable when the parameter of interest can change in any direction

<img src="test_statistic_chart.png"  width="50%" height="50%" />

**Knowledge Check**

How many variables do we have? Which are independent and which are dependent?
<details>
	<summary>Answer: </summary>
	We have two variables: smoking and lung cancer. Smoking is independent as it is the variable that we are able to change. Lung cancer is the dependent variable because the value of it depends on our independent variable.
</details>

What type of variable is the independent variable? What type of variable is the dependent variable?
<details>
	<summary>Answer: </summary>
	Our independent variable is binary because there are only two values: a person is either a smoker or they are not. Our dependent variable is also binary. A person either has or doesn't have lung cancer.
</details>

What study design is our case study? Is it paired or unpaired? Is it one-tailed or two-tailed?
<details>
	<summary>Answer: </summary>
	We are using an unpaired study because the groups of smokers and non-smokers are separate. We are going to be using a two-tailed test because we don't know if smoking definitively increases or decreases the likelihood of lung cancer. 
</details>

Given the criteria of our study, which test statistic would be ideal for our cases? Please refer to the table provided for help.
<details>
	<summary>Answer: </summary>
	The chi-squared test would be ideal for our situation because our indepdent and dependent variables are both binary variables. Our study is non-parametric because we are not making any assumptions about the distribution of our data.
</details>

**Case Study**

For our case study, we have calculated our expected values, and it is highlighted in green. We found these expected values by using the formula:
$$expectedCount = \frac{(rowTotal)(columnTotal)}{tableTotal}$$

The reason why the expected values are the same is because the expected values assume that there is no correlation between smoking and lung cancer (assuming the null hypothesis is true).

To find our test statistic for Chi-squared tests, we used the equation:

<img src="chi-squared_equation.png"  width="50%" height="50%" />

Where O represents the observed value, and E represents the corresponding expected value.

<img src="data_table_with_expected.png"  width="50%" height="50%" />

---

## P-value <a name="5"></a>
Once we have generated a test statistic, we need to generate a p-value from that statistic. The p-value is the chance of seeing a test statistic equal or more extreme than the generated test statistic given that the null hypothesis is true. The p-value ranges from 0 to 1, the lower the value the more likely the difference is real and not caused by random sampling. The p-value is calculated by finding the CDF of the null distribution. 
The CDF of the null distribution can be found through 2 ways.
1. The mathematical form of the CDF can be determined using assumptions on the distribution itself.
2. Computer simulations can be used to produce random data points using the null hypothesis. The data points can be aggregated to approximate the CDF of the null distribution. 

**Case Study:**
We can use our chi-squared value along with the degrees of freedom to find our p-value. Degrees of freedom can be found by multiplying the (number of sample columns - 1) by the (number of sample rows - 1) [3]. For chi-squared tests, the p-value can be found by using a calculator or by looking up a table. From a calculator, the p-value is equal to 2.184e-52. Note that it is unlikely you would find a p-value this extreme even when the null hypothesis is false.  

**Knowledge Check**

How many degrees of freedom are we using? How did we find that? 

<details>
    <summary>Answer: </summary>
    We are using 1 degree of freedom. We did (number of sample columns - 1) * (number of sample rows - 1). There are two sample columns (smoker and non-smoker) as well as two sample rows (lung cancer and no lung cancer). Doing the math, we get $(2-1) * (2-1) = 1$. 
</details>

What does our low p-value mean $(2.184 e-52)$?
<details>
    <summary>Answer:</summary>
    It means that it is very likely that the difference is real and not caused by random sampling. 
    
</details>

---

## Making a decision based off the P-value <a name="6"></a>

After we generate the p-value, we must make a decision to reject the null hypothesis or not reject the null hypothesis. 
We use a cut-off value 𝛂 to make this decision. This value must be decided ahead of time.
Most of the times, 0.05 is chosen as the arbitrary value  
For any p-value lower than or equal to 𝛂, the null hypothesis will be rejected
For any p-value higher than 𝛂, the null hypothesis will not be rejected

<img src="critical_value_graph.png"  width="50%" height="50%" />




**Knowledge Check**

If our 𝛂 is 0.05, what decision would we make based off of the p-value of our chi-squared test?
<details>
    <summary>Answer:</summary>
    Because our p-value of 2.184e-52 is less than 0.05, we would reject our null hypothesis. 
</details>

**Case Study**
Case study: for a chi-squared test, you can look directly at a table such as the one (below,above, depends on formatting). The table tells us the chi-squared value that corresponds to a significance threshold for a certain degree of freedom. This value is known as a critical value. If the chi-squared test value is higher than the table’s critical value, then that means the null hypothesis should be rejected. Otherwise, the null hypothesis cannot be rejected. 

<img src="chi-squared-table.png"  width="40%" height="40%" />


**Knowledge Check**

What chi-squared value from the table would correspond to our case study?

<details>
    <summary>Answer:</summary>
    The chi-squared critical value would be 3.841 This is because we have 1 degree of freedom, and 𝛂 is 0.05, so we would look for the critical value in the 1 degree of freedom row and the .05 column.
</details>

---

### Considerations when choosing the significance threshold <a name="7"></a>

The decision to reject the null hypothesis given that the null hypothesis is true (Reject H0 | H0) is known as a type I error.

The decision to not the null hypothesis given that the null hypothesis is not true (Not Reject H0 | H1) is known as a type II error. 

P(Reject H0|H0) = P(pδ|H0), P(Do not reject H0|H1) = P(p>δ|H1)

When the significance threshold increases, the chance of a type I error increases while the chance of a type II error decreases. 

Conversely, when the significance threshold decreases, the chance of a type I error decreases while the chance of a type II error increases.

Therefore, it is important to consider both types of errors when choosing a significance threshold. 


---

### Applications of Hypothesis Testing in DESeq2 <a name="8"></a>
Hypothesis testing is an important step in all experiments. 

For example, this is how DEseq2 applies the steps of hypothesis testing to find differentially expressed genes.

**Creating a Null and Alternative Hypothesis**  
   Deseq2’s null hypothesis for each gene is that the gene is not differentially expressed  
Deseq2’s alternative hypothesis for each gene is that the gene is differentially expressed

**Gather Data**  
	Deseq2 takes in FeatureCount data from an RNA-seq experiment
 
**Test statistic**  
Deseq2 uses the Wald test to generate the test statistic from feature count data

**P-value**  
	Deseq2 also uses the wald test to generate the p-value based on the test statistic values
 
**Make a decision based on the hypothesis**  
Based on a predetermined p-value threshold, genes will be classified as either differentially expressed or not differentially expressed. 


---

## Conclusions <a name="9"></a>

Different areas of science require hypothesis testing as a way to help scientists reach a conclusion on the outcome of the experiment, based on the data collected. It is important to know how to conduct hypothesis testing, including how to generate a test statistic, create a p-value, and evaluate the p-value. It is also important to correctly conduct the hypothesis testing as falsely accepting or rejecting a hypothesis could lead to incorrect conclusions and errors. 
