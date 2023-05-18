# Configuración NGINX

Ejemplo con mintral

- Crear archivo

touch /etc/nginx/sites-available/mintral


- Ejemplo de archivo

server {
    server_name wisecity-app.kausana.cl;

    client_max_body_size 1510M; # allows file uploads up to 1500 megabytes

    root /opt/wisecity_web/;

    location /static {
        alias /opt/wisecity_web/assets;
        expires 10d;
        access_log off;
        add_header Cache-Control "public";
    }

    location /media {
        alias /opt/wisecity_web/media;
        expires 365d;
    }

    location / {

        proxy_pass http://0.0.0.0:9040;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";

        proxy_redirect     off;
        proxy_set_header   Host $host;
        proxy_set_header   X-Real-IP $remote_addr;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Host $server_name;
    }

}

- Agregar a avalibles
sudo ln -s /etc/nginx/sites-available/mintral /etc/nginx/sites-enabled

- Sintaxis
sudo nginx -t

- Restart
sudo systemctl restart nginx

- Firmar con certbot
sudo certbot --nginx -d mintral-app.kausana.cl

- Referencias

https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-18-04