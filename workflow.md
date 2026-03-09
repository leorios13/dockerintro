# Taller de Docker: Flujo de Trabajo

## 1. Imágenes

- **Emerson:** `emersonic/cali-service:v1`
- **Miguel:** `mzmiguelwd/miguelimg`
- **Leonardo:** `leorios13/cali-service:v1`
- **Laura:** `lauraceleste/lauraimg`

---

## 2. Flujo de Trabajo (Workflow)

### Paso 1: Creación de las Redes

```bash
docker network create granada
docker network create samanes
docker network create las-granjas
docker network create villa-fatima
```

### Paso 2: Creación del Volumen Compartido

```bash
docker volume create biblioteca-del-pueblo
```

### Paso 3: Creación de los Contenedores

```bash
docker run -d --name svc-emerson --network granada -v biblioteca-del-pueblo:/var/log/app -p 1000:8080 emersonic/cali-service:v1
docker run -d --name svc-miguel --network samanes -v biblioteca-del-pueblo:/var/log/app -p 1001:8080 mzmiguelwd/miguelimg
docker run -d --name svc-leo --network las-granjas -v biblioteca-del-pueblo:/var/log/app -p 1002:8080 leorios13/cali-service:v1
docker run -d --name svc-laura --network villa-fatima -v biblioteca-del-pueblo:/var/log/app -p 1003:8080 lauraceleste/lauraimg
```

### Paso 4: Visualización de los Logs

```bash
docker run --rm -v biblioteca-del-pueblo:/data alpine sh -c "tail -n 20 /data/visitas.log"
```

### Paso 5: Pruebas de Conectividad (Llamados a la API)

**Desde el host:**
*(Nota: Reemplazar `[puerto-asignado]` por 1000, 1001, 1002 o 1003)*

```bash
curl http://localhost:[puerto-asignado]
```

**Desde otro contenedor en el mismo barrio:**
*(Nota: Reemplazar `[nombre-de-la-red]` y `[nombre-del-contenedor]` según corresponda)*

```bash
docker run --rm --network [nombre-de-la-red] curlimages/curl -s http://[nombre-del-contenedor]:8080/
```

---

## 3. Limpieza del Entorno (Reset)

```bash
docker rm -f svc-emerson svc-miguel svc-leo svc-laura
docker volume rm biblioteca-del-pueblo
docker network rm granada samanes las-granjas villa-fatima
```
