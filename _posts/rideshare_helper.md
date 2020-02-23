---
layout: post
title: Uber Surge Predicted with Machine Learning
---

For starters, here's a [Youtube video](https://youtu.be/M016woop34c), or you can just read below if that's more your speed.

# Rideshare Helper
What can rideshare drivers in Chicago do to earn more money?  
Here's a new thing: They can use this data science project with its machine learning model which predicts when and where high demand pricing will occur.  
High demand pricing goes by different names at different companies: At Uber, it is called Surge Pricing, at Lyft, it's called Prime Time Pricing.  
For this project, I used data from the city of Chicago: A dataset of [rideshare trips](https://data.cityofchicago.org/Transportation/Transportation-Network-Providers-Trips/m6dm-c72p), a data set of [per capita income](https://data.cityofchicago.org/Health-Human-Services/Per-Capita-Income/r6ad-wvtk), among other health factors, and data set with geographical outlines for the 77 [community areas](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Community-Areas-current-/cauq-8yn6) in Chicago. The rideshare dataset contained about 129 million trips over a bit more than a year, but I focused on one arbitrarily selected day to do my analysis. This greatly simplified things and allowed me to run the model on my laptop.  
The techniques used were Linear Regression for feature engineering and Random Forest Classification to predict whether a given trip will be under surge pricing.  
The Random Forest Classifier Model performed passably well: It had 25% precision, although the recall was quite low. However, this is adequate for my use case: If I can tell drivers "go to this place at this time and you've got a 25% chance of catching a surge," I think that's valuable.  
The model also identified important features: proximity to the loop, per capita income in the community area where the trip starts, and whether the trip starts between 4 pm and 8 pm. In other words, high demand pricing is more likely to occur downtown.
This is a nice sanity check to ensure the model makes sense.  
Below, you can see some visualizations of the model's predictions. There are also live, interactive visualization [here](https://public.tableau.com/profile/erik.kristofer.anderson#!/vizhome/RideshareHighDemandPricingPredictions/predict_morn_eve?publish=yes) and [here](https://public.tableau.com/profile/erik.kristofer.anderson#!/vizhome/RideshareHighDemandPricingPredictions/true_and_pred_dashboard?publish=yes).  
The jupyter notebooks contain most of the code and the detailed analysis. Most everything can be found [on Github][(https://github.com/ekand/rideshare_helper).  
For those of you who are interested, the organization of the project is as follows:  
```
------------
.
├── data              -----> contains various data files, organized and excluded from version control 
│   ├── external
│   ├── interim
│   ├── pickles
│   ├── processed
│   └── raw
├── docs             -----> documentation (currently empty)
├── models           -----> pickled models
├── notebooks        -----> jupyter notebooks with main code and explanation
├── references       -----> external reference, if needed
├── reports          -----> presentation files
│   ├── external_images
│   ├── figures
│   └── videos
└── src               -----> Python scripts, packaged as modules and imported using `pip install -e .`
    ├── data_prep
    ├── features
    ├── models
    ├── pickle
    ├── surge
    └── visualization
--------
```
This project was based on the cookiecutter data science project template.
" https://drivendata.github.io/cookiecutter-data-science/"
#cookiecutterdatascience
I hope you enjoyed reading this and please post below if you have questions (or if you just liked it, or even if you didn't; I just love comments).


---

Originally published at https://dev.to on February 12, 2020.
