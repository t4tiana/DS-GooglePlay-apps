# Purpose
In order to demonstrate my abilities in data cleaning and EDA, I downloaded the [Google Play Store Apps Dataset from Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps) and used Jupyter Lab to run a series of analyses.
</br>
# How I selected the dataset
While there are many public datasets available for the Apple App Store, there aren't as many for the Google Play Store and I thought it would be interesting to explore this data since I am an Android user. The publisher of the dataset said it wasn't easy to scrape data from the Google Play Store, so I guessed there would be ample opportunity to get meaningful practice in cleaning the data before using it.</br>
# Steps taken to clean and preprocess the dataset </br>
Before the data was loaded, I took a look at it in Excel to see if there were any obvious issues that needed to be addressed first. One row was missing data in one of its columns, so every other column's data had been shifted by one cell. This put a float value in a column that would otherwie be classed as an object, but since I didn't know the value of the missing cell I deleted the row altogether.
</br></br>
Once the data was imported from Hugging Face, I preprocessed it by:
- loading necessary libraries (Pandas, NumPy)
- checking the datatypes of the different columns
- removing unneeded columns
<br>

And then cleaned it by:
- deleting duplicate data
- removing special characters from the Installs and Price columns to ensure the data is purely numeric
- converting Installs and Price data types from object to float<br>

# EDA performed
### Most popular app categories
<br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/0af86303-71bd-49ac-afed-5ac561da6977" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/0af86303-71bd-49ac-afed-5ac561da6977)
<br>

### Average app ratings
<br>
We see that the histogram is skewed to the left, meaning that the majority of apps are rated highly.<br> However, with 1465 out of 10358 apps (14.1%) of apps missing a rating, we cannot be certain that the mean rating is actually 4.2
<br><br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/d03f364b-7c77-4508-aaf6-a572d98cf414" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/d03f364b-7c77-4508-aaf6-a572d98cf414)
<br>

### App Size and Price
<br>
App developers may be interested to know whether or not the size of an app influences how many people will download it. Consumers with older phone models may forgo downloading an app if it takes up too much of their phone's finite storage.
<br><br>
By also looking at the price of apps on the Google App Store, a developer could answer these questions:
<br>

- Does the size of an app affect its rating?
- Do users prefer small-sized apps?
- Does the price of an app affect its rating?
- Do users always prefer free apps over paid apps?
- How can we effectively come up with strategies to size and price our app?

#### Rating vs App Size
<br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/36ba7357-40a6-4fed-a137-29110797310b" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/36ba7357-40a6-4fed-a137-29110797310b)

#### Rating vs App Price
<br>
We find that the majority of top-rated apps (rated 4+) are under 20 MB. We also find that the vast majority of apps price themselves under $10.
<br><br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/1c382f3c-618a-4696-a155-fda46ac87a62" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/1c382f3c-618a-4696-a155-fda46ac87a62)
<br>

### App prices by Category
<br>

Companies not only want to cover the cost of developing and maintaining their apps, but also generate profit. Strategies could include offering the app for free but including ads, or having in-app purchases. If an app has a paid download, companies should balance maximum perceived value with going market rates for similar apps, which is possible by looking at data of app prices by Category. <br>

**Medical** and **Family** apps are the most expensive. This could mean that customers perceive the value of these apps to be higher than apps in other categories.<br> All **Game** apps are priced below $20, which a company should take into consideraion when developing a pricing strategy for their new gaming app.
<br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/2781b710-43a2-447c-9ac9-7bec31cf12b9" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/2781b710-43a2-447c-9ac9-7bec31cf12b9)
<br>

### Excluding outliers: Apps priced over US $100
<br>

Some apps are priced high but don't seem to serve a purpose (*I'm Rich*, *most expensive app*, *I am Rich Plus*, etc.)
Excluding these apps from the strip plot can provide a more useful visualization for someone who wants to understand the pricing of apps in each category. <br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/31a585f3-64cd-4f02-a257-a0903581d42a" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/31a585f3-64cd-4f02-a257-a0903581d42a)
<br>

### Number of installs: Free vs Paid Apps
<br>

According to Google AdMob there are [5 monetization strategies for apps](https://admob.google.com/home/resources/5-app-monetization-strategies-to-grow-and-monetize-your-app/), 3 of which involve offering a free download.<br>
In the original dataset, apps that are categorized as **Paid**:
- Require the customer to pay in order to download the app
- Don't allow the customer to try the app before they buy it
<br>

This is a pretty big commitment. **Does it result in fewer installs?**
<br>

Of the 10,358 apps that have been analyzed in this dataset, 76.5% are Free to download.<br>
One may think that this would result in Paid apps being installed much less frequently, but this box plot shows **this is not the case.**
<br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/ba3afb50-07cd-4fe8-b70a-15cbe45b8f4d" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/ba3afb50-07cd-4fe8-b70a-15cbe45b8f4d)
<br>

### Sentiment Analysis of user review data
<br>

By plotting sentiment polarity scores of user reviews for paid and free apps, we observe the following:<br>
- Free apps receive more harsh comments, as indicated by the outliers on the negative y-axis.
- Reviews for paid apps appear never to be extremely negative. This may indicate something about app quality, i.e., paid apps being of higher quality than free apps on average.
- The median polarity score for paid apps is a little higher than free apps, in congruence with the previous observation.
<br>

[<img src="https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/27825d5a-4b61-45dc-8605-d7feff87516f" width="800"/>](https://github.com/t4tiana/EDA-GooglePlay-apps/assets/118233338/27825d5a-4b61-45dc-8605-d7feff87516f)

<br>

# Conclusions from analysis
Companies looking to develop apps for download in the Google Play Store could use this analysis to inform their decisions around what category of app to create, what size to make it, and how to price it.<br>

# Next steps
With additional data on **when** downloads were taking place, linear regression and time series analysis could be used to look at potential seasonality and forecast downloads at different points of the year. It would be interesting to test the hypothesis that Paid apps are more likely to get downloaded at certain times of the year, like paid fitness apps being more frequently downloaded in January after people have made their New Years resolutions. This could help companies decide when to offer promotions or release new features to encourage more downloads.
