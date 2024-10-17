# Cloud SQL for PostgreSQL

## Task 1. Create a Cloud SQL instance
1. Click on the menu icon in the top left of the screen to see the Navigation menu (Navigation menu icon).
2. In the left menu of the Console, click on SQL.
3. Click Create Instance.
4. Click Choose PostgreSQL.
5. Create your instance with the following settings:
6. Enter myinstance for Instance ID.
7. Enter a password for the postgres user. Save or remember this password, you'll need it in the next section.
8. For Choose a Cloud SQL edition, select Enterprise.
9. For Region select us-east4.
10. Leave the default values for the other fields.
11. Click Create Instance.
12. You are returned to the instances list. Your new instance is greyed out while it initializes and starts.
13. After a few minutes your instance is created and you can continue to the next section. If it seems to be taking a long time refresh your browser.


## Task 2. Connect to your instance using the psql client in the Cloud Shell
1. In the Cloud Console, click Cloud Shell (Cloud Shell icon) in the upper right corner.
2. Then click Continue if prompted.
3. At the Cloud Shell prompt, connect to your Cloud SQL instance by running:
``` sql
gcloud sql connect myinstance --user=postgres
```

Note: The cursor will not move. Press Enter when you're done typing.

3. You should now see the psql prompt.

## Task 3. Upload data into the postgres database

1. Insert sample data into the postgres database:
``` sql
CREATE TABLE guestbook (guestName VARCHAR(255), content VARCHAR(255),
                        entryID SERIAL PRIMARY KEY);
INSERT INTO guestbook (guestName, content) values ('first guest', 'I got here!');
INSERT INTO guestbook (guestName, content) values ('second guest', 'Me too!');
```
2. Retrieve the data:
``` sql
SELECT * FROM guestbook;
```






