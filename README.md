# Replace missing value with mean if the % of missing value is less than 10%.
for i in (df.columns[df.isnull().mean() < 0.10]): 
  df[i].fillna(df.mean())
# Perform the mode imputation for a categorical data.
df.fillna(df.mode())
# Perform a KNNImputer to estimate the missing values.
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=2)
After_imputation = imputer.fit_transform(df._get_numeric_data())
# Drop the columns with more than 10% missing values and display the size.
for i in df.columns[df.isnull().mean() > 0.10]:
  df.drop(i, axis=1)
# Drop the rows with outlier Z-score value> 3 and display the size.
from scipy import stats
import numpy as np
temp = stats.zscore(df.select_dtypes(include=np.number))
temp = temp.dropna(axis=1)
# Rescale your data using min-max normalization for a numerical feature.
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
temp = df.select_dtypes(include=np.number)
normalized_data = scaler.fit_transform(temp)
print(normalized_data)
###########
#  Split the dataset into train and test sets.
from sklearn.model_selection import train_test_split
train_df, test_df = train_test_split(df, test_size=0.2, random_state=42)
#  check shape of training and test sets
print(train_df.shape, test_df.shape)
temp = df.select_dtypes(include=np.number)
temp.dropna(axis=1)
#  Perform scaling in the data using Standard Scalar
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
temp[df.select_dtypes(include=np.number).columns] = scaler.fit_transform(df.select_dtypes(include=np.number))
#  Calculate the % of missing values in a column.
for i in df.columns:
  print(i,(((df[i].isnull().sum())/len(df))*100))
#  Remove features with missing values (>20%)
for i in df.columns:
  if((((df[i].isnull().sum())/len(df))*100) > 20):
    df.drop(i, axis=1)
#  If the missing values is <20% ,do data imputation(mean/median)
for i in df.columns:
  if((((df[i].isnull().sum())/len(df))*100) < 20):
    df[i].fillna(df.mean())
# Remove the outliers.
df = df.reset_index(drop=True)
drop_indexes = []
for col in df.columns:
  if(df[col].dtype == "float64" or df[col].dtype == "int64"):
    mean = df[col].mean()
    std = df[col].std()
    for i in range(len(df)):
      val = df.loc[i,col]
      if( ((val-mean)/std) > 3.0):
        drop_indexes.append(i)
df.drop(drop_indexes,inplace=True)
# Use sklearn variancethreshold to find the constant features
from sklearn.preprocessing import OrdinalEncoder
from sklearn.feature_selection import VarianceThreshold
ord_enc = OrdinalEncoder()
df_ = ord_enc.fit_transform(df)
var_thr = VarianceThreshold(threshold = 0)
var_thr.fit(df_)
const_cols = list(pd.DataFrame(df_).columns[[not elem for elem in var_thr.get_support()]])
# Remove features with low variance
var_thr = VarianceThreshold(threshold = 0)
var_thr.fit(df_)
low_var_cols = list(pd.DataFrame(df_).columns[[not elem for elem in var_thr.get_support()]])
#  Remove highly correlated features
corr = temp.corr()
corr = corr.reset_index(drop=True)
drop_cols = []
for index,col in enumerate(temp.columns):
  if(index == 0):
    continue
  for i in range(index):
    if abs(corr.loc[i,col]) > 0.95:
      drop_cols.append(col)
      continue
#  Apply Pearson Correlation Coefficient/Spearman’s rank coefficient 
from seaborn import heatmap
corr = temp.corr(method='pearson')
heatmap(corr)
