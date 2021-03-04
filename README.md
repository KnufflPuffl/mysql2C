# mysql2php

## How does it work ? 

mysql2php provides a simple to use iterface, in order to obtain and update database information for a MySQL database (CRUD Operations). 
It will automatically convert all database tables into PHP Classes. It will also provide an object oriented array of all the database data of each class. It can then be used to manipulate the data from an object, and the library will automatically update the data in the corresponding database entry, which will save you a tremendous amount of time, because no more SQL queries are needed. 

## Explanaiton 

See the following example for a better understanding of how the library works. 

![Image description](http://viewport.at/projects/mysql2php/images/concept.jpg)


## Installation 

simply require the provided autoloader.php file. 

## Configuration  

All you have to do is adjust the config.php file with your database connection parameters. 

## Initialization  

Before you can use mysql2php it has to create the PHP Class Files first. 
To do this open the installation.php file in your browser, or call `$mysql2php->install();` 

This will create all neccessary class files in /classes folder, and create an autoloader for it. You only should call this once, or if you applied some changes to your database structure. 

## Loading Data 

At the start up of your application call `$mysql2php->loadData();`
This will load all entries from your Database into a array for each table. 

Note: The reason why it is not included directly in autoload is, because there might be pages on which you might not need any data from your database. 
You should only call this function, at the first startup of your application / loadup.  

## Accessing Data 

use the mysql2php function `$mysql2php->getData(String classname);` which will return an array of all data within the supplied classname / database table name. 

## Accessing specific Data 

To access a specific object use `$mysql2php->getData(String classname, int primary_key);` this will return the object with supplied primary key of the given class. 

In this object all the properties are accessable using => operator. For example to get the value of property name for object person with primary key 1 you would use this command: 

`$name = $mysql2php->getData('person',1)->name;`

## Updating Data 

To update a value use setData method like this `$mysql2php->setData(String classname, int primary_key, String attribute_name, String value);` 

For example to update the Name of Person with primary key 1, you would write the command like this: 

`$mysql2php->setData('person',1,'name','Mustermann');`

## Delete an entry  

To delete a data entry use deleteData method like this  `$mysql2php->deleteData(String classname, int primary_key);`


# mysql2j (JavaScript Client - Experimental)

## mysql2j is a Javascript library which can be used in a very similar way 

Dependencies: mysql2php, jQuery 
--> mysql2j requires that you have also installed mysql2php, as it is using mysql2php's API in the exact same way using AJAX. It also requires jQuery > 3.0 

Experimental Status: depending on data amount mysql2j might be slow - especially on low memory end devices (data in Javascript is stored on the client), next version of mysql2j will include more options for only loading the required data. It should work quite fast for regular data heavy applications though. You also have the option to do regular AJAX requests and use mysql2php only on the server side if you run into performance issues. Future versions of mysql2j will also include option to use indexedDB (hardware storage) instead of random access memory. 


## Installation 

include the mysql2j.js file, and its config file in your web application (after you have included jQuery): 

`<script type="text/javascript" src="/mysql2j/mysql2j-config.js"></script>`
`<script type="text/javascript" src="/mysql2j/mysql2j.min.js"></script>`


## Configuration  

All you have to do is adjust the mysql2j-config.js file.
You only need to change the backendurl variable to the URL where your mysql2php library is stored (and accessible using any common webserver). 

mysql2j-config.js example: 
`backendurl = "http://localhost/mysql2php/"; `


## Initialization  

--> this does the exact same thing as described above, but you can also do it now using Javascript directly:

` mysql2j.install(); `


## Loading Data 

At the start up of your application call `mysql2j.loadData();`
This will load all entries from your Database into a array for each table. 

Note: The reason why it is not included directly in autoload is, because there might be pages on which you might not need any data from your database. 
You should only call this function, at the first startup of your application / loadup.  


## Accessing Data 

`mysql2j.getData(String classname);` which will return an array of all data within the supplied classname / database table name. 


## Accessing specific Data 

To access a specific object use `mysql2j.getData(String classname, int primary_key);` this will return the object with supplied primary key of the given class. 

In this object all the properties are accessable using .operator For example to get the value of property name for object person with primary key 1 you would use this command: 

`var name = mysql2j.getData('person',1).name;`

## Updating Data 

To update a value use setData method like this `mysql2j.setData(String classname, int primary_key, String attribute_name, String value);` 

For example to update the Name of Person with primary key 1, you would write the command like this: 

`mysql2j.setData('person',1,'name','Mustermann');`


## Delete an entry  

To delete a data entry use deleteData method like this  `mysql2j.deleteData(String classname, int primary_key);`


## Data Ensurance 

As you might have noticed, mysql2j doesn't yet provide any kind of success or error callbacks - it simply sends out the requests to the server. 
Therefore, (right now) it is not guaranteed that the server will process the request correctly (server might be offline, or some other server side error could happen, timeout errors or something else).

The advantage on the other hand is, that the usage of mysql2j currently is very simple, without the need to mess with callbacks/Promises. 
Therefore it is planned that next versions of mysql2j will include an option which will allow you to use callbacks or promises, for better data ensurance. 


## Experimental Status

All of mysl2j features are currently still in experimental state - if you discover any issue, please let us know. 



