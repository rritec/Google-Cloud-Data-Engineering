# Cloud SQL
1. Cloud SQL offers a fully-managed database service for MySQL, PostgreSQL, and SQL Server, reducing your overall cost of operations and freeing up teams to focus on innovation

## Task 1. Create a Cloud SQL instance

1. From the Navigation menu (Navigation menu icon) click on SQL.
2. Click Create Instance.
3. Choose MySQL database engine.
4. For Choose a Cloud SQL edition, select Enterprise edition.
5. Select the database version as MySQL 8.
6. Enter Instance ID as myinstance.
7. In the password field click on the Generate link and the eye icon to see the password. Save the password to use in the next section.
8. For Preset choose Development (4 vCPU, 16 GB RAM, 100 GB Storage, Single zone).
9. Warning: if you choose a preset larger than Development, your project will be flagged and your lab will be terminated.
10. Set Region as us-west1.
11. Set the Multi zones (Highly available) > Primary Zone field as us-west1-a.
12. Click CREATE INSTANCE.
13. It might take a few minutes for the instance to be created. Once it is, you will see a green checkmark next to the instance name.
14. Click on the Cloud SQL instance. The SQL Overview page opens.

## Task 2. Connect to your instance using the mysql client in Cloud Shell

1. In the Cloud Console, click the Cloud Shell icon in the upper right corner.
2. Click Continue.
3. At the Cloud Shell prompt, connect to your Cloud SQL instance by running the following:
4. gcloud sql connect myinstance --user=root
5. Enter your root password when prompted. Note: The cursor will not move.
6. Press the Enter key when you're done typing.
7. You should now see the mysql prompt.

## Task 3. Create a database and upload data

1. Create a SQL database called guestbook on your Cloud SQL instance:
``` sql 
CREATE DATABASE guestbook;
```
2. Insert the following sample data into the guestbook database:
``` sql
USE guestbook;
CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255),
    entryID INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(entryID));
    INSERT INTO entries (guestName, content) values ("first guest", "I got here!");
INSERT INTO entries (guestName, content) values ("second guest", "Me too!");
```
3. Now retrieve the data:
``` sql
SELECT * FROM entries;
```


+--------------+-------------------+---------+
| guestName    | content           | entryID |
+--------------+-------------------+---------+
| first guest  | I got here!       |       1 |
| second guest | Me too!           |       2 |
+--------------+-------------------+---------+

