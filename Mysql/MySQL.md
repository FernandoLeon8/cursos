
# MariaDB - PostgreSQL en Linux

## Instalar MariaDB debian


*  :link: [MariaDB Downloads](https://downloads.mariadb.org/mariadb/repositories/#mirror=globotech)
*  :link: [MariaDB tutorials](https://mariadb.com/kb/en/library/training-tutorials/)

Crear en `source.list`

```
# MariaDB 10.2 repository list - created 2018-04-30 01:28 UTC
# http://downloads.mariadb.org/mariadb/repositories/
deb [arch=amd64,i386,ppc64el] http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.2/debian stretch main
deb-src http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.2/debian stretch main

```
Despues

```
sudo apt-get install software-properties-common dirmngr
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xF1656F24C74CD1D8
sudo apt-get update
sudo apt-get install mariadb-server
```

Para añadir password y configurar las opciones de MariaDB:
```
# mysql_secure_installation
```

## Instalar PostgreSql :link: https://www.postgresql.org/

En debian 9

Añadir en el archivo `/etc/apt/sources.list`
```
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
```

Importar la key
```
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

Para que quede de la siguiente mandera:
```
# PostgreSQL
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
# apt-get install postgresql postgresql-client postgresql-contrib libpq-dev
```

### Database Backups

Store mysql root password in `/root/.cnf` Como __root__ se puede acceder. chmod 600

```
[client]
user=root
password=<CONTRASEÑA>
```

### Back Up una DB

```
mysqldump --add-drop-table --database nombredelabasededatos > /home/nombredeusuario/backups/db/$(bin/date '+\%Y-\%m-\%d').sql.bk
```

### Back Up todas las DB
```
mysqldump --all-databases --all-routines > /path/to/fulldump.sql
```

### Restaurar a DB de un Back Up
```
mysql -u root -p [nombredelabasededatos] < archivoDeBackup.sql
```

### Para restaurar dotas las DB
Primero necesitan existir o el archivo debe de contener __CREATE TABLE__
```
mysql -u root -p < archivoDeTodasLasDB.sql
```

### Login MySQL
```
mysql -u root -p -h localhost
```

### Howto's MySql

Mostrar lista de todos usuarios de MySql
```
mysql> SELECT user,host FROM mysql.user;
```

### Mostrar variables MySql/mariadb
```
SHOW VARIABLES LIKE "%version%";
```

### Cambiar contraseña de _root_

1. `mysql -u root -p`
2. `use mysql;`
3. `update user set password=PASSWORD('your_new_password') where User='root';`
4. `flush privileges;`
5. `quit`

#### Mostrar privilegios concedidos de un usuario
1. `mysql> show grants for 'root'@'%';`
2. `SHOW GRANTS FOR 'root'@'localhost';`


#### Muestra las BD
```
mysql> show DATABASES;
```

#### Crea una BD
```
mysql> CREATE DATABASE nombredelabasededatos;
```

#### Borrar una BD
1. `mysql> DROP DATABASE nombredelabasededatos;`
2. `DROP DATABASE IF EXISTS tutorial_database;`

#### Para usar una BD
```
mysql> USE nombredelabasededatos;
```

#### Crear usuario
```
mysql> CREATE USER 'mi_usuario'@'localhost' IDENTIFIED BY 'mi_contraseña';
```

### Dar permisos a una DB a un usuario.
1. `GRANT permission ON database.table TO 'user'@'localhost';`
    - ALL – Allow complete access to a specific database. If a database is not specified, then allow complete access to the entirety of MySQL.
    - CREATE – Allow a user to create databases and tables.
    - DELETE – Allow a user to delete rows from a table.
    - DROP – Allow a user to drop databases and tables.
    - EXECUTE – Allow a user to execute stored routines.
    - GRANT OPTION – Allow a user to grant or remove another user’s privileges.
    - INSERT – Allow a user to insert rows from a table.
    - SELECT – Allow a user to select data from a database.
    - SHOW DATABASES- Allow a user to view a list of all databases.
    - UPDATE – Allow a user to update rows in a table.
2. _Dar permisos a todas las DB_ para un suario -> `GRANT CREATE ON *.* TO 'testuser'@'localhost';`
3. Dar permiso de _borrar_ una DB a un usuario -> `GRANT DROP ON tutorial_database.* TO 'testuser'@'localhost';`
4. Cuando termine de hacer los cambios de permiso, _es una buena práctica volver a cargar todos los privilegios con el comando de descarga_ -> `FLUSH PRIVILEGES;`
5. Mostrar permisos otorgados para un usuario -> `SHOW GRANTS FOR 'testuser'@'localhost';`

### Quitar/revocar permisos de una DB a un usuario.
1. `REVOKE permission ON database.table FROM 'user'@'localhost';`
    - ALL – Allow complete access to a specific database. If a database is not specified, then allow complete access to the entirety of MySQL.
    - CREATE – Allow a user to create databases and tables.
    - DELETE – Allow a user to delete rows from a table.
    - DROP – Allow a user to drop databases and tables.
    - EXECUTE – Allow a user to execute stored routines.
    - GRANT OPTION – Allow a user to grant or remove another user’s privileges.
    - INSERT – Allow a user to insert rows from a table.
    - SELECT – Allow a user to select data from a database.
    - SHOW DATABASES- Allow a user to view a list of all databases.
    - UPDATE – Allow a user to update rows in a table.
2. _Quitar permisos para todas las DB_ a un usuario -> `REVOKE CREATE ON *.* FROM 'testuser'@'localhost';`
3. _Quitar el permiso de eliminar una DB_ -> `REVOKE DROP ON tutorial_database.* FROM 'testuser'@'localhost';`
4. Cuando termine de hacer los cambios de permiso, _es una buena práctica volver a cargar todos los privilegios con el comando de descarga_ -> `FLUSH PRIVILEGES;`
5. Mostrar permisos otorgados para un usuario -> `SHOW GRANTS FOR 'testuser'@'localhost';`

#### Para borrar un usuario.
```
mysql> DROP USER 'usuario';
```

#### Para mostrar las tablas:
```
mysql> SHOW TABLES;
```

#### Para dar permisos desde la consola sobre todas las tablas de una base de datos
```
mysql> GRANT ALL PRIVILEGES ON nombredelabasededatos.* TO 'landani'@'localhost';
```

#### Después de dar o quitar permisos, siempre tendremos que ejecutar el siguiente comando para aplicarlos.
```
mysql> FLUSH PRIVILEGES;
```

#### Para dar permisos desde la consola sobre una tabla concreta de la base de datos
```
mysql> GRANT SELECT,INSERT,UPDATE,DELETE ON database_name.concrete_table TO 'landani'@'%';
```

#### Para quitar permisos desde la consola de mysql, ejecutaremos el siguiente comando. Si queremos afectar a una base de datos, tabla concreta, etc. lo haremos igual que para dar permisos. En este ejemplo afectamos a todas las bases de datos *(*.*)* y quitaremos todos los permisos (`ALL PRIVILEGES`)
```
mysql> REVOKE ALL PRIVILEGES ON *.* FROM 'landani'@'localhost';
```

#### Para saber que BD estoy usando.
```
mysql> SELECT DATABASE(); ------- \s
```

#### Para saber que usuario estoy parado.
```
mysql> SELECT USER(); ------- \s
mysql> SELECT CURRENT_USER;
```

#### Para saber los privilegios de un usuario.
```
mysql> SHOW GRANTS FOR 'root'@'localhost';
```

#### Para ver los privilegios consedidos a una cuenta que se esta que se esta usuando conectada al server
```
SHOW GRANTS;
SHOW GRANTS FOR CURRENT_USER;
SHOW GRANTS FOR CURRENT_USER();
```

#### How to check MySQL Server is running?
```
# mysqladmin -u root -p ping

    Enter password:
    mysqld is alive
```

#### How to Check which MySQL version I am running?
```
# mysqladmin -u root -p version
```

#### How to Find out current Status of MySQL server?
```
# mysqladmin -u root -ptmppassword status
```

#### How to check status of all MySQL Server Variable’s and value’s?
```
# mysqladmin -u root -p extended-status   
```

#### How to see all MySQL server Variables and Values?
```
# mysqladmin  -u root -p variables
```

#### How to check all the running Process of MySQL server?
```
# mysqladmin -u root -p processlist
```

#### How to reload/refresh MySQL Privileges?
```
# mysqladmin -u root -p reload;
# mysqladmin -u root -p refresh
```

#### Como apagar el servidor de MySql dse forma segura
```
# mysqladmin -u root -p shutdown
    Ó
# /etc/init.d/mysqld stop
# /etc/init.d/mysqld start
```

#### Some useful MySQL Flush commands - Following are some useful flush commands with their description.
```
flush-hosts: Flush all host information from host cache.
flush-tables: Flush all tables.
flush-threads: Flush all threads cache.
flush-logs: Flush all information logs.
flush-privileges: Reload the grant tables (same as reload).
flush-status: Clear status variables.

# mysqladmin -u root -p flush-hosts
# mysqladmin -u root -p flush-tables
# mysqladmin -u root -p flush-threads
# mysqladmin -u root -p flush-logs
# mysqladmin -u root -p flush-privileges
# mysqladmin -u root -p flush-status
```

#### How to kill Sleeping MySQL Client Process? - Use the following command to identify sleeping MySQL client process.
```
# mysqladmin -u root -p processlist
```

#### Despues con el siguiente comando se mata el proceso, es el "Id"
```
# mysqladmin -u root -p kill 5
```

#### How to Connect remote mysql server - To connect remote MySQL server, use the -h (host)  with IP Address of remote machine.
```
# mysqladmin  -h 172.16.25.126 -u root -p
```

#### How to start/stop MySQL replication on a slave server? - To start/stop MySQL replication on salve server, use the following commands.
```
# mysqladmin  -u root -p start-slave
# mysqladmin  -u root -p stop-slave
```

#### How to store MySQL server Debug Information to logs? - It tells the server to write debug information about locks in use, used memory and query usage to the MySQL log file including information about event scheduler.
```
# mysqladmin  -u root -p debug
```
asd
