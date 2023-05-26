# Movie_Recomendation
Title: Movie Recommendation System Based on Movie Overviews 

##Introduction: The code provided implements a movie recommendation system based on the content of movie overviews using the TMDB movie metadata dataset. The goal is to recommend similar movies based on the similarity of their overviews.

Importing Libraries:
The necessary libraries are imported, including numpy, pandas, and os. These libraries are used for data manipulation, file handling, and other operations.

Exploring Kaggle Input Directory:
The code snippet walks through the Kaggle input directory (/kaggle/input) using the os.walk() function. It retrieves the names of all the files present in that directory and prints them.

Reading Dataset Files:
The code reads two CSV files, namely tmdb_5000_movies.csv and tmdb_5000_credits.csv, using the pd.read_csv() function. These files contain movie metadata, such as movie titles, overviews, and other relevant information. The assumption is that the code is running in the Kaggle environment, where the dataset files are located in the specified paths.

Processing Movie Overviews:
The code accesses the 'overview' column of the df_movies DataFrame, which contains textual descriptions of each movie's plot. This step is necessary to prepare the data for further analysis.

TF-IDF Vectorization:
A TfidfVectorizer object is created from the sklearn.feature_extraction.text module. The vectorizer is initialized with the parameter stop_words='english', which instructs it to ignore common English words during vectorization.

The 'overview' column in the df_movies DataFrame is then filled with empty strings ("") for any missing values using the fillna() function. The TfidfVectorizer is fitted on the 'overview' column of df_movies using the fit_transform() method. This step transforms the textual data into a TF-IDF matrix representation, capturing the importance of words in the movie overviews.

Computing Cosine Similarities:
The linear_kernel() function from the sklearn.metrics.pairwise module is used to compute the cosine similarity between each pair of vectors in the TF-IDF matrix. This results in a matrix of pairwise cosine similarities, representing the similarity between movie overviews.

Creating Index Mapping:
A Pandas Series named indices is created. It maps movie titles to their corresponding index in the df_movies DataFrame. This mapping is useful for retrieving movie recommendations later.

Defining Recommendation Function:
The get_recommendations() function is defined to provide movie recommendations based on a given movie title. Given a title, the function retrieves the index of the movie using the indices mapping. It then iterates over the cosine similarity scores for that movie's index and performs the following steps:

a. Sorts the similarity scores in descending order.
b. Selects the top similar movies (excluding the first entry, which is the movie itself) based on the sorted scores.
c. Retrieves the indices of the selected similar movies.
d. Prints the original titles of the recommended movies.

Conclusion:
The code implements a movie recommendation system based on movie overviews using the TMDB movie metadata dataset. By calculating cosine similarities between movie overviews, it suggests similar movies based on the user's input.
