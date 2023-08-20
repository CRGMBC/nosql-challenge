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

Some of the number values are stored as strings, when they should be stored as numbers. I used update_many to convert latitude and longitude to decimal numbers.  To check that these values were all updated, I created 2 counts - a float_count & a non_float_count.  I looped through the documents and counted if the "longitude" or "latitude" values are of type float or int.  If they were of type float or int, the float_count was incremented, if not, the non_float_count ws incremented.  The results were printed.

The Rating_value also needed to be amended to an integer.  This field has non-numeric values that I first set to 'Null' and then set the field to an integer type using update_many.  I then checked that these values are now numbers by iterating through the documents to see if thr RatingValue field exisits and if it does, print the type which will be int or float for a number.  

