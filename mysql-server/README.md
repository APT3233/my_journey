# MYSQL SERVER

1. Install package
    ```sh
    sudo apt update
    sudo apt install mysql-server
    ```
    - Set up root password and basic security
        ```sh
        sudo mysql_secure_installation
        ```
2. Login
    ```
    mysql -u <user_name> -p
    ````