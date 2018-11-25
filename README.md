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



# Milestone 2 checklist : 


- updated your plan in a reasonable way, reflecting your improved knowledge after data acquaintance.

<p> discuss how your data suits your project needs and discuss the methods you’re going to use, giving their essential mathematical details in the notebook. </p>

- your plan for analysis and communication is now reasonable and sound, potentially discussing alternatives to your choices that you considered but dropped.

--------

**Part 1: Finding the information of interest to answer the different questions (handle data in its size, understand what is into the data, filtering)**

We have explored the data thoroughly in different files with names DataExploration. <a href="./DataExploration_JeV.ipynb"> here </a> and <a href="./data_exploration_johan.ipynb"> here </a>. The dataset is composed of 681602 different products. Each product is represented by 173 different features. We have noticed that they are many many missing values, not all the features are complete for a given product. This will impact negatively on our analysis as only a subset of the products can be used to answer the question. Those subsets will be obtained using filtering to keep only products that contain values for the features of interest.

First, we based ourselves on the features’ description given on the dataset website (https://static.openfoodfacts.org/data/data-fields.txt). Nevertheless, we observed that new columns were added. Also, several columns contain repetitive information but sometimes one column is more useful as it contains the English translation. For instance the label of the product are contain in three different features: 'labels', 'labels_tags' and 'labels_en'. In such cases, we will use 'labels_en' as the tags are translated in English and thus it avoids some language handling problems. More genrally, data exploration was useful to determine which are the different columns which will be useful to answer the different questions we had.

More precisely, here is the different filtering we done:
- For all question regarding distance calculations, we will use origins_tags, first_packaging_code_geo and/or manufacturing_places_tags as starting point. We mixed them in order to have more products (88001 in total). Then the arrival point is represented with the countries_en feature. (see DistanceCalculations.ipynb)

- For questions regarding a specific kind of product (water bottle for instance), we used the feature categories_en. We split the feature in order to obtain the different categories and then filter in order to obtain the index of the product with the category of interest. (see WaterBottle.ipynb)

-	For question regarding the evolution of a label of evolution of the use of palm oil, we focused on products which had information about palm oil. However we kept used all the products whend standardizing our data to have a more meaningful analysis. 

We also consider enriching our data:
- For distance calculation, once the starting and arrival point are computed, we used geopy to obtain their respective coordinate. This will allow us to compute easily the distance that the product has travelled. (DistanceCalculations.ipynb) 

- For the water bottle, we aimed to compute the distance between the source and the point where the bottle is sold. As the source is not always indicated, we have been trying to get the origin of articles where the information is missing (VeryBeautifulSoupTesting.ipynb ). 

- For the origin, we considered using requests and beautiful soup to get the origin of products on wikipedia. This however proved to be not very effective time wise and also precision wise. ( see VeryBeautifulSoupTest.ipynb )

Moreover, we already produce several pipelines which could be generalized and used on different categories of food product if we want to compare them in the future.

**Part 2: Update of our plan**

The question “What is the environmental impact of food products?” is more the general question that we want to answer given the dataset we have. Our study's main goal is to offer an analysis on our consumption habits and their daily impact on the environment. We thought of several ways to answer it: either by looking at the distance that the product is traveling, looking at the label, the carbon footprint given on the product.

We already face several problems and thought of ways to overcome them.
-	We wanted to study the carbon footprint and try to determine what it is related to (distance, bio,…). Once we filtered the product that contain information regarding carbon footprint, we observed that only 342 products have this information which is too little to draw any conclusion. 
Moreover, the dataset is fairly sparse with many holes and nan values. Concerning this we will try to address the issues in the following way : 


For the rest of the project, we will focus more on the distance the products travelled and use a formula to estimate how much pollution this generates. Then we will verify how this extra information relates to our already computed information about each country. 

In the end, we would be interested in doing a sort of ecological competition between each country. This would be done by allocating points to each country based on how ecological they are on each categories. In the end we would have a leaderboard of the countries and this would give some insights on how good the countries are at being ecological. 



## Final milestone goals : 
- Compute a fair equation to express the carbon footprint of the food. 
- Create a graph that will show who imports and who exports
- ???


## Questions for TA : 
- Is there a library that works like folium that allows to do network graphs ? 