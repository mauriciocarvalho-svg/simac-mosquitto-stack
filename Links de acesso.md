1. Grafana (Para visualizar os dashboards)
Você acessará a interface web do Grafana para criar e visualizar seus gráficos e dashboards.

Endereço: http://localhost:3000 (abra este link no seu navegador)
Usuário: nti (definido em GF_SECURITY_ADMIN_USER no seu .env)
Senha: 1nfr@CUP (definido em GF_SECURITY_ADMIN_PASSWORD no seu .env)


2. InfluxDB (Para gerenciar o banco de dados)
Você pode usar a interface web do InfluxDB para gerenciar seus buckets, tokens, explorar dados com Flux, etc.

Endereço: http://localhost:8086 (abra este link no seu navegador)
Usuário: nti (definido em DOCKER_INFLUXDB_INIT_USERNAME no seu .env)
Senha: 1nfr@CUP (definido em DOCKER_INFLUXDB_INIT_PASSWORD no seu .env)
3. Mosquitto (Broker MQTT)
Este é o endereço que seus dispositivos (como ESP32, sensores, etc.) ou clientes MQTT usarão para se conectar e publicar/assinar mensagens.

Endereço para clientes MQTT (ex: ESP32, MQTT Explorer): localhost (ou o IP da máquina que está rodando o Docker)
Porta padrão: 1883
Porta para WebSockets: 9001


Resumo Rápido
Serviço	Onde Acessar	Endereço	Credenciais (Usuário / Senha)
Grafana	Navegador Web	http://localhost:3000	nti / 1nfr@CUP
InfluxDB	Navegador Web	http://localhost:8086	nti / 1nfr@CUP
Mosquitto	Dispositivos/Clientes MQTT	localhost (ou IP do host)	Depende da sua config mosquitto.conf
Porta: 1883 / 9001	
Observação: O serviço Telegraf não possui um endereço de acesso externo. Ele funciona "nos bastidores", dentro da rede Docker simac_net, coletando dados do Mosquitto (mosquitto:1883) e enviando-os para o InfluxDB (http://influxdb:8086). Você não precisa interagir diretamente com ele.