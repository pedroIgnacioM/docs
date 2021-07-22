<https://www.luisllamas.es/como-instalar-mosquitto-el-broker-mqtt/>

Config de ejemplo

	GNU nano 2.5.3                                  File: /etc/mosquitto/sia-prod.conf

	# Escuchar puerto mqtt
	listener 1887
	# Escuchar el 8097 para websockets sin ssl
	listener 8087
	protocol websockets

	# MQTT sobre ssl
	# listener 8888
	# certfile /etc/letsencrypt/live/mqtt.motionsolutions.cl/cert.pem
	# cafile /etc/letsencrypt/live/mqtt.motionsolutions.cl/chain.pem
	# keyfile /etc/letsencrypt/live/mqtt.motionsolutions.cl/privkey.pem

	# WS sobre SSL
	# listener 8889
	# protocol websockets
	# certfile /etc/letsencrypt/live/mqtt.motionsolutions.cl/cert.pem
	# cafile /etc/letsencrypt/live/mqtt.motionsolutions.cl/chain.pem
	# keyfile /etc/letsencrypt/live/mqtt.motionsolutions.cl/privkey.pem

	## General configs
	log_timestamp true

	# Deshabilitar password
	allow_anonymous true
	# password_file /etc/mosquitto/passwd

	persistence false
	log_dest none