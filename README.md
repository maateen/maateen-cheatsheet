
# maateen's cheatsheet
It's my personal cheatsheet. Please feel free to make it usable for you.

## Docker

### Start, Up, Stop, Down a single container

```
$ docker-compose start/up -d/stop/down/restart {container_name}
```

## PostgreSQL

### Install & Run

#### In docker container
Run PostgreSQL in docker container:

```
$ docker run -d -p host_port:container_port -v local_path:/path/on/container --name container_name -e POSTGRES_PASSWORD=password postgres
```

Login to the PostgreSQL:

```
$ docker exec -it {CONTAINER ID} psql -U postgres
```

#### Login to a normal Postgresql

```
psql -h db_host -p db_port -U db_username db_name -W
```

### Revoke CONNECT on the template1 database 

To every new database, no user will be able to connect.

```
REVOKE CONNECT ON DATABASE template1 FROM PUBLIC;
```

### Create Super User

```
# CREATE ROLE "db_username" WITH SUPERUSER LOGIN PASSWORD 'password';
```

### Create Normal User

```
# CREATE ROLE "db_username" WITH LOGIN PASSWORD 'password';
```

### Create Database

Create a database named "db_name".

```
# CREATE DATABASE "db_name";
```

### Revoke connect to a newly created database

```
REVOKE connect ON DATABASE "database_name" FROM PUBLIC;
```

### Granting privileges on database

```
# grant all privileges on database "db_name" to "username";
```

### Granting privileges on all tables of a database

> Connect to the `db_name` before running the following command:

```
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO "username";
```

### Grant connect to a database

```
GRANT connect ON DATABASE "database_name" TO "rolename";
```

### Change owner of a database

```
ALTER DATABASE "db_name" OWNER TO "db_user";
```

### Connect to a Database

```
# \c db_name
```

### Backup

After applying the command, we will see the password prompt:

```
$ pg_dump -U db_username -h db_hostname --port 5432 -W db_name --schema schema_name > /path/to/backup/file.sql
```

### Restore

After applying the command, we will see the password prompt:

```
$ psql -U db_username -h db_hostname --port 5432 -W -d db_name -f /path/to/backup/file.sql
```

### Create a Sudo User

```
$ username='username'
$ adduser $username
$ usermod -aG sudo $username
$ gpasswd -a $username docker
$ mkdir -p /home/$username/.ssh
$ touch /home/$username/.ssh/authorized_keys
$ chown -R $username:$username /home/$username/
$ nano /home/$username/.ssh/authorized_keys
```
