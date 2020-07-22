# Comandos para PostgreSQL

#### Listar base de datos:
```
$ psql -l
```

### Mostrar todas las configuraciones
```
$ psql -c 'show all'
```

#### Mostrar ayuda para backup:
```
$ pg_dump -?
$ pg_restore -?
$ psql -?
```

#### Backup tipo custom:
```
$ pg_dump -i -h localhost -p 5432 -U postgres -F c -b -v -f "RUTA.backup" NOMBRE_BD

-p, --port=PORT database server port number
-i, --ignore-version proceed even when server version mismatches
-h, --host=HOSTNAME database server host or socket directory
-U, --username=NAME connect as specified database user
-W, --password force password prompt (should happen automatically)
-d, --dbname=NAME connect to database name
-v, --verbose verbose mode
-F, --format=c|t|p output file format (custom, tar, plain text)
-c, --clean clean (drop) schema prior to create
-b, --blobs include large objects in dump
-v, --verbose verbose mode
-f, --file=FILENAME output file name
```

Restore tipo custom:
```
$ pg_restore -i -v -h localhost -p 5432 -U postgres -d NOMBRE_BD "RUTA.backup"

-p, --port=PORT database server port number
-i, --ignore-version proceed even when server version mismatches
-h, --host=HOSTNAME database server host or socket directory
-U, --username=NAME connect as specified database user
-W, --password force password prompt (should happen automatically)
-d, --dbname=NAME connect to database name
-v, --verbose verbose mode
```


####  Restore tipo custom y crear DB:
(creará la bd que se referencia dentro del backup y usa la bd postgres para conectarse):
```
$ pg_restore -i -h localhost -p 5432 -U postgres -C -d postgres -v "RUTA.backup"

-p, --port=PORT database server port number
-i, --ignore-version proceed even when server version mismatches
-h, --host=HOSTNAME database server host or socket directory
-U, --username=NAME connect as specified database user
-W, --password force password prompt (should happen automatically)
-d, --dbname=NAME connect to database name
-v, --verbose verbose mode
-C, --create Create database
```

#### Backup tipo plain:
```
$ pg_dump -i -h localhost -p 5432 -U postgres -F p -b -v -f "RUTA.sql" NOMBRE_BD

-p, --port=PORT database server port number
-i, --ignore-version proceed even when server version mismatches
-h, --host=HOSTNAME database server host or socket directory
-U, --username=NAME connect as specified database user
-W, --password force password prompt (should happen automatically)
-d, --dbname=NAME connect to database name
-v, --verbose verbose mode
-F, --format=c|t|p output file format (custom, tar, plain text)
-c, --clean clean (drop) schema prior to create
-b, --blobs include large objects in dump
-v, --verbose verbose mode
-f, --file=FILENAME output file name
```

#### Restore tipo plain:
```
$ psql -h localhost -p 5432 -U postgres -d NOMBRE_BD -f "RUTA.backup"

-p, --port=PORT database server port number
-h, --host=HOSTNAME database server host or socket directory
-U, --username=NAME connect as specified database user
-W, --password force password prompt (should happen automatically)
-d, --dbname=NAME connect to database name
-f, --file file
```
