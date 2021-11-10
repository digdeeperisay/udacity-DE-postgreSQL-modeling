Overview:

In this project, we are designing and implementing a data model in PostgreSQL to help Sparkify analyze the data collected on songs and user activity on their platform. There are two types of raw data in separate folders under the 'data' folder - log data (contains simulated details on session activity on the platform) and song data (contains information on songs and artists / meta data information). We can join these two datasets together with the help of a couple of columns. If you open the 'Exploring.ipynb' notebook, you can see how the tables are structured. 

We use Pandas/Python to read each file into a pandas dataframe and eventually load the data into our fact and dimension tables. Given the use case of analyzing song behavior and queries related to that, a star schema is well suited here. 

Explanation of the star schema:

We have 1 Fact table and 4 Dimension tables. 

- The Fact table is like our transactions table and called 'songplays' - who played what song when etc.
- The Dimension tables all join to this Fact table and we have the following tables - 'songs', 'artists', 'users', and 'time'

See below for exact structure of the Fact and Dimension tables

Fact Table

songplays - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

Dimension Tables

users - user_id, first_name, last_name, gender, level
songs - song_id, title, artist_id, year, duration
artists - artist_id, name, location, latitude, longitude
time - start_time, hour, day, week, month, year, weekday

Explanation of the files:

- sql_queries.py contains all the necessary SQL code to create, drop, and insert into our fact/dimension tabls. This script gets called into a few other files
- create_tables.py invokes the sql_queries.py code and connects to the Sparkify database/creates our tables
- test.ipynb helps us test the code to make sure our tables have the necessary records 
- etl.ipynb contains the code necessary to do the ETL (Extract, Transform, Load) work here - reads the JSON files, extracts the fields, transforms them as needed, and loads them into our star schema
- etl.py is like an extension of the etl.ipynb and helps loop through all the song/log data files
- exploring.ipynb is just a scratch notebook 
- data contains the raw data files

How to execute the .py and i.pynb files:

- The .py files are python files. Open the 'terminal' from the 'Launcher' and type 'python filename.py'
- The .ipynb notebooks are Jupyter notebooks and once opened, you can execute each cell from top to bottom

The individual notebooks contain the actual code used for implementation here.