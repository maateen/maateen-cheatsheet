# maateen's cheatsheet
It's my personal cheatsheet. Please feel free to make it usable for you.

## PostgreSQL

### Install & Run

Run PostgreSQL in docker container:

```
$ docker run -d -p 5432:5432 --name container_name -e POSTGRES_PASSWORD=password postgres
```

Login to the PostgreSQL:

```
$ docker exec -it {CONTAINER ID} psql -U postgres
```

Create a database named "db_name".

```
# CREATE DATABASE db_name;
```

### Backup

After applying the command, we will see the password prompt:

```
$ pg_dump -U db_username -h db_hostname -W db_name > /path/to/backup/file.sql
```
