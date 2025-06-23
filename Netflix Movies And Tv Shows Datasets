import pandas as pd

# Load the dataset 
df = pd.read_csv("C:/Users/LENOVO/Desktop/netflix_dataset.csv")
df.head(2)
df.tail(2)

# Removing duplicates
df_cleaned = df.drop_duplicates().copy()
df.describe()

# Missinng values
df_cleaned['director'] = df_cleaned['director'].fillna('Unknown')
df_cleaned['cast'] = df_cleaned['cast'].fillna('Unknown')
df_cleaned['country'] = df_cleaned['country'].fillna('Unknown')
df_cleaned['date_added'] = df_cleaned['date_added'].fillna('Unknown')
df_cleaned['rating'] = df_cleaned['rating'].fillna('Unknown')
df_cleaned = df_cleaned.dropna(subset=['duration'])
# Correcting date formats
df_cleaned['date_added'] = pd.to_datetime(df_cleaned['date_added'], errors='coerce')

# Inconsistent texts
df_cleaned['country'] = df_cleaned['country'].str.strip().str.title()
df_cleaned['rating'] = df_cleaned['rating'].str.strip().str.upper()

# Correcting mix formats of movies and tv shows
df_cleaned[['duration_int', 'duration_type']] = df_cleaned['duration'].str.extract(r'(\d+)\s*(\w+)')
df_cleaned['duration_int'] = pd.to_numeric(df_cleaned['duration_int'])

# Reset the index
df_cleaned = df_cleaned.reset_index(drop=True)
# Saved the cleaned dataset to an Excel file
df_cleaned.to_excel("netflix_dataset_cleaned.xlsx", index=False)

print("Dataset cleaned and saved successfully as 'netflix_dataset_cleaned.xlsx'")
