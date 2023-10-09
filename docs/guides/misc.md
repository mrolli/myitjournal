# Miscellaneous Interesting Stuff

Please find here preserved knowledge that does not (yet) deserves its own page
or is interdisciplanry so that it would fit in more that one place. This includes
topics like...

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
    * [How to support full Unicode in MySQL databases](https://mathiasbynens.be/notes/mysql-utf8mb4) by Mathias Bynens

## OpenSSH ProxyJump and ProxyCommand

**ProxyJump** is available since OpenSSH version 7.5. **ProxyCommand** somewhat
longer. The following examples both establish a connection to the remote server
by using a jump server as a proxy server in between.

    ssh -J user@<jump server> <remote-server>

    ssh -o ProxyCommand="ssh -W %h:%p <jump server>" <remote-server>

The ProxyJump even provides fallback:

    ssh -J <jump server1>,<jump server2>,<jump server3> <remote-server>

You can put this config into your `~/.ssh/config` file:

    Host remoteserver
      HostName demo.test.com
      User dev
      IdentityFile ~/.ssh/id_rs
      Port 2048

      ## sample for ProxyJump
      ProxyJump user@jump.test.com

      ## sample for ProxyCommand
      ProxyCommand ssh -W %h:%p user@jump.test.com

See [How to Use SSH ProxyJump and SSH ProxyCommand](https://goteleport.com/blog/ssh-proxyjump-ssh-proxycommand/)
for more details.
