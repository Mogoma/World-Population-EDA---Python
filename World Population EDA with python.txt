
#Exploritory data analysis

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt 
import seaborn as sns

#reading in the csv file
df=pd.read_csv(r"C:\Users\User\Desktop\tutorials\Pandas tutorial\world_populations.csv")

#Change numbers from scientific notation to two decimal places
pd.set_option('display.float_format', lambda x: '%.2f' %x)

#quick calculations to describe the data at a glance
df.describe()

#sum of all null values
df.isnull().sum()

#No of unique values per column
df.nunique()

#top range of countries
df.sort_values(by="2022 Population", ascending=False).head()

#top 10
df.sort_values(by="2022 Population", ascending=False).head(10)

#correlation
df.corr(numeric_only=True)

#bringing in matplotlib to visualie data(heatmap to visualie the correlation)
sns.heatmap(df.corr(numeric_only=True), annot=True)
plt.rcParams['figure.figsize'] = (20,7)
plt.show()

#Continent growth rate
df.groupby('Continent').mean(numeric_only=True).sort_values(by="2022 Population", ascending=False)

#what is oceania, contained in
df[df['Continent'].str.contains("Oceania")]

#population per continent
df2 = df.groupby('Continent').mean(numeric_only=True).sort_values(by="2022 Population", ascending=False) 
df2.plot()

#transposing the array to compare population size per different decades
df2.transpose()
df3 = df2.transpose()
df3.plot()

df.boxplot()
#selecting only number values or columns with numbers only
df.dtypes
df.select_dtypes(include='number')

#now selecting objects only
df.select_dtypes(include='object') 