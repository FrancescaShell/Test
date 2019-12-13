# Open Air Quality
### Monitor pollution levels of major Europen cities :deciduous_tree: :partly_sunny:

Breathing in particle pollution can be harmful to your health. Some particles can irritate your eyes, nose, and throat, whereas smaller particles can even get into your lungs. In this repository you can find a file named ```main.py``` that can help you monitoring European city's air pollution levels. Indeed, it queries the [OpenAQ](https://openaq.org) website for air quality measurements within specific European cities. Data of the following polluting molecules are gathered from multiple sources and made web-accessible through the [Open AQ Platform API](https://docs.openaq.org/): bc, co, no2, o3, pm10, pm25, so2.


### Get started!
The project requires the following modules: argparse, sqlite3, hashlib, random, requests, json, csv, unittest, os, and sys.
Firstly, **registration is required** to access information about the atmosphere!
In order to register you need to: 
1. Open the ```scripts``` file;
2. Register with username and password:
```
$ python dbmanager.py -a test -p test  
The registration had been successful
```
> **Note:** you can add as many users as you want repeating these steps. Remember, you can't add more than one user with the same username.
If you run the program for the first time, this will create a username and password database, so you can run the main program as follows:
3. Execute the main file by running the program with: 
```$ python main.py -a username -p password -c city -m pm10```

You will get this kind of result:	
```
$ python3 main.py -a username -p password -c city -m pm10
Successful log-in. Welcome username!
16.043478260869566
```
> **Note:** in case the user forgets to specify the parameter, the programm runs the default parameter “pm10”. Indeed, pm10 are the most common polluting particles from 2.5 to 10 micrometers in diameter.

### Parameters Guide
Positional arguments:

•	**username**: name of the user to log-in

Optional arguments:

•	**-v**, **--verbosity**: output verbosity (three levels of verbosity admitted).

•	**-p**, **--password**: user password to log-in (required).

•	**-c**, **--city**: name of the European city (required).

•	**-m**, **--molecule**: molecule of the polluting parameter (pm10 by default). 

### Documentation

To join the program, you can choose:
- a **city**, in the list of European cities
- a **parameter**, from the set of molecules. 

Cities and parameters are stored in ```pypackage``` as .csv files; respectively in ```cities.csv``` and ```parameters.csv```

### Create and Populate Openairq_user.db
Before running ```main.py``` you need to register with a username and a password. There is sign-in necessity of a database to record all the users' information. You find all the processes needed to create a database inside the ```dbmanager.py```file inside /script directory.
You need to import and use the library SQLite3. The program will check if the database is already existing. If not you create a new DB called user_database using: 
```
cursor.execute('''CREATE TABLE user_database
                     (username TEXT CHAR(30) NOT NULL, 
                     password_digest TEXT CHAR(30) NOT NULL,
                     salt TEST, PRIMARY KEY (username))''')
```
 
It will create a table with 3 columns (username, password_digest, and salt). NOT NULL and CHAR(30) conditions allow the DB will not register Nan or a maximum of 30 characters.

### Testing 

You can test the code by yourself running the module ```test_openairquality``` inside the test directory. The function checked is the **list_csv** of the module ```openairquality.py``` inside pypackage folder.
To run it use from the main folder :
```$ python3 -m unittest -v -b tests/test_test_open_airquality.py```
```
$ python3 -m unittest -v -b tests/test_test_open_airquality.py
 test_empty_file (tests.test_main.TestCsvCreation) ... ok
 test_invalid_file (tests.test_main.TestCsvCreation) ... ok
 test_no_file (tests.test_main.TestCsvCreation) ... ok
 test_valid_file (tests.test_main.TestCsvCreation) ... ok
```
> **Note:** inside the folder the two file ```eu.csv``` and ```ibelieveinmyself.jpg``` are used in the module ```test_main``` to test that the function accept a csv a file different and not accept a file with a different format(jpg)


#### This repository has been created by the Group Unicorns :unicorn: :
Anna Lagrasta (868543) <br/>
Francesca Griggio (866764) <br/>
Martina Gualandi (869442)

