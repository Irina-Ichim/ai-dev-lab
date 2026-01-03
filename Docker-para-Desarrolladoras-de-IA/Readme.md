# 🐳 Docker para Desarrolladoras de IA

> De Junior a Pro: Controlando tus entornos de ejecución

Una guía completa y práctica para dominar Docker, diseñada especialmente para desarrolladoras que trabajan con Java, React y aplicaciones de IA.

## 📋 Descripción

Este proyecto es una documentación interactiva y visualmente atractiva que cubre desde los conceptos fundamentales de Docker hasta técnicas avanzadas de orquestación, networking y buenas prácticas de producción.

## 🎯 Para quién es esta guía

- Desarrolladoras Junior que quieren dar el salto a entornos profesionales
- Programadoras que trabajan con Java Spring Boot y React
- Equipos que necesitan estandarizar sus entornos de desarrollo
- Profesionales de IA que quieren containerizar sus modelos y servicios

## 📚 Contenido

### 1. Fundamentos
- ¿Por qué Docker? El problema que resuelve
- Vocabulario esencial (Imágenes, Contenedores, Volúmenes, Redes)
- Comandos fundamentales y su uso práctico

### 2. Configuración de Entorno
- Diferencias entre Windows (WSL2), macOS y Linux
- Estructura de proyectos con Docker
- Archivo `.dockerignore` y mejores prácticas

### 3. Casos Prácticos
- **Java/Spring Boot**: Dockerfile multietapa optimizado
- **React**: Build con Nginx para producción
- **Docker Compose**: Orquestación de aplicaciones completas

### 4. Networking y CORS
- Comunicación entre contenedores
- Solución de problemas comunes de CORS
- Variables de entorno y configuración

### 5. Producción y Optimización
- Antipatrones comunes y cómo evitarlos
- Checklist de producción
- Herramientas de debugging y monitoreo

### 6. IA como Copilot
- Prompts útiles para generar Dockerfiles
- Integración con proyectos de IA
- FastAPI, TensorFlow y modelos en contenedores

## 🚀 Visualización

Para ver la documentación:

1. Clona este repositorio
2. Abre el archivo `index.html` en tu navegador
3. ¡Disfruta de la experiencia visual!

```bash
git clone <url-del-repositorio>
cd Docker-para-Desarrolladoras-de-IA
# Abre index.html con tu navegador preferido
```

## 🎨 Características

- **Diseño Moderno**: Interfaz limpia y profesional con tipografía optimizada
- **Código Semántico**: HTML5 semántico para mejor accesibilidad
- **Responsive**: Adaptado para diferentes tamaños de pantalla
- **Navegación Intuitiva**: Índice interactivo con anclas a secciones
- **Ejemplos Prácticos**: Código real con comentarios explicativos
- **Visualizaciones**: Diagramas de flujo y arquitectura

## 🛠️ Tecnologías Utilizadas

- HTML5 Semántico
- CSS3 con Variables Personalizadas
- Google Fonts (Roboto + Asap Condensed)
- Estructura modular y mantenible

## 📖 Estructura del Proyecto

```
Docker-para-Desarrolladoras-de-IA/
├── index.html          # Documentación principal
├── styles.css          # Estilos visuales
└── Readme.md          # Este archivo
```

## 💡 Conceptos Clave Cubiertos

- **Imágenes vs Contenedores**: La diferencia fundamental
- **Multi-Stage Builds**: Optimización de tamaño de imágenes
- **Docker Compose**: Orquestación de servicios múltiples
- **Networking**: Comunicación entre contenedores
- **Volúmenes**: Persistencia de datos
- **Seguridad**: Usuarios non-root y variables de entorno
- **Optimización**: Caché de dependencias y .dockerignore

## 🎓 Casos de Uso Cubiertos

### Backend Java + Spring Boot
```dockerfile
# Ejemplo de build multietapa
FROM maven:3.8.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jre-alpine
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

### Frontend React + Nginx
```dockerfile
# Build de React con Nginx
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Orquestación Completa
```yaml
# docker-compose.yml
version: '3.8'
services:
  database:
    image: postgres:15-alpine
    volumes:
      - postgres_data:/var/lib/postgresql/data
  backend:
    build: ./backend
    depends_on:
      - database
  frontend:
    build: ./frontend
    depends_on:
      - backend
```

## ⚠️ Antipatrones a Evitar

- ❌ Usar imágenes `:latest` en producción
- ❌ No crear archivo `.dockerignore`
- ❌ Hardcodear secretos en Dockerfiles
- ❌ Ejecutar contenedores como root
- ❌ Incluir `node_modules` o `target` en la imagen
- ❌ No limpiar imágenes antiguas

## ✅ Mejores Prácticas

- ✓ Usar versiones específicas de imágenes
- ✓ Implementar multi-stage builds
- ✓ Crear usuarios non-root
- ✓ Usar variables de entorno
- ✓ Configurar healthchecks
- ✓ Optimizar el orden de COPY para aprovechar caché
- ✓ Documentar comandos importantes

## 🔧 Herramientas Recomendadas

- **Docker Desktop**: GUI oficial para Windows/Mac
- **LazyDocker**: TUI para terminal
- **Docker Extension (VS Code)**: Gestión desde el IDE
- **dive**: Análisis de capas de imágenes
- **hadolint**: Linter para Dockerfiles

## 📝 Comandos Esenciales

```bash
# Construcción
docker build -t mi-app .

# Ejecución
docker run -p 8080:8080 mi-app

# Compose
docker-compose up --build
docker-compose down -v

# Debugging
docker logs -f <contenedor>
docker exec -it <contenedor> bash

# Limpieza
docker system prune -a
```

## 🤝 Contribuciones

Este proyecto es un recurso educativo. Si encuentras errores o tienes sugerencias para mejorar la documentación, ¡tus contribuciones son bienvenidas!

## 👩‍💻 Autora

**Irina Ichim**
Full-Stack Developer & Tech Lead

- 🌐 Web: www.irina-ichim.com
- 📧 Contacto disponible en el sitio web

## 📅 Versión

**Versión 1.0** - Enero 2026

## 📄 Licencia

Este material está diseñado con fines educativos para ayudar a desarrolladoras a dominar Docker.

---

## 🎯 Objetivos de Aprendizaje

Al completar esta guía, serás capaz de:

1. ✅ Comprender la arquitectura de Docker y sus componentes
2. ✅ Crear Dockerfiles optimizados para Java y React
3. ✅ Orquestar aplicaciones multi-contenedor con Docker Compose
4. ✅ Solucionar problemas de networking y CORS
5. ✅ Aplicar mejores prácticas de seguridad y optimización
6. ✅ Usar Docker en proyectos de IA y Machine Learning
7. ✅ Desplegar aplicaciones containerizadas a producción

---

### 💬 Cita de la Guía

> "Docker no es solo una herramienta de infraestructura, es una herramienta de desarrollo. Si sabes Docker, tu valor en el mercado se multiplica porque eres capaz de entregar software que funciona, no solo código que compila."

---

¡Feliz Dockerización! 🐳✨
