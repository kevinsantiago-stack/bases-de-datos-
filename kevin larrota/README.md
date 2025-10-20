Autores: Kevin Santiago Larrota Cuervo  
Fecha: 20/10/2025  

# Vídeo 1  
Enlace: [https://youtu.be/4Dko5W96WHg?si=SpMGU5aJJ1JrDwd_](https://youtu.be/4Dko5W96WHg?si=SpMGU5aJJ1JrDwd_)  

# Resumen de los conceptos aprendidos  
- Introducción a qué es Docker: una plataforma que permite empaquetar aplicaciones en contenedores, aislando dependencias y entorno.  
- Concepto de **imagen de contenedor** (container image): artefacto reproducible que contiene el sistema de ficheros, librerías, configuración de la aplicación.  
- Concepto de **contenedor** (container): la instancia en ejecución de una imagen.  
- Cómo se construye una imagen con un archivo `Dockerfile`: pasos `FROM`, `RUN`, `COPY`, `EXPOSE`, `CMD`.  
- Uso de comandos básicos de Docker: `docker build`, `docker run`, `docker images`, `docker ps`.  
- Ventajas: portabilidad, reproducibilidad, escalabilidad, consistencia.  
- Retos: gestión de datos, persistencia, redes, seguridad.  

# Reflexión personal sobre los puntos clave  
- **Ventajas**: Docker simplifica el ciclo de vida de las aplicaciones, eliminando problemas de entorno.  
- **Desafíos**: Persistencia y seguridad siguen siendo temas clave.  
- **Uso práctico**: Ideal para equipos de desarrollo que buscan reproducibilidad y despliegues consistentes.  

# Ejemplo práctico / mini‑proyecto  
```dockerfile
# Dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "index.js"]
```
```js
// index.js
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hola Mundo desde Docker!');
});

app.listen(port, () => {
  console.log(`Servidor escuchando en puerto ${port}`);
});
```
Comandos:
```bash
docker build -t miapp-docker .
docker run -d -p 3000:3000 miapp-docker
```

# Recursos adicionales consultados  
- [Documentación oficial de Docker](https://docs.docker.com/)  
---
# Este mini proyecto crea una aplicación web simple en Node.js
# que muestra "Hola Mundo" y se ejecuta dentro de un contenedor Docker.
# Sirve para aprender cómo construir una imagen Docker personalizada
# y ejecutar una aplicación de forma aislada en cualquier entorno.



# Vídeo 2  
Enlace: [https://youtu.be/CV_Uf3Dq-EU?si=OzZ795q_ViUU1nl9](https://youtu.be/CV_Uf3Dq-EU?si=OzZ795q_ViUU1nl9)  

# Resumen de los conceptos aprendidos  
- Uso de Docker Compose para múltiples servicios.  
- Redes de contenedores.  
- Volúmenes y persistencia de datos.  
- Buenas prácticas: imágenes ligeras y seguras.  
- Seguridad básica: usuario no root, puertos mínimos.  
- Despliegue y monitoreo.  

# Reflexión personal sobre los puntos clave  
- **Ventajas**: Facilita orquestar varios servicios sin configuraciones complejas.  
- **Desafíos**: Aumenta la complejidad de redes y persistencia al escalar.  
- **Uso práctico**: Perfecto para desarrollo y staging; usar Kubernetes si la escala lo requiere.  

# Ejemplo práctico / mini‑proyecto  
```yaml
version: "3.9"
services:
  web:
    build: ./web
    ports:
      - "8000:8000"
    depends_on:
      - db
      - cache
    networks:
      - appnet

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - appnet

  cache:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    networks:
      - appnet

volumes:
  db_data:

networks:
  appnet:
    driver: bridge
```

# Recursos adicionales consultados  
- [Documentación de Docker Compose](https://docs.docker.com/compose/)  
---

# Este mini proyecto define un sistema de tres servicios con Docker Compose:
# una aplicación web, una base de datos PostgreSQL y un servidor de caché Redis.
# Permite practicar cómo conectar múltiples contenedores, manejar redes y volúmenes
# y ejecutar un entorno completo de desarrollo con un solo comando.


# Conclusión general  
Docker facilita la portabilidad y la gestión de entornos reproducibles.  
Compose amplía esta capacidad para múltiples servicios.  
Ambas herramientas simplifican el desarrollo y despliegue moderno, siempre que se acompañen de buenas prácticas de seguridad y mantenimiento.
