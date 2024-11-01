# Setup mysql-server

1. Create user and database
- Step 1:    
    ```sh
    sudo mysql
    ```
- Step 2:
    ```sql
    CREATE DATABASE database_name;
    ```
- Step 3:
    ```sql
    CREATE USER 'username'@'%' IDENTIFIED BY 'yourpassword';
    GRANT ALL PRIVILEGES ON fitness_db.* TO 'username'@'%';
    FLUSH PRIVILEGES;
    ```
2. Config MySql allow connection from the internet
- Step 1: 
    ```sh
    sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
    ```
- Step 2: replace bind-address
    ```sh
    bind-address = 0.0.0.0
    ```
- Step 3: 
    ```sh
    sudo systemctl restart mysql
    sudo ufw allow 3306/tcp
    ```
- Step 4: Security: 
    ```sql
    UPDATE mysql.user SET host='localhost' WHERE user='root';
    FLUSH PRIVILEGES;
    ```


## Setup mysql use SSL
1. Create key and certify
    ```sh
    sudo mysql_ssl_rsa_setup --uid=mysql
    ```
2. Config mysql use SSL
    - Edit file <code>/etc/mysql/my.cnf</code>
    ```
    [mysqld]
    ssl-ca=/var/lib/mysql/ca.pem
    ssl-cert=/var/lib/mysql/server-cert.pem
    ssl-key=/var/lib/mysql/server-key.pem
    ```
    - Restart service
    ```sh
    sudo systemctl restart mysql
    ```
3. Check config and Access permission for user
    ```sql
    SHOW VARIABLES LIKE '%ssl%';
    ```
    - Permission
    ```sql
    CREATE USER 'yourusername'@'%' IDENTIFIED BY 'yourpassword' REQUIRE SSL;
    GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'%' WITH GRANT OPTION;
    FLUSH PRIVILEGES;
    ```
4. Test connection 
    ```sh
    mysql -u yourusername -p -h IP --ssl-mode=REQUIRED     
    ```