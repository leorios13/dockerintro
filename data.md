# Nombre de las imágenes

- Emerson: emersonic/cali-service:v1
- Miguel: mzmiguelwd/miguelimg
- Leonardo: leorios13/cali-service:v1

# Workflow

- docker run -d --name svc-emerson --network emerson -v biblioteca-del-pueblo:/var/log/app -p 1000:8080 emersonic/cali-service:v1
- docker run -d --name svc-miguel --network miguel -v biblioteca-del-pueblo:/var/log/app -p 1001:8080 mzmiguelwd/miguelimg
- docker run -d --name svc-leo --network leo -v biblioteca-del-pueblo:/var/log/app -p 1002:8080 leorios13/cali-service:v1
