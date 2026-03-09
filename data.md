# Nombre de las imágenes

- Emerson: emersonic/cali-service:v1
- Miguel: mzmiguelwd/miguelimg
- Leonardo: leorios13/cali-service:v1

# Workflow

## Creación de las redes

- docker network create limonar
- docker network create samanes
- docker network create las-granjas

- docker run -d --name svc-emerson --network limonar -v biblioteca-del-pueblo:/var/log/app -p 1000:8080 emersonic/cali-service:v1
- docker run -d --name svc-miguel --network samanes -v biblioteca-del-pueblo:/var/log/app -p 1001:8080 mzmiguelwd/miguelimg
- docker run -d --name svc-leo --network las-granjas -v biblioteca-del-pueblo:/var/log/app -p 1002:8080 leorios13/cali-service:v1
