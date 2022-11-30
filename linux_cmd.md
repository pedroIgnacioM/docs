### Crear usuario
sudo useradd -m -d /home/username -s /bin/bash username
passwd username
sudo usermod -a -G sudo username
sudo - username

### Buscar palabra en carpeta
grep -nr -B 4 "palabra_buscada" nombre_carpeta/


### instalar base de datos comprimida
sudo -u postgres bash -c "gunzip -c /home/ramcolog/backup_db_ziyu/20220922_05-00_db_ziyu.sql.gz | psql db_ziyu;"

### Compresión de archivos gzip .gz
https://flaviocopes.com/linux-command-gzip/