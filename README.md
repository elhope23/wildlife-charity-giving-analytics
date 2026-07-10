# Wildlife Charity Giving Analytics

According to the Charities Aid Foundation's [UK Giving Report 2026](https://www.cafonline.org/insights/research/uk-giving-report), there are six million fewer charity donors in the UK than there were a decade ago. Factors including a rising cost of living have meant that 1 in 5 people say they cannot afford to give to charity and we have seen the first fall in annual total giving since 2021 and the COVID-19 pandemic (£15.4 billion in 2024 down to £14 billion in 2025).

This is where the practice of data analytics is so valuable: supporting charities who might have limited fundraising resources (e.g. time, budget, staff capactiy) to make evidence-based fundraising decisions to increase their income. With charities being unable to solely depend on "force-of-habit" gift giving, they are required to work even harder to earn the trust and goodwill of potential donors and ensure that they engage effectively with their longstanding supporters. 

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)

## Dataset Content

* The dataset I have chosen is [Animal Charity: Wildlife Conservation Donations](https://www.kaggle.com/datasets/jaderz/synthetic-animal-charity-donations) - a public domain dataset sourced from Kaggle. 
* It is a **synthetic dataset** that includes 10,000 records that represent donations made to a fictional wildlife conservation charity. 
* The data simulates donation behaviour and includes the following columns:

|**Column Name**| **Description**|
|---------------|----------------|
|`donor_id`| Unique Donor ID linked to an individual donor to the charity|
|`age_group`| Age of the donor in age brackets|
|`gender`| Donor's gender|
|`name`| Donor's full name (synthetic)|
|`email`| Donor's email address (synthetic)|
|`country`| Donor's country of residence|
|`donation_type`| Monthly or one-off gift|
|`donation_amount`| Donation amount|
|`donation_date`| Donation date (2023-2025)|
|`payment_method`| What method of payment was used|
|`newsletter_opt_in`| Whether the donor agreed to receive email newsletters from the charity|
|`referral_channel`| How the donor found the charity|
|`sector`| The donor's professional sector|
|`campaign`| The charity's fundraising campaign the donor gave to|

## Business Requirements

* In the context of this synthetic data, this analysis will serve to support the wildlife conservation charity to know their donors better and understand how they give. This ensures that their fundraising activity can be more targeted and ultimately lead to better ROI on future fundraising activity.

|**Business Requirement**|*(Related Hypothesis)*|Description
|---|------|
|**Donation Amount by Age Group**| *(H1)* | Understand which donor segments (by age) generate the most value|
|**Monthly Donation Patterns**| *(H2)*| Identify patterns in donation volume to support campaign planning|
|**Payment Method by Country**| *(H3)*| Ensure payment processing setup serves donors effectively while also being efficient|

## Hypothesis and how to validate?

* The hypotheses that will be examined are as follows: 

|**Hypothesis**| **Description**|
|--------------|----------------|
|**H1**| Donors aged 50 - 65 give more per transaction than other age brackets |
|**H2**| The highest number of donations in the year will come in December |
| **H3**| Donors from the USA are more likely to donate with Cheques|

* They will be validated as follows:

|**Hypothesis**| **How to Validate**|
|--------------|----------------|
|**H1**| Plotly boxplot and Seaborn barplot to show median and mean donation values per donor age group|
|**H2**| Matplotlib line plot showing the trend of the number of donations per month |
|**H3**| Seaborn heatmap to analyse the relationship between country and payment method|

## Project Plan

* This project was divided into three separate sections: **Stage 1 - Anonymise**, **Stage 2 - ETL**, **Stage 3 - Visualisation**
* **Stage 1 - Anonymise**: The raw dataset was downloaded from Kaggle and saved as a CSV in a .gitignore folder. This data was then anonymised to ensure removal of all PII before the anonymised version was saved to the folder `datasets/anonymised-raw-data`. The anonymised dataset can be viewed in the repository for this project.
* **Stage 2 - ETL**: The data was inspected to ensure no duplicates or incorrect datatypes. Necessary cleaning was completed alongside some exploratory data analysis, before a cleaned version of the dataset was saved to the folder `datasets/cleaned-data`. This, too, can be viewed in the repository for this project.
* **Stage 3 - Visualisation**: Three hypotheses were analysed using data visualisation techniques to explore the hypotheses, ultimately supporting or disproving them.

## The rationale to map the business requirements to the Data Visualisations

|**Business Requirement**| **Data Visualisations** | **Rationale**|
|---|------|
|**Donation Amount by Age Group**| Plotly boxplot, Seaborn|The boxplot showed the distribution and the median values per age group, the bar plot very easily demonstrates which age group had the highest mean value donation amount|
|**Monthly Donation Patterns**| Matplotlib line graph |Good tool when analysing trends over a continuous period of time|
|**Payment Method by Country**| Seaborn heatmap | Easy to spot when combinations are the most common|


## Analysis techniques used

* **Stage 1 - Anonymisation**
    * Applied hashing and salting to donor IDs to protect personally identifiable information.
    * Rationale for doing this first was to separate the process from other steps in ETL, ensuring the sensitive data was kept separate and never committed alongside the working dataset.

* **Stage 2 - ETL**
    * I cleaned and fixed inconsistent categories.
    * Extracted new feature columns, `donation_year` and `donation_month` from a datetime column.
    * Created new labels for donation amounts by applying a function with if/elif/else statements and creating a new `donation_amount_category` column.
    * I also practiced using OneHotEncoder to encode categorical columns `gender` and `donation_type`.

* **Stage 3 - Visualisation**
    * Investigated hypotheses using a range of visualisation libraries: Matplotlib, Seaborn and Plotly.
    * I used descriptive statistics like mean, median, `groupby()` to find the right data to be used in visualisations and analyse hypotheses.
    * Applied crosstabulation (`pd.crosstab) to examine relationships between categorical variables.

## How did you use generative AI tools to help with ideation, design thinking and code optimisation?
* I very much wanted to solidify what I'd learned myself when completing this project, so treated AI as an "assistant" to support specific troubleshooting issues or processes I was unfamiliar with. Examples of when I did this are outlined in my project under *"Toubleshoot Issues"* and *"Notes on Process"*.
* I did find CopPilot's in-line AI support unhelpful at times, because it tended to confuse the code and made it harder for me to visualise what I needed to write. However, I did find it useful in certain instances:
    * I copied a DataFrame and gave it a new name, requiring me to go through old code cells to ensure I had changed all the names. CoPilot's in-line assistance with identifying all the occasions with the old name were very useful.
    * I used the inline suggestion when using `os.getenv` in **Stage 1 - Anonymise**

## Ethical considerations

* This data, whilst synthetic, contains **PII (Personally Identifiable Information)**.
* In our course, we have not yet learned about ethical considerations when working with data, or what is best practice when it comes to dealing with PII in raw datasets.
* However, I wanted the opportunity to practice new skills (for instance, learning about **salting** and **hashing**) and to deliver anonymised donor IDs for this project.
* In this project, I will treat this sensitive data as though not synthetic and implement best practices when handling it (to the best of my ability at this stage of the course).

## Development Roadmap

* I identified some clear areas that I am looking forward to improving on as the course continues:
    * Data Anonymising - I look forward to learning best practice when it comes to handling sensitive PII data.
    * Selecting the appropriate visualisation - with more practice, I hope to be able to better identify which visualisation will be best for a specific analysis.

## Main Data Analysis Libraries

* The main data analysis libraries used were:
    * pandas
    * numpy
    * matplotlib
    * seaborn
    * plotly.express
    * hashlib
    * python-dotenv
    * feature_engine.encoding
    * sklearn.pipeline
    * os

## Credits

* In all sections, I have included Markdown cells entitled *"Toubleshoot Issues"* and *"Notes on Process"*: in cases where I have used blogposts/ articles, official documentation or generative AI to support me in troublshooting issues or in asissting me to complete a process I might not have seen before, I have also included references to this within the notebooks themselves in these cells.

### Section 1 - Anonymise
* This section required a lot of research on my part to discover how best to anonymise data, given that we had not yet learned about this in our course.
* The sources I used for assistance in this section:
    * Medium.com - [Pandas Move Column to Front](https://medium.com/@amit25173/pandas-move-column-to-front-3-simple-steps-to-organize-your-dataframe-99bf1f2d39aa)
    * Medium.com - [Anonymise Sensitive Data in a Pandas DataFrame Column with hashlib](https://medium.com/data-science/anonymise-sensitive-data-in-a-pandas-dataframe-column-with-hashlib-8e7ef397d91f)
    * Medium.com - [Create my project structure](https://saurabh-sawhney.medium.com/create-my-project-structure-please-aa8ed9b98c7f) - This gave me the correct characters to use (**│**, **├──**, and **└──**) to be able to correctly outline my folder structure and to ask generative AI tools where the .env should be placed in my project.
* I also used Claude (Sonnet 5, Anthropic) generative AI to assist in the structure of my project - particularly in the context of the creation of a `.env` file and where that should sit in the folder/file hierarchy.
* I used **Microsoft Copilot's inline suggestions** to support me in writing the lines of code with `os.getenv`, having not worked with it previously.

### Section 2 - ETL
* For the **Extract** section, I need to give credit to Rory (Code Institute), who gave us the acronym **D**-**I**-**S**-**H** to help with remembering processes.
* I consulted Claude (Sonnet 5, Anthropic) generative AI to find `pd.Categorical` and the `.set_xticks()` function.
* The Code Institute LMS examples were extremely helpful, especially when completing the OneHotEncoder section.

### Section 3 - Visualisation
* The sources I used for assistance in this section:
    * Stack Overflow - [Changing the tick frequency](https://stackoverflow.com/questions/12608788/changing-the-tick-frequency-on-the-x-or-y-axis)
    * Stack Overflow - [Convert pandas Series to DataFrame](https://stackoverflow.com/questions/26097916/convert-pandas-series-to-dataframe)
* Thank you to Vasi (Code Institute) for confirming that I needed to use `pd.crosstab` to compare categorial data in a heatmap.
* The Code Institute LMS examples were extremely helpful when plotting data visualisations - with more practice, the code will become more second-nature.

### Media
* The image used in this README.md is from Code Institute

## Acknowledgements (optional)

* Thank you to everyone from the Code Institute team who have been instrumental in my learning up to this point - Vasi, Rory, Mike and Niel.
* Thanks to my great cohort! 