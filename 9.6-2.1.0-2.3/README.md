# Version 9.6-2.1.0-2.3

This Docker image contains:

- PostgreSQL 9.6

- PL/v8 2.1

- PostGIS 2.3

This is basically a 'merge' of 2 images:

- clkao/docker-postgres-plv8: https://github.com/clkao/docker-postgres-plv8/blob/master/9.6-2.0/Dockerfile

with update of PL/v8 to 2.1

- mdillon/postgis: https://github.com/appropriate/docker-postgis/blob/master/9.6-2.3/Dockerfile

with fix for issue https://github.com/appropriate/docker-postgis/issues/60

# Running

```
$ docker run -p 5432:5432 geodan/docker-postgres-plv8-postgis:9.6-2.1.0-2.3
```

# Building

```
$ docker build -t geodan/docker-postgres-plv8-postgis:9.6-2.1.0-2.3 .
```

# Testing

```
$ docker run -p 5432:5432 -d geodan/docker-postgres-plv8-postgis:9.6-2.1.0-2.3
$ docker ps
$ docker exec it <container-id> psql -U postgres
postgres=# SELECT extversion FROM pg_extension WHERE extname = 'plv8';
extversion
------------
 2.1.0
 (1 row)
```