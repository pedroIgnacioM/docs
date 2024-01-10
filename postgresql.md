

## Ubicación en debian

/etc/postgresql/15/main/postgresql.conf

## Ejemplo de pg_hba.conf

local   all             postgres                                trust

# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     md5
# IPv4 local connections:
host    all             all             0.0.0.0/0               md5


## postgresql.conf

listen_adress="x"

## Reiniciar postgres

sudo service postgresql restart