# Part 2 - Connecting and Configuring MariaDB Database

# Connect to the MariaDB Server and open MySQL CLI with root user, no password set as default.
mysql -u root  >> connected as a root user

# Show default databases in the MariaDB Server.
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
# Choose a database (mysql db) to work with. ⚠️ Caution: We have chosen mysql db as demo purposes, normally database mysql is used by server itself, it shouldn't be changed or altered by the user.
USE mysql;  >>  mysql database choosed


# Show tables within the mysql db.
SHOW TABLES;

+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| event                     |
| func                      |
| general_log               |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| host                      |
| ndb_binlog_index          |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| servers                   |
| slow_log                  |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
# Show users defined in the db server currently.
SELECT * FROM user;
or
SELECT Host, User, Password FROM user;
+-------------------------------+------+----------+
| Host                          | User | Password |
+-------------------------------+------+----------+
| localhost                     | root |          |
| ip-172-31-54-104.ec2.internal | root |          |
| 127.0.0.1                     | root |          |
| ::1                           | root |          |
| localhost                     |      |          |
| ip-172-31-54-104.ec2.internal |      |          |
+-------------------------------+------+----------+

# Close the mysql terminal.
EXIT;

# Setup secure installation of MariaDB.
sudo mysql_secure_installation

# No root password for root so 'Enter' for first question,

# Then set root password: 'root1234' and yes 'y' to all remaining ones.


# Show that you can not log into mysql terminal without password anymore.


# Connect to the MariaDB Server and open MySQL CLI with root user and password (pw:root1234).


# Show that test db is gone.
SHOW DATABASES
+--------------------+
| Database           |
+--------------------+
| information_schema |
| clarusdb           |
| mysql              |
| performance_schema |
+--------------------+

# List the users defined in the server and show that it has now password and its encrypted.
SELECT Host, User, Password FROM user;

+-------------------------------+------+-------------------------------------------+
| Host                          | User | Password                                  |
+-------------------------------+------+-------------------------------------------+
| localhost                     | root | *7FB1F1B8AD1B4CFD578E76ABC1B6ADFF70D04FA0 |
| ip-172-31-27-235.ec2.internal | root | *7FB1F1B8AD1B4CFD578E76ABC1B6ADFF70D04FA0 |
| 127.0.0.1                     | root | *7FB1F1B8AD1B4CFD578E76ABC1B6ADFF70D04FA0 |
| ::1                           | root | *7FB1F1B8AD1B4CFD578E76ABC1B6ADFF70D04FA0 |
+-------------------------------+------+-------------------------------------------+

# Create new database named 'clarusdb'.
CREATE DATABASE clarusdb;
USE clarusdb;

# Show newly created database.
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| clarusdb           |
| mysql              |
| performance_schema |
+--------------------+

# Create a user named 'clarususer'.
CREATE USER clarususer2 IDENTIFIED BY "clarus1234";

# Grant permissions to the user clarususer for database clarusdb.
GRANT ALL ON clarusdb.* TO clarususer2 IDENTIFIED BY "clarus1234" WITH GRANT OPTION;

# Update privileges.
FLUSH PRIVILIGES;

# Close the mysql terminal.
EXIT;