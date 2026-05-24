# API Documentation - BrightPath Academy

## 📖 Guía de Referencia de API

Esta documentación describe las funciones y APIs disponibles en BrightPath Academy.

## 🎯 Espacio Global: `BrightPath`

Todas las funciones del core están disponibles en el objeto global `BrightPath`.

### Métodos Disponibles

#### 1. fetchCourses()

Obtiene la lista de cursos disponibles.

```javascript
BrightPath.fetchCourses()
    .then(courses => console.log(courses))
    .catch(error => console.error(error));
```

**Retorna:** `Promise<Array<Course>>`

**Ejemplo de respuesta:**
```javascript
[
    {
        id: 1,
        title: 'Desarrollo Web',
        description: 'HTML, CSS, JavaScript',
        icon: '💻',
        level: 'beginner',
        duration: '8 semanas',
        students: 2345,
        rating: 4.8,
        instructor: 'Juan García',
        price: 'Gratis'
    }
]
```

---

#### 2. fetchUserProgress(userId)

Obtiene el progreso de un usuario específico.

```javascript
BrightPath.fetchUserProgress('user_001')
    .then(progress => console.log(progress))
    .catch(error => console.error(error));
```

**Parámetros:**
- `userId` (string): ID único del usuario

**Retorna:** `Promise<Array<ProgressItem>>`

**Ejemplo de respuesta:**
```javascript
[
    {
        courseId: 1,
        progress: 65,
        completedLessons: 13,
        totalLessons: 20,
        lastAccessed: '2024-05-24'
    }
]
```

---

#### 3. showNotification(message, type)

Muestra una notificación al usuario.

```javascript
BrightPath.showNotification('¡Bienvenido!', 'success');
BrightPath.showNotification('Algo salió mal', 'error');
BrightPath.showNotification('Información importante', 'info');
```

**Parámetros:**
- `message` (string): Texto de la notificación
- `type` (string): Tipo ['success', 'error', 'info'] - Default: 'info'

**Retorna:** `void`

---

#### 4. trackEvent(eventName, data)

Registra eventos para análisis.

```javascript
BrightPath.trackEvent('course_enrollment', {
    courseId: 1,
    courseName: 'Desarrollo Web',
    timestamp: new Date().toISOString()
});
```

**Parámetros:**
- `eventName` (string): Nombre del evento
- `data` (object): Datos asociados al evento

**Retorna:** `void`

**Eventos disponibles:**
- `page_view` - Usuario visita una página
- `course_access` - Usuario accede a un curso
- `course_enrollment` - Usuario se inscribe
- `lesson_completed` - Lección completada
- `certificate_earned` - Certificado obtenido

---

#### 5. formatDate(date)

Formatea una fecha en español.

```javascript
BrightPath.formatDate('2024-05-24');
// Retorna: "24 de mayo de 2024"
```

**Parámetros:**
- `date` (string|Date): Fecha a formatear

**Retorna:** `string`

---

#### 6. calculateProgress(completed, total)

Calcula el porcentaje de progreso.

```javascript
const progress = BrightPath.calculateProgress(13, 20);
// Retorna: 65
```

**Parámetros:**
- `completed` (number): Elementos completados
- `total` (number): Total de elementos

**Retorna:** `number` (0-100)

---

### Storage API

#### saveUserPreference(key, value)

Guarda datos en localStorage con prefijo `bpa_`.

```javascript
BrightPath.saveUserPreference('theme', 'dark');
BrightPath.saveUserPreference('language', 'es');
BrightPath.saveUserPreference('userCourses', [1, 2, 3]);
```

**Parámetros:**
- `key` (string): Clave única
- `value` (any): Valor a guardar (se convierte a JSON)

**Retorna:** `void`

---

#### getUserPreference(key, defaultValue)

Obtiene datos guardados.

```javascript
const theme = BrightPath.getUserPreference('theme', 'light');
const courses = BrightPath.getUserPreference('userCourses', []);
```

**Parámetros:**
- `key` (string): Clave a recuperar
- `defaultValue` (any): Valor por defecto si no existe

**Retorna:** `any`

---

#### clearAllPreferences()

Borra todas las preferencias guardadas.

```javascript
BrightPath.clearAllPreferences();
```

**Retorna:** `void`

---

## 🎓 Espacio Global: `CourseManager`

Gestión de cursos.

### Propiedades

#### courses

Array con todos los cursos disponibles.

```javascript
console.log(CourseManager.courses);
// Retorna array de 8 cursos
```

---

### Métodos

#### renderCourses(coursesToRender)

Renderiza cursos en el DOM.

```javascript
const filtered = CourseManager.courses.filter(c => c.level === 'beginner');
CourseManager.renderCourses(filtered);
```

**Parámetros:**
- `coursesToRender` (Array<Course>): Cursos a renderizar

**Retorna:** `void`

---

#### enrollCourse(courseTitle)

Inscribe al usuario en un curso.

```javascript
CourseManager.enrollCourse('Desarrollo Web');
```

**Parámetros:**
- `courseTitle` (string): Título del curso

**Retorna:** `void`

---

## 👤 Espacio Global: `UserProgress`

Seguimiento de progreso del usuario.

### Propiedades

#### userProgressData

Objeto con todos los datos del usuario.

```javascript
console.log(UserProgress.userProgressData);
/*
{
    userId: 'user_001',
    name: 'Juan Pérez',
    email: 'juan@example.com',
    enrolledCourses: [...],
    achievements: [...],
    totalHoursLearned: 42,
    certificatesEarned: 3
}
*/
```

---

### Métodos

#### updateCourseProgress(courseId, completedLessons, totalLessons)

Actualiza el progreso de un curso.

```javascript
UserProgress.updateCourseProgress(1, 15, 20);
// Establece progreso al 75%
```

**Parámetros:**
- `courseId` (number): ID del curso
- `completedLessons` (number): Lecciones completadas
- `totalLessons` (number): Total de lecciones

**Retorna:** `void`

---

#### unlockAchievement(type, metadata)

Desbloquea un logro.

```javascript
UserProgress.unlockAchievement('certificate', 'Desarrollo Web');
UserProgress.unlockAchievement('streak', 7);
UserProgress.unlockAchievement('milestone', 'Primer Curso Completado');
```

**Parámetros:**
- `type` (string): Tipo de logro ['certificate', 'streak', 'milestone']
- `metadata` (any): Información adicional

**Retorna:** `void`

---

#### calculateStatistics()

Calcula estadísticas del usuario.

```javascript
const stats = UserProgress.calculateStatistics();
/*
{
    totalProgress: 68,
    completedCourses: 1,
    totalCourses: 3,
    averageProgress: 68,
    learningVelocity: 0.5,
    recommendedNextCourse: {...}
}
*/
```

**Retorna:** `object`

---

## 🔄 Ciclo de Vida

### Al cargar la página

```javascript
// 1. DOMContentLoaded dispara inicialización
document.addEventListener('DOMContentLoaded', function() {
    // 2. Se cargan preferencias del usuario
    const userTheme = BrightPath.getUserPreference('theme');
    
    // 3. Se obtienen cursos
    BrightPath.fetchCourses().then(courses => {
        // 4. Se renderizan en el DOM
        CourseManager.renderCourses(courses);
    });
});
```

---

## 📝 Ejemplos de Uso

### Ejemplo 1: Crear un Sistema de Recomendaciones

```javascript
function getRecommendedCourses() {
    const stats = UserProgress.calculateStatistics();
    const nextCourse = stats.recommendedNextCourse;
    
    if (nextCourse) {
        console.log(`Se recomienda: ${nextCourse.title}`);
        BrightPath.showNotification(
            `Continúa con: ${nextCourse.title}`,
            'info'
        );
    }
}

getRecommendedCourses();
```

---

### Ejemplo 2: Guardar Preferencias de Usuario

```javascript
function setUserPreferences(preferences) {
    const { theme, language, notifications } = preferences;
    
    BrightPath.saveUserPreference('theme', theme);
    BrightPath.saveUserPreference('language', language);
    BrightPath.saveUserPreference('notifications', notifications);
    
    BrightPath.showNotification('Preferencias guardadas', 'success');
}

setUserPreferences({
    theme: 'dark',
    language: 'es',
    notifications: true
});
```

---

### Ejemplo 3: Monitorear Progreso de Curso

```javascript
function completeLesson(courseId) {
    const course = UserProgress.userProgressData
        .enrolledCourses
        .find(c => c.id === courseId);
    
    if (course) {
        const newCompleted = course.completedLessons + 1;
        
        UserProgress.updateCourseProgress(
            courseId,
            newCompleted,
            course.totalLessons
        );
        
        BrightPath.trackEvent('lesson_completed', {
            courseId,
            progress: course.progress
        });
        
        // Verificar si se completó el curso
        if (newCompleted === course.totalLessons) {
            UserProgress.unlockAchievement('certificate', course.title);
        }
    }
}
```

---

## 🔒 Seguridad

### Consideraciones Importantes

1. **LocalStorage no es seguro** - No guardes información sensible
2. **Validación** - Siempre valida datos del usuario
3. **CORS** - Para APIs externas, configura CORS correctamente
4. **XSS Prevention** - Escapar HTML en entrada de usuario

---

## 🔗 Integración con Backend

Para conectar con un servidor:

```javascript
const API_URL = 'https://tu-api.com';

async function fetchCoursesFromBackend() {
    try {
        const response = await fetch(`${API_URL}/api/courses`);
        const courses = await response.json();
        return courses;
    } catch (error) {
        console.error('Error fetching courses:', error);
        BrightPath.showNotification('Error al cargar cursos', 'error');
        return [];
    }
}
```

---

## 📞 Soporte

Para problemas o preguntas sobre la API:

1. Revisa la sección de [Issues](https://github.com/ndocyo-ux/brightpathacademy.design/issues)
2. Abre un nuevo issue con etiqueta `documentation`
3. Incluye: pregunta específica y contexto de uso

---

**Última actualización:** 24 de mayo de 2024
