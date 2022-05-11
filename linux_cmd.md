### Crear usuario
sudo useradd -m -d /home/username -s /bin/bash username
passwd username
sudo usermod -a -G sudo username
sudo - username