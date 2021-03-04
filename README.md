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


# mysql2j

## mysql2j is a Javascript library which can be used in a very similar way 

--> mysql2j requires that you have also installed mysql2c, as it is using mysql2c's API in the exact same way using AJAX. 






