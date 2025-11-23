Perfecto, acá tenés **solo la parte de conexión**, limpia y lista para guardar.

---

# 📄 Cómo Conectarse a MongoDB en Docker mediante SSH Tunnel

## 1. Obtener la IP interna del contenedor MongoDB

En tu VPS:

```sh
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mongodb
```

Ejemplo de salida:

```
172.18.0.5
```

---

## 2. Crear el túnel SSH desde tu Mac

Ejecutá en tu Mac:

```sh
ssh -L 27017:172.18.0.5:27017 -p 40302 root@185.66.141.92
```

* Redirige tu `localhost:27017` → MongoDB dentro del contenedor.
* Mantener la ventana **abierta** mientras usás Mongo.

---

## 3. Conectarse a MongoDB desde tu Mac

### MongoDB Compass / Studio 3T

Connection String:

```
mongodb://MONGO_USERNAME:MONGO_PASSWORD@localhost:27017
```

### mongosh:

```sh
mongosh "mongodb://MONGO_USERNAME:MONGO_PASSWORD@localhost:27017"
```

---

## 4. Verificaciones útiles

### Ver si el túnel está funcionando:

```sh
nc -zv localhost 27017
```

### Probar conexión a Mongo desde el contenedor:

```sh
docker exec -it mongodb mongosh
```

---

Si querés, te lo dejo en PDF, DOCX o Markdown.
