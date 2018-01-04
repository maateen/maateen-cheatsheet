# maateen's cheatsheet
It's my personal cheatsheet. Please feel free to make it usable for you.

## Docker

### Start, Up, Stop, Down a single container

```
$ docker-compose start/up -d/stop/down {container_name}
```

## PostgreSQL

### Install & Run

Run PostgreSQL in docker container:

```
$ docker run -d -p host_port:container_port -v local_path:/path/on/container --name container_name -e POSTGRES_PASSWORD=password postgres
```

Login to the PostgreSQL:

```
$ docker exec -it {CONTAINER ID} psql -U postgres
```

### Create User

```
# CREATE ROLE "db_username" WITH SUPERUSER LOGIN PASSWORD 'password';
```

### Create Database

Create a database named "db_name".

```
# CREATE DATABASE db_name;
```

### Connect to a Database

```
# \c db_name
```

### Backup

After applying the command, we will see the password prompt:

```
$ pg_dump -U db_username -h db_hostname -W db_name > /path/to/backup/file.sql
```

### Restore

After applying the command, we will see the password prompt:

```
$ psql -U db_username -h db_hostname -W -d db_name -f /path/to/backup/file.sql
```
