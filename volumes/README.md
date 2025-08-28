# Ejecutar servicios de Docker compose

Es necesario ejecutar estos servicios primero para evitar errores al iniciar sus microservicios.

- `redis`
  - `docker compose up -d redis`
- `mongodb`
  - `docker compose up -d mongodb`
- `mysql`
  - `docker compose up -d mysql`
- `postgres`
  - `docker compose up -d postgres`
- `rabbitmq`
  - `docker compose up -d redis`
- `elasticsearch`
  - `docker compose up -d elasticsearch`
  - Puede tomar entre 5 a 10 minutos a elasticsearch para correr el contenedor.
- Todos excepto los microservicios
  - `docker compose up -d redis mongodb mysql postgres rabbitmq elasticsearch kibana`

# Configurando Kibana

- Si se utiliza una imagen de Docker de Kibana superior a la versión 8.10.x, la configuración es un poco diferente.
- Una vez que Elasticsearch esté en ejecución, abra la terminal del contenedor de Elasticsearch y cambie la contraseña de Kibana_system.
  - `curl -s -X POST -u elastic:admin1234 -H "Content-Type: application/json" http://localhost:9200/_security/user/kibana_system/_password -d "{\"password\":\"kibana\"}"`
  - Si la actualización fue exitosa, deberías ver un `{}` en la terminal.
- También desde la terminal de contenedores de Elasticsearch, crea un token de servicio de Kibana:
  - `bin/elasticsearch-service-tokens create elastic/kibana jobber-kibana`.
  - Si se generó el token de cuenta de servicio, se mostrará.
  - Una vez generado, cópialo y agrégalo a la variable de entorno de Kibana `ELASTICSEARCH_SERVICEACCOUNT_TOKEN` dentro de tu archivo de composición de Docker.

# Archivo Heartbeat

- Reemplazar `<nuestra-ip>` con su propia dirección IP dentro del `heartbeat.yml`.

# Ejecutar microservicios

- Puede ejecutar los microservicios utilizando Docker Compose o abriendo una terminal para cada servicio y ejecutando `npm run dev`.
- Personalmente, prefiero ejecutar los microservicios individualmente en la terminal porque me permite monitorear fácilmente los errores que se muestran.
- Cualquiera sea el enfoque que desee utilizar para iniciar los microservicios, asegúrese de que el `servicio de puerta de enlace` sea siempre el último servicio que inicie. Todos los demás servicios deben estar ejecutándose antes de iniciar el `servicio de puerta de enlace`.
