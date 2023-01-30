# EPAM-DevOps22: Database _Administration

[Task description in .pdf file](/Database_Administration_task.pdf)

## This task describes how to work with MySQL on a virtual machine.

## Steps of Task
**1. Download and install MySQL server on VM.**
```
sudo apt install mysql-server
```
![](/Database%20_Administration/Screens/MySql-version.png)

**2. Select a subject area and describe the database schema, (minimum 3 tables)**

- Aircraft table:

| Number |Manufacturer | Model | Price |
| ---------| ------------- | ----------| ----------|
| 1 | Boeing | 737-800 | 62.00 |
| 2 | Boeing | 747-400 | 82.00 |
| 3 | Boeing | 777 | 305.00 |
| 4 | Airbus | A380 | 489.00 |
| 5 | Airbus | A310 | 59.00 |

- Engines table:

| Number |Producer | Type | Price |
| ---------| ------------- | ----------| ----------|
| 1 | General Electric | CFM56  | 10.00 |
| 2 | General Electric | GE90 | 27.50 |
| 3 | Pratt & Whitney  | PW4000 | 8.50 |
| 4 | Pratt & Whitney  | GP7200  | 45.00 |

- Assembly table:

| Number |Country | Final product | Price |
| ---------| ------------- | ----------| ----------|
| 1 | USA | Boeing-CFM56   | 14.00 |
| 2 | France | Boeing-PW4000 | 10.50 |
| 3 | Germany  | PW4000 | 8.60 |
| 4 | China  | Boeing-GE90  | 7.80 |
| 5 | India  | Airbus-GP7200  | 6.50 |
| 6 | Canada  | Airbus-CFM56   | 9.60 |

**3. Created a database and 3 tables:**

![](/Database%20_Administration/Screens/Create%20Database.png)

![](/Database%20_Administration/Screens/Create%20table.png)

**4. Filling tables with data:**

![](/Database%20_Administration/Screens/Filling%20tables.png)

**5. Construct and execute `SELECT` operator with `WHERE`, `GROUP BY` and `ORDER BY`:**

![](/Database%20_Administration/Screens/Work%20with%20tables.png)

**5. Execute other defferents SQL queries DDL, DML, DCL.**

- 5.1 DDL

![](/Database%20_Administration/Screens/DDl-1st.png)
![](/Database%20_Administration/Screens/DDl-2nd.png)

- 5.2 DML

![](/Database%20_Administration/Screens/DMl-1st.png)
![](/Database%20_Administration/Screens/DMl-2nd.png)

- 5.3 DCL

![](/Database%20_Administration/Screens/DCL-1.png)
![](/Database%20_Administration/Screens/DCL-2.png)
![](/Database%20_Administration/Screens/DCL-3.png)
![](/Database%20_Administration/Screens/DCL-4.png)

**6. Make a selection from the main table DB MySQL.**

![](/Database%20_Administration/Screens/DM%20MySQL.png)

**7. Make backup of your database.**

![](/Database%20_Administration/Screens/BackUp%20databases.png)

**8. Delete the table and/or part of the data ine the table.**

![](/Database%20_Administration/Screens/Change%20table.png)

**9. Restore your database.**

![](/Database%20_Administration/Screens/Restore%20table.png)

**10. Transfer your local database to RDS AWS.**
> Since I do not have the ability to connect to RDS AWS, it will use the second virtual machine available.

10.1 Comress backup file: 

![](/Database%20_Administration/Screens/Compress%20backup.png)

10.2 Send backup file to another VM: 

![](/Database%20_Administration/Screens/send%20backup.png)

10.3 Extrcat backup file on the VM: 

![](/Database%20_Administration/Screens/Extract%20backup.png) 

**11. Create a database and collection in MongoDB.**

![](/Database%20_Administration/Screens/Create%20a%20database%20and%20collection%20in%20Mongo.png)

**12. Using the command find() in MongoDB.**

![](/Database%20_Administration/Screens/Comand-find.png)

*End task*
