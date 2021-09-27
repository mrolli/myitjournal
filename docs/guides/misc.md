Please find here preserved knowledge that does not (yet) deserves its own page or is interdisciplanry so that it would fit
in more that one place. This includes topics like...

## Charsets

[The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)

!!! tip "Charset and Collation Recommendation for MySQL/MariaDB"
    ```ini

    [client]
    default-character-set = utf8mb4

    [mysql]
    default-character-set = utf8mb4

    [mysqld]
    character-set-client-handshake = FALSE
    collation-server = utf8mb4_unicode_ci
    init-connect = 'SET NAMES utf8mb4 COLLATE utf8mb4_unicode_ci'
    character-set-server = utf8mb4
    ```

    **Further Reading / Sources**:

    * [utf8 vs. utf8mb4](https://www.hydroxi.de/utf8-vs-utf8mb4/)
    * MariaDB KB article on [Setting Character Sets and Collactions](https://mariadb.com/kb/en/library/setting-character-sets-and-collations/)
    * <https://medium.com/@adamhooper/in-mysql-never-use-utf8-use-utf8mb4-11761243e434>
    * <https://stackoverflow.com/questions/47566730/force-mariadb-clients-to-use-utf8mb4>




