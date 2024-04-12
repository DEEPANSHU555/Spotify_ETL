# Spotify_ETL
This project automates song data extraction from Spotify API, transforms it with Spotipy, and loads it into AWS S3. AWS Lambda orchestrates ETL, enabling efficient music data management and processing. The goal is streamlined Spotify data handling using cloud-based automation.

In this project, we're using the Spotify API to make a new app that works with Spotify. We'll use a python library called Spotipy in Python to easily get information about songs from Spotify, like their album, artist, and title.

Next, we'll set up a new storage space on AWS called an S3 bucket. Inside this bucket, we'll make two folders: one for raw data and one for transformed data. In the raw data folder, we'll have two more folders: "to_processed," where we'll put the raw data, and "processed," where we'll store the transformed data. In the transformed data folder, there will be three more folders: one for artist data, one for album data, and one for song data. Each folder will contain the transformed data organized as tables.

Once we've set up everything, we'll need to write two special functions called Lambda functions. The first one, called "extract_lambda_function," will get the data from Spotify and put it in the "to_processed" folder as raw data. The second one, called "transformation_load_lambda_function," will take the raw data from the "to_processed" folder, transform it according to what the user wants, and save the transformed data into the "transformed_data" folder, organized into artist, album, and song folders. Additionally, this function will copy the transformed data into the "processed" folder within the raw data section and delete the files from the "to_processed" folder.

In the final step, we'll automate the whole process by setting up triggers. We'll add two triggers to make everything run smoothly. 

First, we'll set up a CloudWatch trigger. This trigger will activate the "extract_lambda_function" every day, ensuring that fresh data is regularly pulled from Spotify.

Secondly, we'll create another trigger. This one will activate the "transformation_load_lambda_function" whenever new data is added to the "to_processed" folder in our S3 bucket. This means that as soon as new raw data arrives, it will automatically undergo transformation and be moved to its respective folder in the "transformed_data" section, simplifying the entire process.
