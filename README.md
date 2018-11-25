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

- That you can handle the data in its size.
<p>We have explored the data thoroughly in different files with names DataExploration.</p>
-  understand what’s into the data (formats, distributions, missing values, correlations, etc.).
<p> During the data exploration we have noticed that they are many many missing values. This will impact negatively on our analysis. However we can keep the values that exist and work with them. TODO HERE EXPLAIN DIFFERENT VALUES </p>
- considered ways to enrich, filter, transform the data according to your needs.
<p> We have worked towards getting the distance that the articles have travelled. (DistanceCalculations.ipynb) We also have been trying to get the origin of articles where the information is missing ( VeryBeautifulSoupTesting.ipynb )
</p>
- updated your plan in a reasonable way, reflecting your improved knowledge after data acquaintance.

<p> discuss how your data suits your project needs and discuss the methods you’re going to use, giving their essential mathematical details in the notebook. </p>

- your plan for analysis and communication is now reasonable and sound, potentially discussing alternatives to your choices that you considered but dropped.
