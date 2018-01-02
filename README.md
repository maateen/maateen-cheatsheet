# maateen's cheatsheet
It's my personal cheatsheet. Please feel free to make it usable for you.

## PostgreSQL
### Backup

After applying the command, we will see the password prompt:

```
pg_dump -U db_username -h db_hostname -W db_name > /path/to/backup/file.sql
```
