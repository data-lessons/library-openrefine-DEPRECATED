#Basic OpenRefine functions II
##Transforming data
###Introducing Transformations
Through facets, filters and clusters OpenRefine offers relatively straightforward ways of getting an overview of your data, and making changes where you want to standardise terms used to a common set of values.

However, sometimes there will be changes you want to make to the data that cannot be achieved in this way. Such types of changes include:

* Splitting data that is in a single column into multiple columns (e.g. splitting an address into multiple parts)
* Standardising the format of data in a column without changing the values (e.g. removing punctuation or standardising a date format)
* Extracting a particular type of data from a longer text string (e.g. finding ISBNs in a bibliographic citation)

To support this type of activity OpenRefine supports 'Transformations' which are ways of manipulating data in columns. Transformations are normally written in a special language called 'GREL' (Google Refine Expression Language). To some extent GREL expressions are similar to Excel Forumla, although they tend to focus on text manipulations rather than numeric functions.

Full documentation for the GREL is available at https://github.com/OpenRefine/OpenRefine/wiki/Google-refine-expression-language. This tutorial covers only a small subset of the commands available.

###Common transformations
Some transformations are used regularly and are accessible directly through menu options, without having to type them directly.

Examples of some of these common transformations are given in the table below, with their 'GREL' equivalents. We'll see how to use the GREL version later in this lesson.

Common Transformation  | Action | GREL expression
--------------------| ------------- | -------------
To Uppercase| Converts the current value to uppercase | value.toUppercase()
To Lowercase| Converts the current value to lowercase | value.toLowercase()
To Titlecase| Converts the current value to titlecase (i.e. each word starts with an uppercase character and all other characters are converted to lowercase) | value.toTitlecase()
Trim leading and trailing whitespace | Removes any ‘whitespace’ characters (e.g. spaces, tabs) from the start or end of the current value | value.trim()

###Exercise 7: Correct Publisher data
* Create a text facet on the Publisher column
* Note that in the values there are two that look identical - why does this value appear twice?
* On the publisher column use the dropdown menu to select 'Edit cells->Common transforms->Trim leading and trailing whitespace'
* Look at the publisher facet now - has it changed? (if it hasn't changed try clicking the Refresh option to make sure it updates)



To start writing transformations, select the column on which you wish to perform a transformation and choose 'Edit cells->Transform…'. In the screen that displays you have a place to write a transformation (the 'Expression' box) and then the ability to Preview the effect the transformation would have on 10 rows of your data.

The transformation you type into the 'Expression' box has to be a valid GREL expression. The simplest expression is simply the word 'value' by itself - which simply means the value that is currently in the column - that is: make no change.

GREL functions are written by giving a value of some kind (a text string, a date, a number etc.) to a GREL function. Some GREL functions take additional parameters or options which control how the function works. GREL supports two syntaxes:

* value.function(options)
* function(value, options)

Either is valid, and which is used is completely down to personal preference. In these notes the first syntax is used.

Next to the 'Preview' option are options to view:
* History - a list of transformations you've previously used with the option to reuse them immediately or to 'star' them for easy access
* Starred - a list of transformations you've 'starred' via the 'History' view
* Help - a list of all the GREL functions and brief information on how to use them

###Some Simple Transformations


###Exercise 8: Put titles into TitleCase
* Facet by publisher
* select Akshantala Enterprises and Society of Pharmaceutical Technocrats
* Use 'Convert to Title Case' tranformation on Title col

###Exercise 9: Convert Date column to Date

* Demonstrate basic GREL
    * e.g. ???
* Match function
    * reorder reversed names in Author col
    * value.match(/(.*),(.*)/)[1] + " " + value.match(/(.*),(.*)/)[0]

* Undo/Redo

* Split and filter on Subject Col?
...