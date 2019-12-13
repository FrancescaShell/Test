# Open Air Quality :deciduous_tree: :partly_sunny:

In this repository you can find a file named ```main.py``` that queries the [OpenAQ](https://openaq.org) website for air quality measurements within European cities. The values of the polluting molecules are gathered through web-accessible API.

If you execute the main file by running the program with: 
```python main.py -a username -p password -c city -m pm10```
 
It will give you this kind of result:	
```
$ python3 main.py -a username -p password -c city -m pm10
Successful log-in. Welcome username!
16.043478260869566
```

> **Note:** 
> - In case the user forgets to specify the parameter, the programm runs the default parameter “pm10”
> - The project requires the following modules: argparse, sqlite3, hashlib, random, requests, json, csv, unittest, os, and sys.


### Get started!
Registration is required!
In order to access information you need to: 
1. open the ```scripts``` file;
2. register with an username and a password.
```
$ python dbmanager.py -a test -p test  
The registration had been successful
```

### Parameters Guide
Positional arguments
*username*: name of the user to log-in

Optional arguments
•	**-v**, **--verbosity**: output verbosity (three levels of verbosity admitted).
•	**-p**, **--password**: user password to log-in.
•	**-c**, **--city**: name of the European city.
•	**-m**, **--molecule**: symbol of the polluting parameter. 

### Documentation
The source of our documentation is the on-line site Openaq. It provides air composition data updated from time to time by other sites. It queries the [OpenAQ](https://openaq.org) website to fetch the value of some air quality parameter in a world city. 

To join the program, you can choose:
- a **city**, in the list of European cities
- a **parameter**, from the set of molecules. 

Cities and parameters are stored in ```pypackage``` as .csv files; respectively in ```cities.csv``` and ```parameters.csv```

### Create AND Populate Openairq_user.DB
Before run ```main.py``` you need to register with a username and a password. The sign-in necessity of a database to record all the users' information. You find all the process to create a database inside the ```dbmanager.py```file inside /script directory.
You need to import and use the library SQLite3. The program will check if the database is already existing. If not you create a new DB called user_database using: 
```
cursor.execute('''CREATE TABLE user_database
                     (username TEXT CHAR(30) NOT NULL, 
                     password_digest TEXT CHAR(30) NOT NULL,
                     salt TEST, PRIMARY KEY (username))''')
```
 
It will create a table with 3 columns (username, password_digest, and salt). NOT NULL and CHAR(30) conditions allow the DB will not register Nan or a maximum of 30 characters.

### Testing 

You can test by yourself running the module ```test_openairquality``` inside the test directory. The function checked is the **list_csv** of the module ```openairquality.py``` inside pypackage folder.
To run it use from the main folder :
```$ python3 -m unittest -v -b tests/test_test_open_airquality.py```
```
$ python3 -m unittest -v -b tests/test_test_open_airquality.py
 test_empty_file (tests.test_main.TestCsvCreation) ... ok
 test_invalid_file (tests.test_main.TestCsvCreation) ... ok
 test_no_file (tests.test_main.TestCsvCreation) ... ok
 test_valid_file (tests.test_main.TestCsvCreation) ... ok
```
> **NOTE:**
Inside the folder the two file ```eu.csv``` and ```ibelieveinmyself.jpg``` are used in the module ```test_main``` to test that the function accept a csv a file different and not accept a file with a different format(jpg)


#### Group Components:
Anna Lagrasta (868543) 30/11/1998 <br/>
Francesca Griggio (866764) 03/12/1998 <br/>
Martina Gualandi (869442) 21/05/1998  

