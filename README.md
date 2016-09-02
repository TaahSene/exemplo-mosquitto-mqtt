# exemplo-mosquitto-mqtt
#### Taynara Sene RA 538515
#### Jordana Nogueira RA 542717
#### Cinthia Silman RA 544590
#### Leandro Cazarini RA 365858

####MQTT = seu principal uso é fazer as máquinas conversarem.
O protocolo MQTT é baseado no TCP/IP. Ele utiliza o paradigma publish/subscribe para a troca de mensagens. Este paradigma utiliza o conceito de tópicos para processar as mensagens, em que cada mensagem é enviada para um determinado tópico. O publisher não envia a mensagem diretamente ao subscriber, diferente dos outros protocolos, mas sim ao broker. Um broker popular que é Mosquitto.

### Instalação servido MQTT 

sudo wget http://repo.mosquitto.org/debian/mosquitto-repo.gpg.key

sudo apt-key add mosquitto-repo.gpg.key

cd /etc/apt/sources.list.d/

sudo wget http://repo.mosquitto.org/debian/mosquitto-wheezy.list

sudo apt-get update

sudo apt-get install mosquitto

sudo apt-get install mosquitto mosquitto-clients python-mosquitto

### Configuração do Servidor

Você deve parar o servidor para alterar o arquivo de configuração.

sudo /etc/init.d/mosquitto stop

##### Acessando o arquivo de configuração 

sudo nano /etc/mosquitto/mosquitto.conf

##### A sua configuração deve ser igual a abaixo:

// Place your local configuration in /etc/mosquitto/conf.d/

// A full description of the configuration file is at
// /usr/share/doc/mosquitto/examples/mosquitto.conf.example

pid_file /var/run/mosquitto.pid

persistence true
persistence_location /var/lib/mosquitto/

log_dest topic


log_type error
log_type warning
log_type notice
log_type information

connection_messages true
log_timestamp true

include_dir /etc/mosquitto/conf.d


### Iniciando o servidor

sudo /etc/init.d/mosquitto start


### Testando o Servidor

Abra uma aba do terminal e utilize o seguinte comando

mosquitto_sub -d -t hello/world

No caso "hello/world" é o topico.

Abra a segunda aba do terminal e utilize o comando abaixo para disparar as mensagens

mosquitto_pub -d -t hello/world -m "Hello from Terminal window 2!"

A saida na primeira aba do terminal deve ser :

Client mosqsub/3014-LightSwarm sending CONNECT

Client mosqsub/3014-LightSwarm received CONNACK

Client mosqsub/3014-LightSwarm sending SUBSCRIBE (Mid: 1, Topic: hello/world, QoS: 0)

Client mosqsub/3014-LightSwarm received SUBACK

Subscribed (mid: 1): 0

Client mosqsub/3014-LightSwarm received PUBLISH (d0, q0, r0, m0, 'hello/world', ... (32 bytes))

Greetings from Terminal window 2








