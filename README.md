# nosql-challenge
Module 12 Challenge


# Part 1: Database and Jupyter Notebook Set Up

I imported provided  data `establishments.json` file from a Terminal using `$ mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`. The database was named `uk_food` and the collection `establishments`.

Within Jupyter Noteboook : NoSQL_setup_starter.ipynb, libraries PyMongo and Pretty Print were imported and an instance of the Mongo Client was installed.

Confirmation that the database was created was tested by printing all the database names from mongo and seeing new database uk_food listed in the output.  From the database uk_food, a list of collection names was printed to ensure establishments was available.  An example of a document was printed using pretty print. Selecting the document was done using find_one. 


# Part 2: Update the Database

Still within NoSQL_setup_starter.ipynb, a new restaurant called "Penang Flavours" was added to the uk_food database.

