[Link to Full Slide Deck (with comments)](https://docs.google.com/presentation/d/1DXl83vDXpoQuyCMGHilI3D8hxATD2cgQEtDR2Q6ABRk/edit?usp=sharing)

# Introduction

Understanding what contributes to the sale price of a house, can greatly improve the experience of buying a home for both buyers and sellers. Inappropriately pricing a house can lead to negative experiences for sellers, such as underselling, elongated sale cycles, unsuccessful target marketing, and bad investments in low-value features. Alternatively, buyers may overpay for a house, experience trouble with their search criteria, and miss out on buying opportunities due to overpriced homes. 

#### Objective 

To help solve this problem, I've set out to **create a predictive model that gives us the expected sale price**, so that we can better understand what we can do to positively influence house sale prices and create a better home buying experience for buyers and sellers.

To evaluate the performance of my model's ability to predict new data, my predictions were submitted to a [Kaggle Competition](https://www.kaggle.com/c/dsir-720-project-2-regression-challenge/overview), which scored my performance by the Root Mean Squared Error (RMSE). 

# Data Description

For this project, I analyzed two files of housing data from Ames, IA. 

#### Training Set

This set contained all of the data that I used to train my model. I used the feature `SalePrice` as my target variable.

* Rows: 2051
* Columns: 81

#### Test Set

This set was used as a final test to evaluate how well my model predicts new data. **It contains the same features as the training set, excluding** `SalePrice`.

* Rows: 878

* Columns: 80

  

Reference the [Data Dictionary](https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/Data_Dictionary.md) in a separate markdown file.

# Exploratory Data Analysis

I few notable insights as I cleaned and manipulated the data. 

#### What are the sales prices of the homes? Are there any outliers?

<img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/price_dist.jpeg" alt="prices_dist" style="zoom:67%;" /> <img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/prices_box.jpeg" alt="price_plot" style="zoom:80%;" />

The mean of the house prices was **$181,484** .  There were also a few outliers greater than $550,000 that were removed from the model. 



#### Which neighborhoods are most expensive?

<img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/prices_by_neighborhood.jpeg" alt="prices_dist" style="zoom:87%;" /> 

The average prices of the houses by neighborhood ranged from **$100,231 - $329,675**. The most expensive and cheapest neighborhoods are as follows:

**Most Expensive:**

* StoneBr - $329,676
* NridgHt - $322,831

**Least Expensive:**

* IDOTRR - $100,371

* MeadowV - $100,231

  

#### What numerical features are most correlated to price?

<img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/corr-saleprice.jpeg" style="zoom:87%;" /> 

The most positively correlated features included: Overall Qual, Gr Liv Area, Garage Area, Garage Cars, Total Bsmt SF, 1st Flr SF, Year Built, Year Remod/Add.



#### What categorical features are correlated to price?

<img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/sale_type_cat.jpeg" style="zoom:87%;" /> <img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/bld_type_cat.jpeg" alt="prices_dist" style="zoom:87%;" /><img src="https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/kitch_qual_cat.jpeg" alt="prices_dist" style="zoom:87%;" />

New homes and sales that gaurantee the seller holds the deed have the most sales and highest price points. Target 1 Family homes and invest in your kitchen. 



# Modeling Process

For my model, I used a **Linear Regression** and **Elastic Net Regression** model to predict `Sale Price`. I performed a **Train, Test, Split** in order evaluate the bias/varience tradeoff between my model, evaluating how well it predicted current and new data. 

![timeline](https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/Timeline.png)

*Note: Green points ended up improving my score, red points ended up hurting my score*

### Model Results

My model appeared to be slightly overfit, but nonetheless produced a quality score.

![model](https://git.generalassemb.ly/Jmizraji/Submissions/blob/master/Projects/project_2-master/imgs/enet_results_sc.jpeg)

**Train, Test, Split** **(R2)**

* Train: 0.917859994162
* Test: 0.8833326064739

**Mean Cross Validation Score (R2)**

* 0.8972232611308646

**Kaggle Submission (RMSE)**

* 29000.28494 (70% of data)
* 24472.33941 (30% of data)

# Recommendations 



* Invest in quality homes with quality materials
* Keep the kitchen quality or remodel the kitchen
* Target 1 family homes for a competitive price
* Possible investment strategy could be to invest in a mid-priced house in either StoneBr or NridgHt, as house prices could continue to stay high as the neighborhood grows or invest in a cheaper neighborhood such as IDOTRR or MeadowV if they are up and coming.
* Build a new home to sell at the highest price
* Older homes generally sell at lower prices, but are not a dealbreaker 