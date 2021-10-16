Pandas is a great packages for tabular data processing.

This notebook aims at covering several best practices to wrangling data. 

Chaining technique is the highlight.



```python
#Chaining techniques
df_cleaned = (
    df
    #Drop column cabin due to high amount of null values
    .drop('Cabin', axis =1)
    #Drop null value at Embard column
    .dropna(subset = ["Embarked"])#Drop null values at cabin column
    #Change data types
    .astype({'Embarked': 'category',
            'Sex':'category'})
    #Fill Null values and create new feature
    .assign(Age = lambda df: df['Age'].fillna(df['Age'].median()),
            First_Name = lambda df: df['Name'].apply(lambda x: x.split(',')[0])
           )
             )

```

