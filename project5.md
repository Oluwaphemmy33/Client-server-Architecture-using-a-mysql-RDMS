# Client-Server Architecture Using mysql RDMS#
## TASK — Implement a Client-Server Architecture using MySQL Database Management System (DBMS).
### Steps
1. Spin up two Linux-based virtual servers (EC2 instances in AWS) and name them:  server and  client respectively.(Can use userdata to update)
2. Run sudo apt update -y for latest updates on server.
3. Edit Inbound rule on mysql server to allow access to mysql client traffic. MySQL server uses TCP port 3306 by default. Specify inbound traffic from the IP of mysql cient for extra security.
4. on mysql server install MySQL Server software: sudo apt install  `mysql-server -y`
5. On mysql client install MySQL Client software: sudo apt install `mysql-client -y`
6. Edit Inbound rule on mysql server to allow access to mysql client traffic. MySQL server uses TCP port 3306 by default. Specify inbound traffic from the IP of mysql cient for extra security.
7. On the mysql server, create a database ansd a user that have the privilege to access it, first run the script: sudo mysql_secure_installation, Encountered lot of error while running the script | checked on the internet and was able to resolved it by running the command *sudo mysql* command gives an error, you can use the *sudo mysql -p* command.
8. create a user using the command: `'test_user'@'%' IDENTIFIED WITH mysql_native_password BY 'testpasswd'; `
9. create a database using `CREATE DATABASE sample_db;`
10. Then grant privileges to test_user: `GRANT ALL ON test_db.* TO 'test_user'@'%' WITH GRANT OPTION;`
11. Finally, flush privileges and exit mysql : `FLUSH PRIVILEGES;`
12. the mysql server need to be configure to allow remote host, this is achieve using the command: `sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf` | can use vi or nano
13. Restart the mysql service on the server : `sudo systemctl restart mysql`
14. from the mysql client, you can now connect remotely to database on the server  using the mysql utility via ssh: `sudo mysql -u remote_user -h 172.31.3.70 -p`, you will be prompted for password which is testpasswd
15. you can type: `Show databases` to see the sample_db that was created.
16. Want to improve on this by creating table and adding data to the table and perform CRUD operation on the table before finally dropping the table.
