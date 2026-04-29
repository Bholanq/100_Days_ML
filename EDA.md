Exploratory Data Analysis 
1. How big is the data? `df.shape`
2. How does the data look like? `df.head(), df.sample(5) - random rows`
3. What is the data types of the cols? `df.info()`
4. Are there any missing values? `df.isnull().sum()` - counts the missing values
5. How does the data look mathematically? `df.describe()`
6. Are there duplicate Values? `df.duplicated().sum()`- count the no of duplicate rows 
7. Correlation between cols? - not all cols are useful - `df.corr() - pearsons corr coeff`

[[Univariate Analysis]]
[[Bivariate]] 
[[Multivariate]] 
