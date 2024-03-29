#TASK-1

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

#Determine the top three most common cuisines in the dataset:

df=pd.read_csv("C:\\Users\\swathiga\\OneDrive\\Desktop\\Dataset .csv")

cuisine_counts = df['Cuisines'].str.split(', ').explode().value_counts()
top_three_cuisines = cuisine_counts.head(3)
print("Top three most common cuisines:")
print(top_three_cuisines)

#Calculate the percentage of restaurants that serve each of the top cuisines:

total_restaurants=len(df)
percentage_of_restaurants= (top_three_cuisines/total_restaurants)*100
print("Percentage of restaurants that serve each of the top cuisines:")
print(percentage_of_restaurants)

#TASK-2

#Identify the city with the highest number of restaurants in the dataset:

city_counts=df['City'].value_counts()
city_with_highest_counts=city_counts.idxmax()
highest_count = city_counts.max()
print(city_with_highest_counts)
print(highest_count)

#Calculate the average rating for restaurants in each city:

average_rating_per_city=df.groupby('City')['Aggregate rating'].mean()
print(average_rating_per_city)

#Determine the city with the highest average rating:

average_rating_per_city = df.groupby('City')['Aggregate rating'].mean()
city_with_highest_avg_rating = average_rating_per_city.idxmax()
highest_avg_rating = average_rating_per_city.max()
print("City with the highest average rating:", city_with_highest_avg_rating)
print("Highest average rating:", highest_avg_rating)

#TASK-3

#Create a histogram or bar chart to visualize the distribution of price ranges among the restaurants:

plt.figure(figsize=(8, 6))
plt.hist(df['Price range'], bins=[1, 2, 3, 4, 5, 6], edgecolor='black', alpha=0.7)
plt.title('Distribution of Price Ranges')
plt.xlabel('Price Range')
plt.ylabel('Frequency')
plt.xticks(range(1, 6))
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()

#TASK-4

#Calculate the percentage of restaurants in each price range category:

price_range_counts = df['Price range'].value_counts()
total_restaurants=len(df)
percentage_of_restaurants= (price_range_counts/total_restaurants)*100
print("Percentage of restaurants in each price range category:")
print(percentage_of_restaurants)

# Get the count of restaurants offering online delivery:

online_delivery_counts = df['Has Online delivery'].value_counts()

# Calculate the total number of restaurants:
total_restaurants = len(df)

# Calculate the percentage of restaurants that offer online delivery:

percentage_online_delivery = (online_delivery_counts['Yes'] / total_restaurants) * 100

print("Percentage of restaurants that offer online delivery:", percentage_online_delivery)
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset:

df = pd.read_csv("C:\\Users\\swathiga\\OneDrive\\Desktop\\Dataset .csv")

# Group the data based on the "Has Online delivery" column and calculate the mean of "Aggregate rating":

ratings_comparison = df.groupby('Has Online delivery')['Aggregate rating'].mean()

# Plotting the bar chart:

plt.figure(figsize=(8, 6))
ratings_comparison.plot(kind='bar', color=['pink', 'turquoise'])
plt.title('Average Ratings of Restaurants with and without Online Delivery')
plt.xlabel('Online Delivery')
plt.ylabel('Average Rating')
plt.xticks(rotation=0)
plt.show()
