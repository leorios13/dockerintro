# Nombre de las imágenes

- Emerson: emersonic/cali-service:v1
- Miguel: mzmiguelwd/miguelimg
- Leonardo: leorios13/cali-service:v1

# Workflow

1. Creación de las redes

- docker network create granada
- docker network create samanes
- docker network create las-granjas

2. Creación del Volume compartido

- docker volume create biblioteca-del-pueblo

3. Creación de los contenedores basados en las imágenes

- docker run -d --name svc-emerson --network granada -v biblioteca-del-pueblo:/var/log/app -p 1000:8080 emersonic/cali-service:v1
- docker run -d --name svc-miguel --network samanes -v biblioteca-del-pueblo:/var/log/app -p 1001:8080 mzmiguelwd/miguelimg
- docker run -d --name svc-leo --network las-granjas -v biblioteca-del-pueblo:/var/log/app -p 1002:8080 leorios13/cali-service:v1

4. Visualizar los logs

- docker run --rm -v biblioteca-del-pueblo:/data alpine sh -c "tail -n 20 /data/visitas.log"

5. Realizar los llamados a la api

## Desde el host

- curl http://localhost:[puerto-asignado]

## Desde otro contenedor en el mismo barrio

- docker run --rm --network [nombre-de-la-red] curlimages/curl -s http://[nombre-del-contenedor]:[puerto-asignado]/

# Reset

- docker rm -f svc-emerson svc-miguel svc-leo
- docker volume rm biblioteca-del-pueblo
- docker network rm granada samanes las-granjas
