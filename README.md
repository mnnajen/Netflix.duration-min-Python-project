# Netflix.duration-min-Python-project
## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install pandas and matplotlib.

```bash
!pip install pandas 
!pip install matplotlib

# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt


# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv(r'C:\Users\DELL\Downloads\netflix_data.csv')
netflix_df

# Subset the DataFrame for type "Movie"
netflix_subset = netflix_df[netflix_df["type"] == "Movie"]
netflix_subset

# Select only the columns of interest
netflix_movies = netflix_subset[["title", "country", "genre", "release_year", "duration"]]
netflix_movies

#Filter for durations shorter than 60 minutes
short_movies = netflix_movies[netflix_movies.duration < 60]
short_movies

# Define an empty list
colors = []
# Iterate over rows of netflix_movies
for label, row in netflix_movies.iterrows() :
if row["genre"] == "Children" :
colors.append("black")
elif row["genre"] == "Documentaries" :
colors.append("blue")
elif row["genre"] == "Stand-Up":
colors.append("green")
else:
colors.append("red")
# Inspect the first 10 values in your list
colors[:10]

# Set the figure style and initialize a new figure
fig = plt.figure(figsize=(12, 8))
# Create a scatter plot of duration versus release_year
plt.scatter(netflix_movies.release_year, netflix_movies.duration, c=colors, alpha=0.9)
# Create a title and axis labels
plt.title('Movie Duration by Year of Release')
plt.xlabel('Release Year')
plt.ylabel('Duration (min)')
# Adding a grid to the plot
plt.grid(True, color='red')
plt.show()


