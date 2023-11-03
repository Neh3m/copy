import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
path = "drive/My Drive/Lab/Sem_6 LAB/ML/Data/Toyato.csv"
df = pd.read_csv(path)

# First 5
df.head(5)
df.tail(5)

# no.of rows and columns
df.shape()

# no of categorical and numberical columns
df._get_numeric_data().count()
df_ = df[df.isin(df._get_numeric_data()) == False]
df_.count()

# For numerical columns, display the min, max and mean
df.describe()

# Display the columns with null values
df.isnull().sum()

# Calculate the 5 number summary for “age” column and correlate with box plot
print(df['Age'].mean())
print(df['Age'].min())
print(df['Age'].max())
def get_percentile(df, percentile_rank):
    df = df.sort_values(by='Age').reset_index()
    index = (len(df.index)-1) * percentile_rank / 100.0
    index = int(index)
    return df.at[index, 'Age']
print(get_percentile(df, 25))
print(get_percentile(df, 75))

plt.boxplot(df['Age']);

# Find the correlation for the input features Age, Price, Quarterly_Tax, Weight
import seaborn as sea
sea.heatmap(df[['Age', 'Price', 'Quarterly_Tax', 'Weight']].corr());

# Display the feature pairs with high positive correlation and high negative correlation values for the given input features
c = df.select_dtypes(include=np.number).corr().abs()
c = c.unstack().sort_values()
print(c)

# Display the feature pairs that have correlation value greater than 70% for the given input features
c = df.select_dtypes(include=np.number).corr().abs()
c = c.unstack().sort_values()
print(c > 7)

# Analyze the skewness of the feature using plot distribution graph for the “cc” column and display whether the feature is right skew, left skew or no skew
df.cc.value_counts().plot(kind='bar', figsize=(10,5));

# Perform univariate analysis for categorical variable “Fuel_Type” using bar plot with counts of observations.
plt.bar(df['Fuel_Type'], df.index)

# Perform univariate analysis for continuous variable “Age” using swarm plot and violin plot
sea.swarmplot(df['Age'])
sea.violinplot(df["Age"])

# Display the scatter plot to show the relationship between two continuous variables “Age” and “Price”
plt.scatter(df['Age'], df['Price'])

# Perform a bivariate analysis between categorical variable and continuous variable of “Fuel_Type” and “Age” using categorical box plot
sea.catplot(x='Fuel_Type', y='Age', data=df, kind='box')

# Perform a multivariate analysis between input features “Age”, “Price”, “KM”, “Weight” using pair plot with respect to Fuel_Type as hue.
pd.plotting.scatter_matrix(df[['Age', 'Price', 'KM', 'Weight']], diagonal="kde",figsize=(20,15))

1b
# Calculate the % of missing values in a column.
(df.isnull().sum()/len(df))*100

# Replace missing value with mean if the % of missing value is less than 10%.
for i in (df.columns[df.isnull().mean() < 0.10]): 
  df[i].fillna(df.mean())

# Perform the mode imputation for a categorical data.
df.fillna(df.mode())

EP2 
#  Split the dataset into train and test sets.
from sklearn.model_selection import train_test_split
train_df, test_df = train_test_split(df, test_size=0.2, random_state=42

#  check shape of training and test sets
print(train_df.shape, test_df.shape)
