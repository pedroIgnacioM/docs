### Crear usuario
sudo useradd -m -d /home/username -s /bin/bash username
passwd username
sudo usermod -a -G sudo username
sudo - username

### Buscar palabra en carpeta
grep -nr -B 4 "palabra_buscada" nombre_carpeta/