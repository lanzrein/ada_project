# Title
An ecological study of the food industry 

# Abstract (150w approx)
As ecology grows a more important concern, populations need not only to focus on driving less or consuming less, but also on how they consume food. 
It is a known fact that consuming products derived from palm oil, or meat in general is much more damaging for the environment than growing your own vegetables. 
During this project, we aim to expose how to be more regarding towards the environment in our daily food consumption. 
We will use a dataset of the Open Food Facts Database and look into where the food comes and how much it has had to travel. Moreover, in our study, we will take note of what region and countries are leading when it comes to sustainable food and who should take lesson from them. 
The main goal is to investigate the world of food and understand what are the next steps that need to be taken to allow future generations to live in the same conditions as us. 
# Research questions
- What is the environmental impact of food products ? 
- Who are the worst and who are the best eco friendly consumers ? ( In terms of proximity of food the country eats for example )  
- Compute distance for food from their selling point to origin ( use geopy ) 
  - Look which category of food product travel more. (dry food, preprepared meal)
  - Look if ecological labels such as "Agriculture Biologique" are more aware to the distance travelled by food
- Look at the distance that mineral water in bottle travels
- See what food contains palm oil - is it on the rise ? 
- Is the carbon footprint only related to distance ? 
- Are the newly added product more eco-friendly ?  
- What countries produce more vegan-labelled products ? Is the frequence of those products increasing with time ?
  
# Dataset
We will use the Open Food Facts database. We will use mainly the tags such as ‘manufacturing\_places’ and ‘countries’. In addition, we will take help of ‘geopy’ to find the coordinate of those place and thus be able to compute the distances. 
Since our focus is more on the ecological aspect of food, we will not be using many of the nutritional facts.

# A list of internal milestones up until project milestone 2
We first need to extract the data relevant to our project. We will also need to clean up a lot of the data as there is a lot of values that are empty or not filled in yet. 

- 14th of November : Explore the dataset, clean it. 
- 21th of November : Extracting the values that will be relevant for this project, with those values create additional features ( such as distance to origin. ) 
- 24th of November : Produce statistics from the datasets that are relevant to our research questions. 
# Questions for TAs

- Is it fine to have a larger pannel of research questions and then as we progress in the progress remove less interesting ones and add new ones ? If they are relevant for the project.
- Is it fine to work on several codes/notebooks addressing the different questions, and then group the results and vizualisations ?

--------

# Milestone 2 checklist : 


**Part 1: Finding the information of interest to answer the different questions (handle data in its size, understand what is into the data, filtering)**

We have explored the data thoroughly in different files with names DataExploration. <a href="./DataExploration_JeV.ipynb"> here </a> and <a href="./data_exploration_johan.ipynb"> here </a>. The dataset is composed of 681602 different products. Each product is represented by 173 different features. We have noticed that they are many many missing values, not all the features are complete for a given product. This will impact negatively on our analysis as only a subset of the products can be used to answer the question. Those subsets will be obtained using filtering to keep only products that contain values for the features of interest.

First, we based ourselves on the features’ description given on the dataset website (https://static.openfoodfacts.org/data/data-fields.txt). Nevertheless, we observed that new columns were added. Also, several columns contain repetitive information but sometimes one column is more useful as it contains the English translation. For instance the label of the product are contain in three different features: 'labels', 'labels_tags' and 'labels_en'. In such cases, we will use 'labels_en' as the tags are translated in English and thus it avoids some language handling problems. More genrally, data exploration was useful to determine which are the different columns which will be useful to answer the different questions we had.

More precisely, here is the different filtering we done:
- For all question regarding distance calculations, we will use origins_tags, first_packaging_code_geo and/or manufacturing_places_tags as starting point. We mixed them in order to have more products (88001 in total). Then the arrival point is represented with the countries_en feature. (see DistanceCalculations.ipynb)

- For questions regarding a specific kind of product (water bottle for instance), we used the feature categories_en. We split the feature in order to obtain the different categories and then filter in order to obtain the index of the product with the category of interest. (see WaterBottle.ipynb)

-	For question regarding the evolution of a label of evolution of the use of palm oil, we focused on products which had information about palm oil. However we kept used all the products whend standardizing our data to have a more meaningful analysis. 

We also consider enriching our data:
- For distance calculation, once the starting and arrival point are computed, we used geopy to obtain their respective coordinate. This will allow us to compute easily the distance that the product has travelled. (DistanceCalculations.ipynb) 

- For the water bottle, we aimed to compute the distance between the source and the point where the bottle is sold. As the source is not always indicated, we have been trying to get the origin of articles where the information is missing. For the origin, we considered using requests and beautiful soup to get the origin of products on wikipedia. This however proved to be not very effective time wise and also precision wise. ( see VeryBeautifulSoupTest.ipynb )

Moreover, we already produce several pipelines which could be generalized and used on different categories of food product if we want to compare them in the future.

**Part 2: Update of our plan**

The question “What is the environmental impact of food products?” is more the general question that we want to answer given the dataset we have. Our study's main goal is to offer an analysis on our consumption habits and their daily impact on the environment. We thought of several ways to answer it: either by looking at the distance that the product is traveling, looking at the label, the carbon footprint given on the product.

We already face several problems and thought of ways to overcome them.

-	We also notice during the data exploration that the majority of the products in the database are French products. Thus, there is a large bias toward France depending the analysis that will be done. In order to avoid that bias, instead of simply counting the label per country we decided to use proportions.

-	For the distance computation we are currently facing some problem with the merge of the different instances used as starting point. And searching how to deal with multiple starting points. We are considering using multiple point as start positions to consider all cases: perhaps the origin of the product depends on the season, or multiple ingredient of a product may come from different countries. Therefore, all origin should be considered.

-	We wanted to study the carbon footprint and try to determine what it is related to (distance, bio,…). Once we filtered the product that contain information regarding carbon footprint, we observed that only 342 products have this information which is too little to draw any conclusion. 

**What next ?**

As the data are completed mainly with French product doing a comparison between countries is not that fair. Clearly, the dataset may not be big enough to be representatives of the other countries. Thus, we decided to base our analysis on French product, draws hypothesis and then try to find if similar behaviors are observed in others countries where we have data.

In this subset we will have an interest on products where we can compute the distance it has travelled. On those products we will do an in depth analysis and see what kind of food travels the most. With those information we can lead some hypothesis testing with regards to other countries. 

Our analysis will also use the labels, palm oil information already computed. We will use them in a correlation relation with the distance and see if there is any relation to the labels and/or palm oil usage. For example we expect to see articles with the label "Agriculture Biologique" to have travelled considerably less than other kind of articles. 



## Final milestone goals : 
- Compute distance for each article.
- Create a network graph that will show where the articles are from
- Compute a correlation between labels /distance, labels/palm oil
- Group articles by categories and do hypothesis testing to see if other countries have the same tendencies for distance
- Link distance and category of product
- Write report about our analysis
- Create a poster that visualize and ties everything up

## Questions for TA : 
- Is there a library that works like folium that allows to do network graphs ? 

---------------------------------------

# Milestone 3 checklist : 
# Report 
- The report was done in the 4-page double column PDF report. 
## Goals
- All the goals that we set fo our final milestone goal have been reached with the exception of the poster that will be done during the winter break as it needs to be done still. 
### Contribution list
- Nicolas Freundler : Vegan products study, Local rule analysis, PCA, ICA, neural net.
- Jennifer Veillard : Preprocessing of data, computing distance for products, dictionary to find translate the countries.
- Johan Lanzrein : Palm oil, ecological labels, origins of french products, origin by category study. 
- Each person was responsible to write the part of the report and produce visualization related to her/his part. 
