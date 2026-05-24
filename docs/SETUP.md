# Setup Guide - BrightPath Academy

## 📋 Requisitos Previos

- Git instalado
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Editor de código (VS Code, Sublime Text, etc.) - Opcional
- Conocimiento básico de HTML, CSS y JavaScript

## 🚀 Instalación

### 1. Clonar el Repositorio

```bash
git clone https://github.com/ndocyo-ux/brightpathacademy.design.git
cd brightpathacademy.design
```

### 2. Iniciar un Servidor Local

#### Opción A: Usando Python (Recomendado)

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

#### Opción B: Usando Node.js

```bash
# Instalar http-server globalmente (si no lo tienes)
npm install -g http-server

# Iniciar servidor
http-server .
```

#### Opción C: Usar Live Server en VS Code

1. Instala la extensión "Live Server"
2. Click derecho en `index.html`
3. Selecciona "Open with Live Server"

### 3. Acceder a la Aplicación

Abre tu navegador y ve a:
```
http://localhost:8000
```

## 📁 Estructura del Proyecto

```
brightpathacademy.design/
│
├── index.html                 # Página de inicio
├── courses.html              # Listado de cursos
├── dashboard.html            # Dashboard del estudiante
│
├── css/
│   ├── styles.css           # Estilos principales
│   ├── responsive.css       # Estilos responsivos
│   └── themes.css           # Temas alternativos (futuro)
│
├── js/
│   ├── main.js              # Funcionalidad principal
│   ├── course-manager.js    # Gestión de cursos
│   └── user-progress.js     # Seguimiento de progreso
│
├── data/
│   ├── courses.json         # Datos de cursos
│   └── users.json           # Datos de usuarios
│
├── assets/
│   ├── images/              # Imágenes
│   ├── fonts/               # Fuentes personalizadas
│   └── icons/               # Iconos SVG
│
├── docs/
│   ├── SETUP.md             # Esta guía
│   ├── API.md               # Documentación de API
│   └── CONTRIBUTING.md      # Guía de contribución
│
├── README.md                # Información del proyecto
├── package.json             # Configuración npm
└── .gitignore              # Archivos a ignorar en git
```

## 🔧 Configuración

### Variables de Entorno

Crea un archivo `.env` en la raíz del proyecto (opcional):

```bash
APP_NAME=BrightPath Academy
APP_VERSION=1.0.0
API_URL=http://localhost:3000
DEBUG=true
```

### Configuración de Desarrollo

Para el desarrollo local, los datos se almacenan en `localStorage`:

```javascript
// Acceder a datos guardados
const userPrefs = BrightPath.getUserPreference('key');

// Guardar datos
BrightPath.saveUserPreference('key', value);
```

## 🗂️ Archivos Importantes

### index.html
- Página de inicio con hero section
- Características del portal
- Llamadas a la acción (CTAs)

### courses.html
- Listado completo de cursos
- Sistema de búsqueda
- Filtros por nivel de dificultad

### dashboard.html
- Panel de control del estudiante
- Seguimiento de progreso
- Logros y certificados
- Cursos recomendados

### js/main.js
```javascript
// Funciones disponibles globalmente:
BrightPath.fetchCourses()           // Obtener cursos
BrightPath.fetchUserProgress(id)    // Obtener progreso
BrightPath.showNotification(msg)    // Mostrar notificación
BrightPath.saveUserPreference(k,v)  // Guardar preferencia
BrightPath.getUserPreference(k)     // Obtener preferencia
```

### js/course-manager.js
```javascript
// Funciones para gestión de cursos:
CourseManager.courses              // Array de cursos
CourseManager.renderCourses(data)  // Renderizar cursos
CourseManager.enrollCourse(title)  // Inscribirse en curso
```

### js/user-progress.js
```javascript
// Funciones de progreso:
UserProgress.userProgressData       // Datos del usuario
UserProgress.updateCourseProgress() // Actualizar progreso
UserProgress.unlockAchievement()    // Desbloquear logro
UserProgress.calculateStatistics()  // Calcular estadísticas
```

## 🎨 Personalización

### Cambiar Colores

Edita las variables CSS en `css/styles.css`:

```css
:root {
    --primary: #2563eb;        /* Azul principal */
    --secondary: #7c3aed;      /* Morado */
    --success: #10b981;        /* Verde */
    --warning: #f59e0b;        /* Ámbar */
    --error: #ef4444;          /* Rojo */
}
```

### Agregar Nuevos Cursos

Edita `js/course-manager.js` y añade a la array `courses`:

```javascript
{
    id: 9,
    title: 'Tu Nuevo Curso',
    description: 'Descripción del curso',
    icon: '📚',
    level: 'beginner',
    duration: '8 semanas',
    students: 0,
    rating: 4.5,
    instructor: 'Tu Nombre',
    price: 'Gratis'
}
```

### Modificar Textos

- Página de inicio: Edita `index.html` directamente
- Cursos: Modifica `js/course-manager.js`
- Dashboard: Modifica `dashboard.html`

## 🧪 Testing

### Pruebas Manuales

1. **Navegación**: Verifica que todos los enlaces funcionan
2. **Responsividad**: Redimensiona el navegador a diferentes tamaños
3. **LocalStorage**: Abre Dev Tools (F12) → Application → LocalStorage
4. **Consola**: Busca errores en la consola (F12 → Console)

### Testing en Dispositivos Móviles

```bash
# Obtén tu IP local
ipconfig getifaddr en0  # macOS
hostname -I             # Linux
ipconfig                # Windows

# Accede desde tu móvil:
http://[TU_IP]:8000
```

## 🚀 Deploy

### Opción 1: GitHub Pages

1. Habilita GitHub Pages en los ajustes del repositorio
2. Selecciona la rama `main` como fuente
3. El sitio estará disponible en `https://ndocyo-ux.github.io/brightpathacademy.design`

### Opción 2: Netlify

```bash
# Conecta tu repositorio en https://netlify.com
# Netlify automáticamente detectará y deployará tu sitio
```

### Opción 3: Vercel

```bash
# Instala Vercel CLI
npm install -g vercel

# Deploy
vercel
```

## 📚 Recursos Útiles

- [MDN Web Docs](https://developer.mozilla.org/)
- [CSS Tricks](https://css-tricks.com/)
- [JavaScript.info](https://javascript.info/)
- [Can I use?](https://caniuse.com/)

## 🐛 Solución de Problemas

### Puerto 8000 ya en uso

```bash
# Usa otro puerto
python -m http.server 8080
```

### CORS Errors

Asegúrate de usar un servidor HTTP local, no abrir archivos con `file://`

### LocalStorage no funciona

- Verifica que no estés en modo incógnito
- Limpia el caché del navegador
- Revisa la consola para errores

## 📞 Soporte

Si tienes problemas:

1. Revisa los [Issues](https://github.com/ndocyo-ux/brightpathacademy.design/issues)
2. Abre un nuevo issue describiendo el problema
3. Incluye: Sistema operativo, navegador, pasos para reproducir

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver `LICENSE` para más detalles.

---

¡Listo para empezar! 🎉
