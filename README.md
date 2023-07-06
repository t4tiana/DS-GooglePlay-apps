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
</br>
And then cleaned it by:
- deleting duplicate data
- removing special characters from the Installs and Price columns to ensure the data is purely numeric
- converting Installs and Price data types from object to float
</br>
# EDA performed
#### Most popular app categories



# Conclusions from analysis
# Next steps
