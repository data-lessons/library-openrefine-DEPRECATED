#Advanced OpenRefine functions
##Looking up data from a URL
OpenRefine can retrieve data from URLs. This can be used in various ways, including looking up additional information from a remote service, based on information in your OpenRefine data.

As an example, you can look up names against the Virtual International Authority File (VIAF), and retrieve additional information such as dates of birth/death and identifiers.

Typically this is a two step process - firstly a step to retrieve data from a remote service, and secondly to extract the relevant information from the data you have retrieved.

To retrieve data from an external source, from the drop down menu at a column heading use the option 'Edit column->Add column by fetching URLs'.

This will prompt you for a GREL expression to create a URL. Usually this would be a URL that uses existing values in your data to build a query. When the query runs OpenRefine will request each URL (for each line) and retrieve whatever data is returned (this may often be structured data, but could be simply HTML).

The data retrieved will be stored in a cell in the new column that has been added to the project. You can then use OpenRefine transformations to extract relevant information from the data that has been retrieved. Two specific OpenRefine functions used for this are:

* parseHtml()
* parseJson()

The 'parseHtml()' function can also be used to extract data from XML.

The next exercise demonstrates this two stage process in full.

###Exercise 11: Retrieving journal details from CrossRef via ISSN
Because retrieving data from external URLs takes time, this exercise targets a single line in the data. In reality you would want to run this over many rows (and probably go and do something else while it ran)

* Select a single row from the data set which contains an ISSN by:
    * Clicking the star icon for the relevant row in the first column
    * Facet by Star
    * Choose the single row
* In the ISSN column use the dropdown menu to choose 'Edit column->Add column by fetching URLs'
* Give the column a name e.g. "Journal details"
* In the expression box you need to write some GREL where the output of the expression is a URL which can be used to retrieve data (the format of the data could be HTML, XML, JSON, or some other text format)

In this case we are going to use the CrossRef api (read more about the CrossRef service at http://www.crossref.org, read more about the API we are going to use at https://github.com/CrossRef/rest-api-doc/blob/master/rest_api.md)

The syntax for requesting journal information from CrossRef is ```http://api.crossref.org/journals/{ISSN}``` where {ISSN} is replaced with the ISSN of the journal

* In the expression box type the GREL ```"http://api.crossref.org/journals/"+value```
* Click 'OK'

You should see a message at the top on the OpenRefine screen indicating it is fetching some data, and how far it has got. Wait for this to complete. Fetching data for a single row should take only ten seconds or so, but fetching data for all rows will take longer. You can speed this up by modifying the "Throttle Delay" setting in the 'Add column by fetching URLs' dialog which controls the delay between each URL request made by OpenRefine. This is defaulted to a rather large 5000 milliseconds (5 seconds).

At this point you should have a new cell containing a long text string in a format called 'JSON' (this stands for Javascript Object Notation, although very rarely spelt out in full).

OpenRefine has a function for extracting data from JSON (sometimes referred to as 'parsing' the JSON). The 'parseJson' function is explained in more detail at [https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions).

* In the new column you've just added use the dropdown menu to access 'Edit column->Add column based on this column'
* Add a name for the new column e.g. "Journal Title"
* In the Expression box type the GREL ```value.parseJson().message.title```
* You should see in the Preview the Journal title displays

The reason for using 'Add column based on this column' is simply that this allows you to retain the full JSON and extract further data from it if you need to. If you only wanted the title and did not need any other information from the JSON you could use 'Edit cells->Transform...' with the same GREL expression.

##Reconciliation services
Reconciliation services allow you to lookup terms from your data in OpenRefine against external services, and use values from the external services in your data.

Reconciliation services can be more sophisticated and often quicker than using the method described above to retrieve data from a URL. However, to use the ‘Reconciliation’ function in OpenRefine requires the external resource to support the necessary service for OpenRefine to work with, which means unless the service you wish to use supports such a service you cannot use the ‘Reconciliation’ approach.

For more information on using Reconciliation services see [https://github.com/OpenRefine/OpenRefine/wiki/Reconciliation-Service-API](https://github.com/OpenRefine/OpenRefine/wiki/Reconciliation-Service-API)

##Extensions
The functionality in OpenRefine can be enhanced by ‘extensions’ which can be downloaded and installed to add functionality to your OpenRefine installation.

A list of Extensions (not necessarily complete) is given at https://github.com/OpenRefine/OpenRefine/wiki/Extensions

One of these extensions tries to work around the limitation of Reconciliation services described above, by making it possible to use a reconciliation service against ‘linked data’ sources which have SPARQL endpoints. For more information on this see the ‘RDF Extension’ at http://refine.deri.ie. An example of how this works is given in more detail at http://refine.deri.ie/showcases.

##Using the ‘cross’ function to lookup data in other OpenRefine projects
As well as looking up data in external systems using the methods described above, it is also possible to look up data in other OpenRefine projects on the same computer. This is done using the ‘cross’ function.

The ‘cross’ function takes a value from the OpenRefine project you are working on, and looks for that value in a column in another OpenRefine project. If it finds one or more matching rows in the second OpenRefine project, it returns an array containing the rows that it has matched.

As it returns the whole row for each match, you can use a transformation to extract the values from any of the columns in the 

You can use to compare the contents of two OpenRefine projects, or to use data between the two projects.

The [VIB-Bits extension](https://www.bits.vib.be/index.php/software-overview/openrefine) adds a number of very useful functions to OpenRefine including a way of using the 'cross' function with simply point-and-click functionality which makes looking up data from other projects significantly simpler.
