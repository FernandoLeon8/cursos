
#PostgreSQL
## Instalar PostgreSQL Debian 11.1

- Añadir en el archivo /etc/apt/sources.list
```bash
# PostgreSQL
# deb http://apt.postgresql.org/pub/repos/apt/ YOUR_DEBIAN_VERSION_HERE-pgdg main
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

- Importar la key
```bash
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
```
- Instalamos los paquetes de postgresql
```bash
apt-get install postgresql postgresql-client postgresql-contrib libpq-dev
```

## Entrar a PostgreSql y crear usuario y base de tados
```bash
createuser [connection-option...] [option...] [username]
```
- Entrar con el usuario *PostgreSQL* e entrar directo a la terminal interactiva de *PostgreSQL*
```bash
$ sudo -u postgres psql
```
```bash
username #Specifies the name of the PostgreSQL user to be created. This name must be different from all existing roles in this PostgreSQL installation.
-c number--connection-limit=number #Set a maximum number of connections for the new user. The default is to set no limit.
-d--createdb #The new user will be allowed to create databases.
-D--no-createdb #The new user will not be allowed to create databases. This is the default.
-e--echo #Echo the commands that createuser generates and sends to the server.
-E--encrypted #This option is obsolete but still accepted for backward compatibility.
-g role--role=role #Indicates role to which this role will be added immediately as a new member. Multiple roles to which this role will be added as a member can be specified by writing multiple -g switches.
-i--inherit #The new role will automatically inherit privileges of roles it is a member of. This is the default.
-I--no-inherit #The new role will not automatically inherit privileges of roles it is a member of.
--interactive #Prompt for the user name if none is specified on the command line, and also prompt for whichever of the options -d/-D, -r/-R, -s/-S is not specified on the command line. (This was the default behavior up to PostgreSQL 9.1.)
-l--login #The new user will be allowed to log in (that is, the user name can be used as the initial session user identifier). This is the default.
-L--no-login #The new user will not be allowed to log in. (A role without login privilege is still useful as a means of managing database permissions.)
-P--pwprompt #If given, createuser will issue a prompt for the password of the new user. This is not necessary if you do not plan on using password authentication.
-r--createrole #The new user will be allowed to create new roles (that is, this user will have CREATEROLE privilege).
-R--no-createrole #The new user will not be allowed to create new roles. This is the default.
-s--superuser #The new user will be a superuser.
-S--no-superuser #The new user will not be a superuser. This is the default.
-V--version #Print the createuser version and exit.
--replication #The new user will have the REPLICATION privilege, which is described more fully in the documentation for CREATE ROLE.
--no-replication #The new user will not have the REPLICATION privilege, which is described more fully in the documentation for CREATE ROLE.
-?--help #Show help about createuser command line arguments, and exit. createuser also accepts the following command-line arguments for connection parameters:
-h host--host=host #Specifies the host name of the machine on which the server is running. If the value begins with a slash, it is used as the directory for the Unix domain socket.
-p port--port=port #Specifies the TCP port or local Unix domain socket file extension on which the server is listening for connections.
-U username--username=username #User name to connect as (not the user name to create).
-w--no-password #Never issue a password prompt. If the server requires password authentication and a password is not available by other means such as a .pgpass file, the connection attempt will fail. This option can be useful in batch jobs and scripts where no user is present to enter a password.
-W--password #Force createuser to prompt for a password (for connecting to the server, not for the password of the new user). This option is never essential, since createuser will automatically prompt for a password if the server demands password authentication. However, createuser will waste a connection attempt finding out that the server wants a password. In some cases it is worth typing -W to avoid the extra connection attempt.
```
**Opciones para crear una BD**

`createdb [connection-option...] [option...] [dbname [description]]`
```bash
dbname  # Specifies the name of the database to be created. The name must be unique among all PostgreSQL databases in this cluster. The default is to create a database with the same name as the current system user.
description  # Specifies a comment to be associated with the newly created database.
-D tablespace--tablespace=tablespace   #Specifies the default tablespace for the database. (This name is processed as a double-quoted identifier.)
-e--echo  # Echo the commands that createdb generates and sends to the server.
-E encoding--encoding=encoding # Specifies the character encoding scheme to be used in this database. The character sets supported by the PostgreSQL server are described in Section 23.3.1.
-l locale--locale=locale  #Specifies the locale to be used in this database. This is equivalent to specifying both --lc-collate and --lc-ctype.
--lc-collate=locale  # Specifies the LC_COLLATE setting to be used in this database.
--lc-ctype=locale  # Specifies the LC_CTYPE setting to be used in this database.
-O owner--owner=owner # Specifies the database user who will own the new database. (This name is processed as a double-quoted identifier.)
-T template--template=template # Specifies the template database from which to build this database. (This name is processed as a double-quoted identifier.)
-V--version # Print the createdb version and exit.
-?--help # Show help about createdb command line arguments, and exit.
# The options -D, -l, -E, -O, and -T correspond to options of the underlying SQL command CREATE DATABASE; see there for more information about them.
# createdb also accepts the following command-line arguments for connection parameters:
-h host--host=host # Specifies the host name of the machine on which the server is running. If the value begins with a slash, it is used as the directory for the Unix domain socket.
-p port--port=port # Specifies the TCP port or the local Unix domain socket file extension on which the server is listening for connections.
-U username--username=username # User name to connect as.
-w--no-password # Never issue a password prompt. If the server requires password authentication and a password is not available by other means such as a .pgpass file, the connection attempt will fail. This option can be useful in batch jobs and scripts where no user is present to enter a password.
-W--password # Force createdb to prompt for a password before connecting to a database.
# This option is never essential, since createdb will automatically prompt for a password if the server demands password authentication. However, createdb will waste a connection attempt finding out that the server wants a password. In some cases it is worth typing -W to avoid the extra connection attempt.
--maintenance-db=dbname # Specifies the name of the database to connect to when creating the new database. If not specified, the postgres database will be used; if that does not exist (or if it is the name of the new database being created), template1 will be used.
```

- Para entrar a modo consola de PostgreSQL
```bash
$ psql
```
- Entrar con usuario a una BD previamente ya creados, estando posicionados en el usuario postgres
```bash
$ psql -h localhost -U [USUARIO] [NOMBRE_DE_BASE_DE_DATOS]
```
- Para crear un usuario por default
```bash
$ createuser -> ES CREAR USUARIO SIN NINGUN ATRIBUTO
```
- Para crear un usuario de forma interactiva
```bash
$ createuser --interactive mack
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
```
- Crear  usuario __mack__ usando el localhost __lamaquina__ por el puerto __5000__, con atributos especificados
```bash
$ createuser -h lamaquina -p 5000 -S -D -R -e mack
CREATE ROLE mack NOSUPERUSER NOCREATEDB NOCREATEROLE INHERIT LOGIN;
```
- El manejo de roles en PostgreSQL permite diferentes configuraciones, entre ellas estan:
`SUPERUSER/NOSUPERUSER`. Super usuario, privilegios para crear bases de datos y usuarios.
`CREATEDB/NOCREATEDB`. Permite crear bases de datos.
`CREATEROLE/NOCREATEROLE`. Permite crear roles.
`CREATEUSER/NOCREATEUSER`. Permite crear usuarios.
`LOGIN/NOLOGIN`. Este atributo hace la diferencia entre un rol y usuario. Ya que el usuario tiene permisos para acceder a la base de datos a traves de un cliente.
PASSWORD. Permite alterar la contraseña.
`VALID UNTIL`. Expiración de usuarios.
eje-
```bash
ALTER ROLE <nombre del rol> WITH <opciones>
```
- Crear usuario __sin privilegios__ _para crear BD, no crear BD, no crear roles y no es super usuario_
```bash
postgres=# CREATE ROLE <usr_db> NOSUPERUSER NOCREATEDB NOCREATEROLE LOGIN ENCRYPTED PASSWORD '<pwd_usr_db>';
```

- Crear usuario __mack__ como __super usuario__ y asignarle una contraseña
```bash
$ createuser -P -s -e mack
Enter password for new role: xyzzy
Enter it again: xyzzy
CREATE ROLE mack PASSWORD 'md5b5f5ba1a423792b526f799ae4eb3d59e' SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN;
```
- Crear usuario con contraseña encriptada.
```bash
postgres=# CREATE ROLE nombre_de_usuario LOGIN ENCRYPTED PASSWORD 'mypguserpass';
```
- Eliminar un usuario
```bash
postgres=# DROP USER <NOMBRE_USR>;
```
- Para crear una BD
```bash
postgres=# createdb <NOMBRE_DE_BASE_DE_DATOS>;
```
- Crear BD y un __usuario/role__ para esa base de datos dentro de __shell__ de postgresql
```bash
postgres=# CREATE DATABASE mypgdatabase OWNER mypguser;
```

- Eliminar una BD
```bash
postgres=# DROP DATABASE <NAME_DB>; # Delete database
```


__NOTA__: Por recomendación django se realizan los siguientes pasos para que se realisen de forma segura y mas efeiciente Optimizando la configuración de POstgreSQL :link: [Optimizing PostgreSQL’s configuration](https://docs.djangoproject.com/en/1.11/ref/databases/#optimizing-postgresql-s-configuration "Optimizing PostgreSQL’s configuration")

Esto acelerará las operaciones de base de datos de modo que los valores correctos no tengan que ser consultados y configurados cada vez que se establezca una conexión.

Se tiene que establecer la codificación por defecto a UTF-8, que es la que Django espera. También tienes que establecer el régimen de aislamiento de las transacciones de read committed, el cual bloquea la lectura de transacciones no confirmadas. Por último, se tendrá que establecer la zona horaria.
```bash
postgres=# ALTER ROLE [NOMBRE_BD/ROLE] SET default_transaction_isolation TO 'read committed';
postgres=# ALTER ROLE [NOMBRE_BD/ROLE] SET client_encoding TO 'utf8';
postgres=# ALTER ROLE [NOMBRE_BD/ROLE] SET timezone TO 'UTC';
```

- Cambiar/Asignar acceso y permisos al usuario para administrar la BD
```bash
postgres=# GRANT ALL PRIVILEGES ON DATABASE [NOMBRE_BD/ROLE] TO [USUARIO]; # ASIGNAR UNA B.D. A UN USUARIO
```

- Crear BD y un usuario para esa base de datos fuera del shell de PostgreSQL y dentro del usuario postgres(default)
```bash
 createuser mypguser #from regular shell
 createdb -O mypguser mypgdatabase
```

- Cambiar/asignar la contraseña del usuario creado, dentro de la consola de postgresql(PREFERENTEMENTE)
    - `postgres=# ALTER USER [USUARIO] WITH LOGIN ENCRYPTED PASSWORD '[CONTRASENA]';`
    - `postgres=# ALTER ROLE [USUARIO] WITH PASSWORD '[CONTRASENA]';`

### Command Functionality
```bash
$ sudo /etc/init.d/postgresql start Start server (Ubuntu)
$ psql -U postgres  Connect
postgres=# \l   Show databases
postgres=# \h   Help
postgres=# CREATE DATABASE jerry; # Create database
postgres=# DROP DATABASE jerry; # Delete database
postgres=# SET search_path TO schema; # above
Use schema
$ psql -U postgres -d # Use database
postgres=# \c test # Change database
postgres=# \du  # List users
postgres=# \d  # List tables
postgres=# CREATE SCHEMA sausalito; # Create schema
postgres=# \dn  # List schema
postgres=# DROP SCHEMA sausalito; # Drop schema
postgres=# SELECT * FROM sausalito.employees;  # Select rows
postgres=# CREATE TABLE sausalito.employees (id INT); # Create table
postgres=# INSERT INTO sausalito.employees VALUES (1);  # Insert record
postgres=# UPDATE sausalito.employees SET id = 4 WHERE id = 2;  # Update table record
postgres=# DELETE FROM sausalito.employees WHERE id = 3;  # Delete record
postgres=# DROP TABLE sausalito.employees;  # Drop table
postgres=# \q  # Quit from session
```

### Para verificar el usuario creado
```bash
$ psql
$ \du # LISTAR LOS USUARIOS
$ \l # LISTAR LAS BASES DE DATOS CREADAS
$ \dl # DESPLEGAR LAS TABLAS DE LA BD CONECTADA
$ \q # Salir de la consola de postgresql
```

Si se muestra el mensaje `createuser: creation of new role failed: ERROR:  role "postgres" already exists` Y esto en ubuntu seguir con el paso seguiente.

_Let's start off our configuration by working with PostgreSQL. With PostgreSQL we need to create a database, create a user, and grant the user we created access to the database we created. Start off by running the following command:_

_The default database name and database user are called postgres._

`$ sudo su - postgres` *PARA CAMBIAR EL USUARIO postgresql PARA PODER HACER LA CONFIGURACIONES*

_Your terminal prompt should now say_ `postgres@yourserver`. _If this is the case, then run this command to create your database:_
`$ createdb mydb` _BORRAR BASE DE DATOS_: `$ dropdb dbname`

_Your database has now been created and is named_ `mydb` _if you didn't change the command. You can name your database whatever you would like. Now create your database user with the following command:_
`$ createuser` _ES CREAR USUARIO SIN NINGUN ATRIBUTO_

```bash
General - \? # for help with psql commands
\copyright  # show PostgreSQL usage and distribution terms
\g [FILE] or ;  # execute query (and send results to file or |pipe)
\gset [PREFIX]  # execute query and store results in psql variables
\h [NAME]  # help on syntax of SQL commands, * for all commands
\q  quit psql
\watch [SEC]  # execute query every SEC seconds

# Query Buffer
\e [FILE] [LINE]  # edit the query buffer (or file) with external editor
\ef [FUNCNAME [LINE]]  # edit function definition with external editor
\p  # show the contents of the query buffer
\r  # reset (clear) the query buffer
\s [FILE]  # display history or save it to file
\w FILE # write query buffer to file

# Input/Output
\copy ...  # perform SQL COPY with data stream to the client host
\echo [STRING]  # write string to standard output
\i FILE  # execute commands from file
\ir FILE  # as \i, but relative to location of current script
\o [FILE]  # send all query results to file or |pipe
\qecho # [STRING] write string to query output stream (see \o)


# Informational
(options: S = show system objects, + = additional detail)
\d[S+]  # list tables, views, and sequences
\d[S+] NAME  # describe table, view, sequence, or index
\da[S] [PATTERN]   # list aggregates
\db[+] [PATTERN]   # list tablespaces
\dc[S+] [PATTERN]   list conversions
\dC[+] [PATTERN]   # list casts
\dd[S] [PATTERN]   # show object descriptions not displayed elsewhere
\ddp [PATTERN]  # list default privileges
\dD[S+] [PATTERN]  # list domains
\det[+] [PATTERN]  # list foreign tables
\des[+] [PATTERN]  # list foreign servers
\deu[+] [PATTERN]  # list user mappings
\dew[+] [PATTERN]  # list foreign-data wrappers
\df[antw][S+] [PATRN]  # list [only agg/normal/trigger/window] functions
\dF[+] [PATTERN]  # list text search configurations
\dFd[+] [PATTERN]  # list text search dictionaries
\dFp[+] [PATTERN]  # list text search parsers
\dFt[+] [PATTERN]  # list text search templates
\dg[+] [PATTERN]  # list roles
\di[S+] [PATTERN]  # list indexes
\dl  # list large objects, same as \lo_list
\dL[S+] [PATTERN]  # list procedural languages
\dm[S+] [PATTERN]  # list materialized views
\dn[S+] [PATTERN]  # list schemas
\do[S] [PATTERN]  # list operators
\dO[S+] [PATTERN]  # list collations
\dp [PATTERN]  # list table, view, and sequence access privileges
\drds [PATRN1 [PATRN2]]  # list per-database role settings
\ds[S+] [PATTERN]  # list sequences
\dt[S+] [PATTERN]  # list tables
\dT[S+] [PATTERN]  # list data types
\du[+] [PATTERN]  # list roles
\dv[S+] [PATTERN]  # list views
\dE[S+] [PATTERN]  # list foreign tables
\dx[+] [PATTERN]  # list extensions
\dy [PATTERN]  # list event triggers
\l[+] [PATTERN]  # list databases
\sf[+]  # FUNCNAME show a function's definition
\z [PATTERN]  # same as \dp

# Formatting
\a  # toggle between unaligned and aligned output mode
\C  [STRING] # set table title, or unset if none
\f  [STRING] # show or set field separator for unaligned query output
\H  # toggle HTML output mode (currently off)
\pset [NAME [VALUE]]  # set table output option

(NAME := {format|border|expanded|fieldsep|fieldsep_zero|footer|null|

# numericlocale|recordsep|recordsep_zero|tuples_only|title|tableattr|pager})
\t [on|off]  # show only rows (currently off)
\T [STRING]  # set HTML <table> tag attributes, or unset if none
\x [on|off|auto]  # toggle expanded output (currently off)

# Connection
\c[onnect] {[DBNAME|- USER|- HOST|- PORT|-] | conninfo} 

# connect to new database (currently "postgres")
\encoding [ENCODING]  # show or set client encoding
\password [USERNAME]  # securely change the password for a user
\conninfo  # display information about current connection

#Operating System
\setenv NAME [VALUE]  # set or unset environment variable
\timing [on|off]  # toggle timing of commands (currently off)
\! [COMMAND]  # execute command in shell or start interactive shell

# Large Objects
\lo_export LOBOID FILE
\lo_import FILE [COMMENT]
\lo_list
\lo_unlink LOBOID large object operations
```

su postgres y luego psql para acceder a la base de datos.

comando \h; obtengo ayuda sobre el comando.

\l lista las base de datos con su nombre, dueño y la codificación.

\du lista los usuarios de postgres y sus propiedades.

createuser -P -s -d -r -e zabbix crea el usuario zabbix con privilegios de root

psql -h localhost -U zabbix zabbix entramos en Postgres, con el usuario zabbix a la base de datos zabbix

create database zabbix with owner=zabbix encoding='LATIN1'; crea una base de datos con el nombre nombredelaDB cuyo dueño de la base de datos es zabbix y la codificación de la base de datos es LAINT1

alter database zabbix owner to zabbix; el nuevo dueño de la base de datos zabbix es el usuario zabbix

alter user zabbix with SUPERUSER; le doy al usuario zabbix permisos de root

drop database zabbix; borra una base de datos zabbix


alter user zabbix with connection limit 20000; aumento el limite de conexiones a 20000

-