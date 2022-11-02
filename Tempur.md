# Tempur

## Docker

### start Docker

```
docker-compose up
```

### list containers

```
docker container ls
```

### list images

```
docker image ls
```

### run `pdb` for a Docker container

Command:

```
docker attach <container-id>
```

These 2 lines are needed for the `docker-componse.yml` Docker image config:

```
services:
  # ..
  web:
    # ..
    stdin_open: true
    tty: true
```

After that, you can drop a pdb somewhere and it will work


### Access psql

docker-compose exec db psql -U postgres -d template1 -h localhost -p 5432

### run command agains container

```
docker-compose exec web python manage.py makemigrations
```

`web` is the image

after that is the command

`exec` says to execute a command against an image in a container

### Terminate session

```
SELECT pg_terminate_backend(pg_stat_activity.pid)
FROM pg_stat_activity 
WHERE pg_stat_activity.datname = 'template1'
	AND pid <> pg_backend_pid();
```

### drop all tables

DROP SCHEMA public CASCADE;
CREATE SCHEMA public;


# Standup notes

People involved

- Chibo
- Linda
- Alder - main stake holder
- Jonah
- TJ - anxiety about

## Thur

Size field in Response

Use for Email products recommended

Recommendation algorithm



