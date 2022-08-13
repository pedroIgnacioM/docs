
supervisorctl reread
supervisorctl update

/etc/supervisor/conf.d
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


ziyu_celery_worker.conf
[program:ziyu-celery-worker]
directory=/opt/ziyu-nav/
command=/root/.pyenv/versions/ziyu/bin/celery -A traklok.celery worker -l info -Q main_tasks
environment=PATH="/root/.pyenv/versions/ziyu/bin"
autostart=true
autorestart=true
stderr_logfile=/opt/logs/ziyu/ziyu_celery_main_tasks.err.log
stdout_logfile=/opt/logs/ziyu/ziyu_celery_main_tasks.out.log