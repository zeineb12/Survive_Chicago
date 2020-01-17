# How to Survive Eating Out in Chicago

The data story we made can be found [here](https://survive-eating-out-chicago.github.io/). The corresponding repository is https://github.com/survive-eating-out-chicago/survive-eating-out-chicago.github.io.

## Abstract
"Foodborne diseases are a major cause of illness and death in the United States." The US Centers for Disease Control and Prevention estimate that each year, there are 9.4 million reported cases of foodborne illness, resulting in 55,961 hospitalizations and 1,351 deaths.
[1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3204615/#R1)

In this project we use data from the Chicago Department of Public Health breaking down inspections of restaurants and other food establishments, with the goal of trying to better understand which factors are most at stake when talking about food safety.

In the process, we will also use socio-economic indicators of Chicago community areas in order to see if eating safely is equally accessible to every class and if our dataset supports the existence of "food deserts".
[4](https://www.chicagoreporter.com/food-deserts-persist-in-chicago-despite-more-supermarkets/)

Our ultimate aim will be to promote public health by providing a reliable recommendation system for eating out in Chicago, based on a "safety score" that we will compute using the information from inspections as well as other metrics that will prove useful during analysis. All of this is will showcase an example of the use of "data science for social good”.

## Research questions

### I. Do facility attributes influence food inspection outcomes for establishments in Chicago?

Our main dataset as well as our secondary datasets give us many attributes for each establishment such as facility type, risk, location and whether it is a chain or not [1](https://www.chicagotribune.com/business/ct-biz-mcdonalds-cyclospora-outbreak-20180719-story.html). Which of these attributes contributes the most to food inspection outcomes in Chicago?

### II. Chicago Food Deserts: an indicator of social segreggation?

Many articles seem to point to the fact that different areas in Chicago do not have equal access to healthy food [3](https://chicago.eater.com/2018/12/13/18138387/chicago-magazine-john-kessler-food-scene-racism-immigration-food) [4](https://www.chicagoreporter.com/food-deserts-persist-in-chicago-despite-more-supermarkets/). These articles claim that this is due to the persistence of racial segreggation. Our aim is to inspect this further and see whether our dataset could help in seeing if this is true.

### III. The survival guide: a personalized guide for eating out safely

This represent the conclusion to our findings. The aim is to display an interactive map with widgets where the user can choose parameters as: "Allergies friendly restaurants", "No food chains" and get restaurants displayed along with their safety scores.

## Datasets

#### Chicago Food Inspections Dataset
We chose the _Chicago Food Inspections_ dataset from the given datasets. It contains information about food inspections of different establishments in Chicago from January 1, 2010 to the present. We will use it as our main dataset for the project and it can be downloaded either as a JSON file _socrata\_metadata.json (9.14 KB)_  or a CSV file _food-inspections.csv (219.71 MB)_ from [5](https://www.kaggle.com/chicago/chicago-food-inspections) (In addition to that source, you can check for the main source dataset on Chicago Data Portal [6](https://data.cityofchicago.org/Health-Human-Services/Food-Inspections-Dashboard/2bnm-jnvb)). More information about the attributes in the Chicago Food Inspections' dataset can be found on [7](https://data.cityofchicago.org/api/assets/BAD5301B-681A-4202-9D25-51B2CAE672FF).

#### Socioeconomic & Health related datasets
In order to answer our second research question, we need a socioeconomic as well as health related indicator datasets.To that end, we will be using selected public health indicators for the different community areas. The dataset is available under this [link](https://data.cityofchicago.org/Health-Human-Services/Public-Health-Statistics-Selected-public-health-in/iqnk-2tcu) and contains measures related to infectious disease, lead poisoning, and economic status.

We will also need the total population by community area which we will merge with the latter. [source](https://www.chicagohealthatlas.org/indicators/total-population)

#### Community Areas boundaries
We need the community areas boundaries dataset for visualization purposes as well as to fill in missing values in our main dataset. The dataset is provided by the City of Chicago under this [link](https://www.chicago.gov/city/en/depts/doit/dataset/boundaries_-_communityareas.html) and is provided under different extensions. We will be using the .geojson file.

#### Fast Food Restaurants Across America
In order to work on chains specifically, we use [this dataset](https://www.kaggle.com/datafiniti/fast-food-restaurants) to get a list of chains that we join with our inspections dataset.

#### Ethnicities by community area
The count of people by different ethnicities present in the city of Chicago is available under this [link](https://www.chicagohealthatlas.org/indicators/non-hispanic-african-american-or-black).

For each ethnicity, we download the corresponding excel file and then merge those in a Pandas dataframe.

## APIs

#### Yelp Fusion
Yelp is a business directory service and crowd-sourced review forum. 
Alongside our main dataset, we will be using the Yelp Fusion API, [8](https://www.yelp.com/developers/documentation/v3). This is a collection of endpoints developers can reach to get information on establishment. It has been made available to use for personal, educational, and academic purposes. To support our research questions, we will be using:

- **Business Match Endpoint**: Lets us match business data from other sources against businesses on Yelp, based on provided business information. 
- **Business Details**: Given the id of any establishment obtained from the Business Match Endpoint, this returns details like price range, rating, and cuisine. 

## Resources
[1] https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3204615/#R1 <br/>
[2] https://www.chicagotribune.com/business/ct-biz-mcdonalds-cyclospora-outbreak-20180719-story.html <br/>
[3] https://chicago.eater.com/2018/12/13/18138387/chicago-magazine-john-kessler-food-scene-racism-immigration-food <br/>
[4] https://www.chicagoreporter.com/food-deserts-persist-in-chicago-despite-more-supermarkets/ <br/>
[5] https://www.kaggle.com/chicago/chicago-food-inspections <br/>
[6] https://data.cityofchicago.org/Health-Human-Services/Food-Inspections-Dashboard/2bnm-jnvb <br/>
[7] https://data.cityofchicago.org/api/assets/BAD5301B-681A-4202-9D25-51B2CAE672FF <br/>
[8] https://data.cityofchicago.org/Health-Human-Services/Public-Health-Statistics-Selected-public-health-in/iqnk-2tcu <br/>
[9] https://www.yelp.com/developers/documentation/v3 <br/>
[10] https://www.kaggle.com/datafiniti/fast-food-restaurants <br/>
[11] https://www.chicago.gov/city/en/depts/doit/dataset/boundaries_-_communityareas.html <br/>
[12] https://data.cityofchicago.org/Health-Human-Services/Public-Health-Statistics-Selected-public-health-in/iqnk-2tcu <br/>
[13] https://www.chicagohealthatlas.org/indicators/total-population <br/>
