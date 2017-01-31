P4TMongo
========

P4TMongo is a PHP Class that mimics the popular AdoDB PHP Library and new PDO Library. Use your favorite getOne (fetchColumn), getRow (fetch), getAll (fetchAll), insert (query) and other commands with MongoDB.

## Prerequisites

* PHP Version 5.2+
* PHP MongoDB Driver Version 1.2.6+
* MongoDB Version 1.6+
  
## Usage

This class is a layer above the MongoDB PHP Driver that implements most AdoDB functions. 
First you need to initialize a connection:

    <?php
  	...
        include_once('P4TMongo.class.php');
        $db = new P4TMongo('mongodb://user.password@localhost');
        $db->setDBName('myDatabase');
	    ...
    ?>

And then you can start using your favorite AdoDB functions with MongoDB right out of the box, for example:

    <?php
        ...
        $filter = array(
                            'Gender' => 'male'
                        );

        //getOne (AdoDB) and fetchColumn (PDO)  returns one value
        $value = $db->getOne('myTestCollection', 'columnIWantToTakeValueFrom', $filter); // like AdoDB
        $value = $db->fetchColumn('myTestCollection', 'columnIWantToTakeValueFrom', $filter); // like PDO
                
        //getRow (AdoDB) and fetch (PDO) returns one row
        $row = $db->getRow('myTestCollection', $filter); // like AdoDB
        $row = $db->fetch('myTestCollection', $filter); // like PDO
        
        //getAll (AdoDB) and fetchAll (PDO) returns all rows
        $allDataInCollection = $db->getAll('myTestCollection', $filter); // like AdoDB
        $allDataInCollection = $db->fetchAll('myTestCollection', $filter); // like PDO
        ...
    ?>
    
Supported getters are:

* getOne() // fetchColumn()
* getOneByID() // fetchColumnByID()
* getCol()
* getRow() // fetch()
* getRowByID() // fetchByID()
* getAll() // fetchAll()
* getAssoc()
    
How about inserting data?
    
    <?php
        ...
        $record = array(
                        'Name' => 'Alehandro Coolikoff',
                        'Gender' => 'male',
                        'Age' => 30
                    );
                    
        $db->insert('myTestCollection', $record); // like AdoDB
        $db->query('myTestCollection', $record); // like PDO
        ...
    ?>
    
There are also helper function for updating, deleting, counting, grouping and executing admin commands. Please check the function definitions for more details on possible usage options.


## License

Copyright 2012 Alexey Kulikov / a.kulikov@gmail.com / POOL4TOOL AG, Vienna, Austra

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.