# nosql-challenge
Module 12 Challenge


# Part 1: Database and Jupyter Notebook Set Up

I imported provided  data `establishments.json` file from a Terminal using `$ mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`. The database was named `uk_food` and the collection `establishments`.

Within Jupyter Noteboook : NoSQL_setup_starter.ipynb, libraries PyMongo and Pretty Print were imported and an instance of the Mongo Client was installed.

Confirmation that the database was created was tested by printing all the database names from mongo and seeing new database uk_food listed in the output.  From the database uk_food, a list of collection names was printed to ensure establishments was available.  An example of a document was printed using pretty print. Selecting the document was done using find_one. 


# Part 2: Update the Database

Still within NoSQL_setup_starter.ipynb, a new restaurant called "Penang Flavours" was added to the uk_food database.

A new restaurant called Penang Flavours was added to the database by creating a a dictionary with the data provided using insert_one.  Confirmation of this insert was done by printing the object pwhere the Business name was Penang Flavours.The data for this new restaurant did not have the Business Type ID populated.  I ran a query to return all the results of  Business Type ID for other businesses with a Business type of 'Restaurant/Cafe/Canteen' (matching the new restaurant).  I then updated the found result of 1 to the Penang Flavours data using $set.
A print of the object id confirmed the Business Type ID was now populated.

The magazine is not interested in any establishments in Dover, so I checked how many documents contain the Dover Local Authority using count and printing the result. I removed all establishments within the Dover Local Authority from the database using delete_many and recounted to check they were deleted.

Some of the number values are stored as strings, when they should be stored as numbers. I used update_many to convert latitude and longitude to decimal numbers.  To check that these values were all updated, I created 2 counts - a float_count & a non_float_count.  I looped through the documents and counted if the "longitude" or "latitude" values are of type float or int.  If they were of type float or int, the float_count was incremented, if not, the non_float_count was incremented.  The results were printed.

The Rating_value also needed to be amended to an integer.  This field has non-numeric values that I first set to 'Null' and then set the field to an integer type using update_many.  I then checked that these values are now numbers by iterating through the documents to see if thr RatingValue field exisits and if it does, print the type which will be int or float for a number.  


# Part 3: Exploratory Analysis

NoSQL_analysis_starter.ipynb : libraries PyMongo, Pretty Print and Pandas were imported and an instance of the Mongo Client was installed. 
There were specific questions asked and the following database exploration was performed to find the results.

Question 1: Which establishments have a hygiene score equal to 20?
A query was used to find the number of establishments with w hygiene score of exactly 20.  I used count_documents to calculate the answer of 41 and displayed the first document in ths results using pretty print.
The results were then converted to a Pandas dataframe and the first 10 rows were displayed.

Question 2: Which establishments in London have a RatingValue greater than or equal to 4? 
A query was used to find the establishments with London in the Locaal Authority name (using $regex) as well as a RatingValue greather than or equal to 4 (using $gte).  I used count_documents to calculate the answer of 33 and displayed the first document in ths results using pretty print.
The results were then converted to a Pandas dataframe and the first 10 rows were displayed.

Question 3: What are the top 5 establishments with a RatingValue of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
Using pretty print, I found the latitude & longitude of Penang Flavours.
A query was used to find the establishments with a RatingValue equal to 5 as well as longitude and latitude of up to 0.01 degree less than or greater than the Penange Flavours longitude and latitude.  The results were then sorted in ascending order of the Hygiene score and limited to the top 5.
The results were then converted to a Pandas dataframe and the 5 rows were all displayed.

Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas. 
An aggregation pipeline was built to include a match query, group, and sort.  The match query was used to return all hygiene scores equal to zero.  The group query was used to count the number of docuemtns by LocalAuthorityName.  The sort query was used to sort the count of the documents in descending order.  The results from the aggregation query wass cast as a list and saved to a results variable.  Pretty print was used to print the first 10 results.  he results were then converted to a Pandas dataframe nad normalised.  The first 10 rows were displayed.
