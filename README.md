# tableau-challenge
This is a repo for the Jupyter Notebook used to process the data obtained from the CitiBike Site.  The amount of data they provide is vast so choices were required to limit the amount of data.  I wanted to look at year to year trends and also seasonal.  Therefore I looked at data from June (summer) and December (winter) from 2013 to 2019.  Even with these limitations the total amount of data was over 14M lines, making this a challenging assignment.

The citibike site provides the data in CSV files for each month of each year.  In order to combine the data for June and Dec from the different months a Juptyer Notebook was employed.  This also provided the opportunity to clean up the data.  Several key discoveries were made in the data:
1. The date format was not consistent year to year and had to be accomodated.
2. The column headings changed a few times - using capitalization rather than all lower case.
3. There was a small amount of NULL data that had to be removed.

In the notebook all the CSV files were read in using "GLOB" which creates a list of dataframes.  Each dataframe is a csv file.  Checking the column names showed the inconsistency in the column naming convention.  However, the columns were in a consistent order.  Therefore the column names from one file was applied to all of them (while still in list form) to create the consistency when merging the dataframes.

The date format was more complicated to overcome.  Using the parse function allowed the dates to be broken into hour (as decimal form of hour and minutes), day, month and year.  These were added as new columns.  The advantage of parse was greater tolerance in accepting different date and time conventions.  Even though the formatting changed between dataframe sections parse was able to handle this change and consistently extract the correct time.

The dataset extended from 2013 to 2020, which was greater than 15M lines of data.  It was later discovered that Tableau only accepts 15M lines.  Therefore the year 2020 was dropped from the dataset (this was done in Tableau which provides an easy process for dropping a given set of data during the import process).  The size of the data file means it took a long time to run.  To make certain the code was actually functioning correctly I wanted to have it update a line every 1000 operations of parsing the data.  I did not want it to write a new line each time but rather continue to update the one line below the code in the Notebook.  This was a new requirement and needed research to find an answer.  A slick solution is provided in the code below:

  
           if(i % 1000 == 0):
 
                clear_output(wait=True)
                
                print(i)  # use display(f) if you encounter performance issues
                
                sleep(0.01)
                
 Please enjoy the Tableau file!
