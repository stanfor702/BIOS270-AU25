```
Writeup 3
Alex Stanford 


    Examine create_bacteria_db.sh, how many tables will be created in the database?
I believe the number of tables that will be created in the database is 3

    In the insert_gff_table.py script you submitted, explain the logic of using try and except. Why is this necessary?
In this python script "try" looks to being attempting to appending the a dataframe to the sql database, if it works the loop breaks,
however I'm not totally sure what "except" is attempting to do. It moves onto this line if adding the df to the database isn't successful
and then retrys if you don't recieve a "database is locked error"? This is probably necessary in order to not lose progress in terms of uploaded to the database if one of the trys fails.  


```
