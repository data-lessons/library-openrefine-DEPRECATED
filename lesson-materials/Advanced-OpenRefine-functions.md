#Advanced OpenRefine functions
##Looking up data from a URL
OpenRefine can retrieve data from URLs. This can be used in various ways, including looking up additional information from a remote service, based on information in your OpenRefine data.

As an example, you can look up names against the Virtual International Authority File (VIAF), and retrieve additional information such as dates of birth/death and identifiers.

Typically this is a two step process - firstly a step to retrieve data from a remote service, and secondly to extract the relevant information from the data you have retrieved.

To retrieve data from an external source, from the drop down menu at a column heading use the option ‘Edit column’ -> ‘Add column by fetching URLs’.

This will prompt you for a GREL expression to create a URL. Often this would be a URL that uses existing values in your data to build a query.

Exercise 11: Retrieving journal details from CrossRef via ISSN
Because retrieving data from external URLs takes time, this exercise targets a single line in the data. In reality you would want to run this over many rows (and probably go and do something else while it ran)
* Select a single row from the data set which contains an ISSN by:
    * Clicking the star icon for the relevant row in the first column
    * Facet by Star
    * Choose the single row
* Add col from URL
* http://api.crossref.org/journals/"+value


##Reconciliation services
Reconciliation services allow you to lookup terms from your data in OpenRefine against external services, and use values from the external services in your data.

Reconciliation services can be more sophisticated and quicker than using the method described above to retrieve data from a URL. However, to use the ‘Reconciliation’ function in OpenRefine requires the external resource to support the necessary service for OpenRefine to work with, which means unless the service you wish to use supports such a service you cannot use the ‘Reconciliation’ approach.

##Extensions
The functionality in OpenRefine can be enhanced by ‘extensions’ which can be downloaded and installed to add functionality to your OpenRefine installation.

A list of Extensions is given at https://github.com/OpenRefine/OpenRefine/wiki/Extensions

One of these extensions tries to work around the limitation of Reconciliation services described above, by making it possible to use a reconciliation service against ‘linked data’ sources which have SPARQL endpoints. For more information on this see the ‘RDF Extension’ at http://refine.deri.ie. An example of how this works is given in more detail at http://refine.deri.ie/showcases.

##Using the ‘cross’ function to lookup data in other OpenRefine projects
As well as looking up data in external systems using the methods described above, it is also possible to look up data in other OpenRefine projects on the same computer. This is done using the ‘cross’ function.

The ‘cross’ function takes a value from the OpenRefine project you are working on, and looks for that value in a column in another OpenRefine project. If it finds one or more matching rows in the second OpenRefine project, it returns an array containing the rows that it has matched.

As it returns the whole row for each match, you can use a transformation to extract the values from any of the columns in the 

You can use to compare the contents of two OpenRefine projects, or to use data between the two projects.