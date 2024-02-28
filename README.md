# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
# data-cleaning
```import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="626" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/97722de6-05b1-420c-a955-8b8129d28121">

```
df.head(10)
```
<img width="434" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/68d55a52-2f11-45b7-89be-269204208ff5">

```
df.tail(10)
```
<img width="462" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/c23285b0-fc42-45f1-904c-d8f8ae79bfb1">

```
df.info
```

<img width="392" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/0b844bad-ee65-4667-b765-6bf6d83a1004">

```
df.describe()
```

<img width="528" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/ce2cfb39-b838-498e-a8ba-297412756584">

```
df.shape
```

<img width="74" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/60f426ff-96ad-457d-ad55-fbdbcc091db8">

```
df.nunique()
```

<img width="235" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/aae0bc9b-46c3-4ed7-bc24-c9bff6e5d28b">

```
df['GENDER'].value_counts()
```

<img width="156" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/523afb48-2acf-4fca-b503-c1b35947a2a1">

```
mn=df.TOTAL.mean()
```

<img width="174" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/832735c8-a21b-4fe6-8ed4-b932ff886038">

```
df.TOTAL.fillna(mn,inplace=True)
df.M4.fillna(mn,inplace=True)
df.isnull()
df
```

<img width="538" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/f85735cd-2c1c-4f91-838a-25db75ed203e">

```
df['cd']=pd.to_datetime(df['DOB'])
df['cd']
```

<img width="175" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/af175242-8154-4c4d-8c95-231078b71a91">

```
df
```

<img width="675" alt="image" src="https://github.com/Jeevapriya14/data-cleaning/assets/121003043/16e9cd23-469e-4552-be60-2b0bf539fe4d">

# outliers
```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

<img width="199" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/8f16c272-c5c8-4d99-87c5-67b2e8317f3b">

```
sns.boxplot(data=af)
```

<img width="331" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/e33c5787-17f3-4eb9-9ab4-d1c417c84c9d">

```
sns.scatterplot(data=af)
```

<img width="420" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/e74150c6-744a-4526-a99a-41e20f844b32">

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```

<img width="80" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/162037a7-d24e-40fa-9b9d-94f231cc64b3">

```
low=q1-1.5*iqr
low
```

<img width="88" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/4eb0c2c0-ec8f-45f9-a220-1492df6da1b3">

```
high=q3+1.5*iqr
high
```

<img width="96" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/48213a8a-6851-4236-a71a-aed5a7e688ff">

```
af=af[((af>=low)&(af<=high))]
af
```

<img width="152" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/d7152c2f-03dd-4a6c-bbd3-f8b20029dac4">

```
af.dropna()
```

<img width="116" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/fd1a33de-45ef-4c29-8dab-76c45cded230">

```
sns.boxplot(data=af)
```

<img width="319" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/245eadda-7184-4224-ba33-02562d399bcf">

```
data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
df
```

<img width="92" alt="image" src="https://github.com/Jeevapriya14/outliers/assets/121003043/5301b7b2-4d45-4de9-8325-977728782e28">

# Result:
Thus,The output has been successfully verified!
