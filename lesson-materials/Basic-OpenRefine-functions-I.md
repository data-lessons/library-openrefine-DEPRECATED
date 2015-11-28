#Basic OpenRefine functions I
##Importing data
###Exercise 1: Create your first Open Refine project (using provided data)
There are several options for getting your data set into OpenRefine. You can upload or import files in a variety of formats including:

TSV (tab-separated values)
CSV (comma-separated values)
Excel
JSON (javascript object notation)
XML
Google Spreadsheet

To import the data for the exercises below, run OpenRefine and:

Click 'Create Project'
Choose 'Get Data from this Computer'
Click 'Choose Files'
Locate the file called 'doaj-article-sample.csv' (this can be downloaded from https://github.com/LibraryCarpentry/week-four-library-carpentry/tree/master/libcarp-wk4-data)
Click 'Next'

The next screen gives you some options to ensure that the data gets imported into OpenRefine correctly. The options vary depending on the type of data you are importing.

In this case you need to:

Set the 'Character encoding' to 'UTF-8'
Ensure the first row is used to create the column headings
Make sure OpenRefine doesn't try to automatically detect numbers and dates

Once you are happy click 'Create Project >>'

This will create the project and open it for you. Projects are saved as you work on them, there is no need to save copies as you go along.

To open an existing project in OpenRefine you can click 'Open Project' from the main OpenRefine screen (in the lefthand menu). When you click this, you will see a list of the existing projects and can click on a project's name to open it.

###Going Further
* Look at the other options on the Import screen - try changing some of these options and see how that changes the Preview and how the data appears after import.
* Do you have access to JSON or XML data? If so the first stage of the import process will prompt you to select a 'record path' - that is the parts of the file that will form the data rows in the OpenRefine project.

##Basic OpenRefine Functions
###The layout of OpenRefine
OpenRefine displays data in a tabular format. Each row will usually represent a 'record' in the data, while each column represents a type of information. This is very similar to how you might view data in a spreadsheet or database.

OpenRefine only displays a limited number of lines of data at one time. You can adjust the number choosing between 5, 10 (the default), 25 and 50.

###Reordering and renaming columns
Many operations in OpenRefine are accessed from the drop down menus at the top of each column. You can re-order the columns by clicking the drop down menu at the top of the first column (labelled 'All'), and choosing 'Edit columns' -> 'Re-order / remove columns …'

You can then drag and drop column names to re-order the columns, or remove columns completely if they are not required.

###Sorting data
You can sort data in OpenRefine by clicking on the drop down menu for the column you want to sort on, and choosing 'Sort'

Once you have sorted the data a new 'Sort' drop down menu will be displayed.

Unlike Excel 'Sorts' in OpenRefine are temporary - that is, if you remove the 'Sort', the data will go back to it's original 'unordered' state. The 'Sort' drop down menu lets you amend the existing sort (e.g. reverse the sort order), remove existing sorts, and make sorts permanent.

You can sort on multiple columns at the same time by adding another sorted column (in the same way).

##Facets
"Facets" are one of the most useful features of OpenRefine and can help both get an overview of the data in a project as well as helping you bring more consistency to the data.

A 'Facet' groups all the values that appear in a column, and then allow you to filter the data by these values and edit values across many records at the same time.

The simplest type of Facet is called a 'Text facet'. This simply groups all the text values in a column and lists each value with the number of records it appears in. The facet information always appears in the left hand panel in the OpenRefine interface.

To create a Text Facet for a column, click on the drop down menu at the top of the column and choose Facet -> Text Facet. The facet will then appear in the left hand panel.

The facet consists of a list of values used in the data. You can filter the data displayed by clicking on one of these headings.

You can include multiple values from the facet in a filter at one time by using the 'Include' option which appears when you put your mouse over a value in the Facet.

You can also 'invert' the filter to show all records which do not match your selected values. This option appears at the top of the Facet panel when you select a value from the facet to apply as a filter.

###Exercise 2: Which licences are used for articles in this file?
Create a facet for the 'Licence' column
What is the most common Licence in the file?
How many articles in the file don't have a licence assigned?

##Filters
As well as using Facets to filter the data displayed in OpenRefine you can also apply 'Text Filters' which looks for a particular piece of text appearing in a column. Text filters are applied by clicking the drop down menu at the top of the column you want to apply the filter to and choosing 'Text filter'.

As with Facets, the Filter options appear in the left hand panel in OpenRefine. Simply type in the text you want to use in the Filter to display only rows which contain that text in the relevant column.

You can also use regular expressions in the filte

##Working with filtered data
It is very important to note that when you have filtered the data displayed in OpenRefine, any operations you carry out will apply only to the rows that match the filter - that is the data currently being displayed.

##More on Facets
As well as 'Text facets' Refine also supports a range of other types of facet. These include:

* Numeric facets
* Timeline facets (for dates)
* Custom facets
* Scatterplot facets

**Numeric and Timeline facets** display graphs instead of lists of values. The graph includes 'drag and drop' controls you can use to set a start and end range to filter the data displayed.

**Scatterplot facets** are less commonly used - for further information on these see the tutorial at http://enipedia.tudelft.nl/wiki/OpenRefine_Tutorial#Exploring_the_data_with_scatter_plots

**Custom facets** are a range of different types of facets, and also allow you write your own custom facets. Some of the default custom facets are:

* Word facet - this breaks down text into words and counts the number of records each word appears in
* Duplicates facet - this results in a binary facet of 'true' or 'false'. Rows appear in the 'true' facet if the value in the selected column is an exact match for a value in the same column in another row
* Text length facet - creates a numeric facet based on the length (number of characters) of the text in each row for the selected column. This can be useful for spotting incorrect or unusual data in a field where specific lengths are expected (e.g. if the values are expected to be years, any row with a text length more than 4 for that column is likely to be incorrect)
* Facet by blank - a binary facet of 'true' or 'false'. Rows appear in the 'true' facet if they have no data present in that column. This is useful when looking for rows missing key data.

Facets are intended to group together common values and OpenRefine limits the number of values allowed in a single facet to ensure the software does not perform slowly or run out of memory. If you create a facet where there are many unique values (for example, a facet on a 'book title' column in a data set that has one row per book) the facet created will be very large and may either slow down the application, or OpenRefine will not create the facet. 

###Exercise 3: Find all publications without a DOI
* Use the 'Facet by blank' function to find all publications in this data set without a DOI

##Amending data through facets
If you create a text facet you can edit the values in the facet to change the value for several records at the same time. To do this, simply mouse-over the value you want to edit and click the 'edit' option that appears.

This approach is useful in relatively small facets where you might have small variations through punctuation or typing errors etc. For example, a column that should contain only terms from a small restricted list such as days of the week or months of the year.

The list of values in the facet will update as you make edits.

###Exercise 4: Correct the "Language" values via a facet
* Create a Text facet on the Language column
* Notice that there is both 'EN' and 'English'
* Put the mouse over the 'English' value
* Click 'Edit'
* Type 'EN' and click 'Apply'
* See how the Language facet updates

Using Clustering to find similar values
Another function that is provided with facets is the 'Cluster' function. The Cluster function looks for similar values across the facet and enables you to merge together several facets to a single value.

This is very effective where you have data where there can be minor variations in data values that are likely such as names of people, organisations and places.

To use the the 'Cluster' function, create a Facet on the relevant column and click the 'Cluster' button. This will bring up a new window where you can see the 'Clusters' that have been detected and work with them:
The 'Clusters' are created automatically according to an algorithm. There are a number of different algorithms supported by OpenRefine - some experimentation maybe required to see which clustering algorithm works best with any particular set of data, and you may find that using different algorithms highlights different clusters.

For more information on the methods used to create Clusters see https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth

For each cluster you have the option of 'merging' the values together - that is replace with a single consistent value. By default OpenRefine uses the most common value in the cluster as the new value, but you can select one of the other values by clicking the value itself, or you can simply type the desired value into the 'New Cell Value' box.

The Clustering function can also be accessed via the drop down menu at the top of a column by selecting "Edit cells" -> "Cluster and edit …"

##

Exercise 5: Use Clustering to clean up author data
Create a Text Facet for the "Publisher" column
Click 'Cluster'
Using the 'key collision' method with the 'fingerprint' Keying Function work through the clusters of values, merging them to a single value where appropriate
