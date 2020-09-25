# Part 4 - Creating a Client Instance and Connecting to MariaDB Server Instance Remotely

# Launch EC2 Instance (Ubuntu 20.04) and name it as MariaDB-Client on Ubuntu.

# AMI: Ubuntu 20.04
# Instance Type: t2.micro
# Security Group
#   - SSH           -----> 22    -----> Anywhere
#   - MYSQL/Aurora  -----> 3306  -----> Anywhere

# Connect to EC2 instance with SSH.

# Update instance.
sudo apt update && sudo apt upgrade -y 

# Install the mariadb-client.
sudo apt install mariadb-client -y
mysql --version

# Connect the clarusdb on MariaDB Server on the other EC2 instance (pw:clarus1234).
mysql -h *ec2-18-212-78-77.compute-1.amazonaws.com* -u clarususer2 -p  >> connected to the MariaDB Server

# Show that clarususer can do same db operations on MariaDB Server instance.
SHOW TABLES;
USE clarusdb;
SHOW TABLES;

# Close the mysql terminal.
EXIT;

# DO NOT FORGET TO TERMINATE THE INSTANCES YOU CREATED!!!!!!!!!!