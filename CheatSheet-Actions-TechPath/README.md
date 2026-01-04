# 🚀 GitHub Actions + CI/CD + Docker - Cheat Sheet

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-00ADD8?style=for-the-badge&logo=go&logoColor=white)

**Cheat Sheet completo para desarrolladoras** sobre GitHub Actions, CI/CD y Docker. Diseñado para consulta rápida y aprendizaje práctico.

## 📋 Contenido

Este Cheat Sheet cubre:

- **🎯 Conceptos Fundamentales** - CI/CD, Docker, GitHub Actions
- **📝 Sintaxis YAML Esencial** - Estructura de workflows, triggers, jobs
- **🐳 Comandos Docker** - Comandos básicos, Docker Compose, optimización
- **🔄 Workflows Comunes** - Ejemplos prácticos de CI/CD
- **🔐 Secretos y Variables** - Gestión segura de credenciales
- **🚨 Troubleshooting** - Soluciones a errores comunes
- **📚 Recursos** - Documentación oficial y comunidad

## 🌟 Características

- ✨ Diseño moderno y profesional con gradientes
- 📱 Responsive y optimizado para impresión
- 🔗 Navegación rápida con índice interactivo
- ⬆️ Botón flotante para volver arriba
- 🎨 Código con sintaxis resaltada
- 📄 Formato A4 listo para PDF

## 🚀 Uso

### Ver en el Navegador

1. Abre el archivo `index.html` en tu navegador:
   ```bash
   # Opción 1: Abrir directamente
   start index.html  # Windows
   open index.html   # macOS
   xdg-open index.html  # Linux

   # Opción 2: Con servidor local (recomendado)
   npx http-server -p 8080
   ```

2. Navega por el índice haciendo clic en cualquier sección

3. Usa el botón ⬆️ para volver arriba en cualquier momento

### Exportar a PDF

**Método 1: Desde el navegador**
1. Abre `index.html` en tu navegador
2. `Ctrl + P` (Windows) o `Cmd + P` (macOS)
3. Selecciona "Guardar como PDF"
4. Ajustes recomendados:
   - Tamaño: A4
   - Márgenes: Predeterminados
   - Gráficos de fondo: Activado

**Método 2: Usando herramientas automatizadas**
```bash
# Con Playwright
npx playwright pdf index.html cheatsheet.pdf

# Con Puppeteer
node -e "const puppeteer = require('puppeteer'); (async () => { const browser = await puppeteer.launch(); const page = await browser.newPage(); await page.goto('file://${PWD}/index.html'); await page.pdf({path: 'cheatsheet.pdf', format: 'A4'}); await browser.close(); })();"
```

## 📁 Estructura de Archivos

```
CheatSheet-Actions-TechPath/
├── index.html          # Contenido principal del Cheat Sheet
├── styles.css          # Estilos y diseño
└── README.md          # Este archivo
```

## 🎨 Personalización

### Colores

Los colores están definidos como variables CSS en `styles.css`:

```css
:root {
    --primary: #ea4f33;      /* Rojo principal */
    --secondary: #4737bb;    /* Azul secundario */
    --accent: #6c63ff;       /* Acento morado */
    --dark: #2a2170;         /* Oscuro */
}
```

### Tipografía

- **Títulos**: Asap Condensed
- **Cuerpo**: Roboto
- **Código**: Consolas, Monaco, Courier New

## 🔧 Tecnologías Utilizadas

- HTML5
- CSS3 (Variables CSS, Flexbox, Grid)
- JavaScript (Vanilla)
- Google Fonts

## 📖 Casos de Uso

Este Cheat Sheet es perfecto para:

- 📚 **Estudiantes** aprendiendo DevOps y CI/CD
- 👩‍💻 **Desarrolladoras** que necesitan consulta rápida
- 🎓 **Formadoras** como material de apoyo
- 📝 **Documentación** de equipos de desarrollo
- 🖨️ **Referencia impresa** en el escritorio

## 🤝 Contribuciones

Si encuentras errores o quieres sugerir mejoras:

1. Abre un issue describiendo el problema o mejora
2. Envía un pull request con tus cambios
3. Asegúrate de mantener el estilo y formato existente

## 📝 Ejemplos de Uso

### Para Proyectos Reales

Todos los ejemplos están basados en el proyecto real **TechPath**:
- [Repositorio TechPath](https://github.com/Irina-Ichim/TechPath)
- Implementación real de GitHub Actions
- Docker multi-stage builds
- CI/CD completo con testing y deployment

### Workflows Incluidos

- ✅ CI básico con tests y linting
- 🐳 Build y push de imágenes Docker
- 🚀 Deploy automático a Render
- 🔄 Pipeline completo CI/CD

## 👩‍🎓 Sobre el Proyecto

**Creado por**: Irina Ichim
**Curso**: IA y DevOps - Factoría F5
**Fecha**: Enero 2025
**Objetivo**: Material educativo para desarrolladoras en formación

## 📄 Licencia

Este material es de uso educativo. Siéntete libre de usarlo, modificarlo y compartirlo con atribución.

---

**💙 Hecho con pasión para la comunidad de desarrolladoras**

¿Preguntas o sugerencias? Contáctame a través de GitHub.
