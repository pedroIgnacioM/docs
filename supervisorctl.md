
supervisorctl reread
supervisorctl update

cat /etc/supervisor/conf.d
chmod +x

<https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps>


ziyu_celery_beat.conf
[program:ziyu-celery-beat]
directory=/opt/ziyu-nav/
command=/root/.pyenv/versions/ziyu/bin/celery -A traklok.celery_staging beat --scheduler django_celery_beat.schedulers:DatabaseScheduler
environment=PATH="/root/.pyenv/versions/ziyu/bin"
autostart=true
autorestart=true
stderr_logfile=/opt/logs/ziyu_nav/celery_beat.err.log
stdout_logfile=/opt/logs/ziyu_nav/celery_beat.out.log


[program:wisecity-celery-worker]
directory=/opt/wisecity_web/
command=/root/.pyenv/versions/wisecity/bin/celery -A traklok.celery worker -l info -Q main_tasks --discard --max-tasks-per-child=10
environment=PATH="/root/.pyenv/versions/ziyu/bin"
autostart=true
autorestart=true
stderr_logfile=/opt/logs/ziyu/ziyu_celery_main_tasks.err.log
stdout_logfile=/opt/logs/ziyu/ziyu_celery_main_tasks.out.log


[program:wisecity-extractor]
directory=/opt/mintral_web/
command=/opt/mintral_web/mintral/supervisor_extractor_socket_test.sh.sh
autostart=true
autorestart=true
stderr_logfile=/opt/logs/mintral/mintral_subscribe.err.log
stdout_logfile=/opt/logs/mintral/mintral_subscribe.out.log
priority = 50


wisecity_celery_worker.conf
[program:wisecity-celery-worker]
directory=/opt/wisecity_web/
command=/root/.pyenv/versions/wisecity/bin/celery -A wisecity.celery_production worker -l info -Q celery
environment=PATH="/root/.pyenv/versions/wisecity/bin"
autostart=true
autorestart=true
stderr_logfile=/opt/logs/wisecity/celery_main_worker.err.log
stdout_logfile=/opt/logs/wisecity/celery_main_worker.out.log


wisecity_celery_beat.conf
[program:wisecity-celery-beat]
directory=/opt/wisecity_web/
command=/root/.pyenv/versions/wisecity/bin/celery -A wisecity.celery_production beat --scheduler django_celery_beat.schedulers:DatabaseScheduler
environment=PATH="/root/.pyenv/versions/wisecity/bin"
autostart=true
autorestart=true
stderr_logfile=/opt/logs/wisecity/celery_beat.err.log
stdout_logfile=/opt/logs/wisecity/celery_beat.out.log



server {
    server_name kaumon-api.kausana.cl;

    access_log  /var/log/nginx/kaumon.access.log;
    error_log /var/log/nginx/kaumon.error.log;
    client_max_body_size 1510M; # allows file uploads up to 1500 megabytes

    root /opt/kaumon_back/;

    location /static {
        alias /opt/kaumon_back/assets;
        expires 10d;
        access_log off;
        add_header Cache-Control "public";
    }

    location /media {
        alias /opt/kaumon_back/media;
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


    # enable gzip compression
    gzip on;
    gzip_min_length  1100;
    gzip_buffers  4 32k;
    gzip_types    text/plain application/x-javascript text/xml text/css image/svg+xml application/javascript;
    gzip_vary on;
    # end gzip configuration

}

sudo ln -s /etc/nginx/sites-available/kaumon /etc/nginx/sites-enabled/

sudo nano /etc/supervisor/conf.d/kaumon.conf
[program:kaumon]
directory=/opt/kaumon_back/
command=/opt/kaumon_back/kaumon/supervisor_config_test.sh
autostart=true
autorestart=true
stderr_logfile=/opt/logs/kaumon/kaumon.err.log
stdout_logfile=/opt/logs/kaumon/kaumon.out.log

### Celery

https://medium.com/@ksarthak4ever/django-handling-periodic-tasks-with-celery-daaa2a146f14