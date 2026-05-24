# Guía de Contribución

¡Gracias por tu interés en contribuir a BrightPath Academy! 🌟

## Cómo Contribuir

### Reportar Problemas

Si encuentras un problema, por favor abre un issue con:
- Descripción clara del problema
- Pasos para reproducirlo
- Comportamiento esperado vs actual
- Capturas de pantalla si es relevante

### Sugerir Mejoras

Tenemos entusiasmo por nuevas ideas. Por favor, abre un issue con:
- Descripción detallada de la mejora
- Casos de uso
- Ejemplos de cómo podría verse

### Pull Requests

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## Estándares de Código

### HTML
- Usa HTML5 semántico
- Mantén la indentación consistente (2 espacios)
- Incluye atributos alt en imágenes
- Usa aria-labels para accesibilidad

### CSS
- Usa clases descriptivas con convención BEM si es posible
- Mantén variables CSS para colores y tamaños reutilizables
- Ordena propiedades alfabéticamente
- Comenta secciones principales

### JavaScript
- Usa ES6+ cuando sea posible
- Documenta funciones con comentarios JSDoc
- Mantén funciones pequeñas y enfocadas
- Usa nombres descriptivos para variables y funciones
- Evita variables globales

### Ejemplo de Comentario JSDoc
```javascript
/**
 * Calcula el progreso del curso
 * @param {number} completed - Lecciones completadas
 * @param {number} total - Total de lecciones
 * @returns {number} Porcentaje de progreso
 */
function calculateProgress(completed, total) {
    return Math.round((completed / total) * 100);
}
```

## Estructura del Proyecto

```
brightpathacademy.design/
├── index.html              # Página principal
├── courses.html            # Listado de cursos
├── dashboard.html          # Dashboard del estudiante
├── css/                    # Estilos
│   ├── styles.css         # Estilos principales
│   ├── responsive.css     # Estilos responsivos
│   └── themes.css         # Temas alternativos
├── js/                    # Scripts JavaScript
│   ├── main.js            # Funcionalidad central
│   ├── course-manager.js  # Gestión de cursos
│   └── user-progress.js   # Seguimiento de progreso
├── data/                  # Datos JSON
│   ├── courses.json       # Datos de cursos
│   └── users.json         # Datos de usuarios
└── docs/                  # Documentación
    ├── SETUP.md           # Guía de instalación
    ├── API.md             # Documentación de API
    └── CONTRIBUTING.md    # Esta guía
```

## Checklist para PRs

- [ ] Mi código sigue los estándares de estilo del proyecto
- [ ] He actualizado la documentación si es necesario
- [ ] He añadido comentarios a código complejo
- [ ] Mi código es responsive y funciona en navegadores modernos
- [ ] He testado mis cambios localmente
- [ ] No hay conflictos con la rama main

## Proceso de Review

1. Al menos un reviewer debe aprobar el PR
2. Todos los tests deben pasar
3. No debe haber conflictos con la rama main
4. Se realizarán cambios si son sugeridos

## Código de Conducta

### Nuestro Compromiso

Nos comprometemos a proporcionar un ambiente acogedor e inclusivo para todos.

### Nuestros Estándares

Esperamos:
- Lenguaje respetuoso e inclusivo
- Crítica constructiva
- Enfoque en lo que es mejor para la comunidad
- Empatía hacia otros colaboradores

### Inaceptable

No toleraremos:
- Lenguaje o conducta sexual
- Acoso o intimidación
- Insultos o ataques personales
- Publicación de información privada sin consentimiento

## Preguntas

¿Tienes preguntas? Abre un issue con la etiqueta `question` o contacta a los mantenedores.

## Licencia

Al contribuir, aceptas que tus contribuciones sean licensiadas bajo la MIT License.

---

¡Gracias por ayudar a hacer de BrightPath Academy un lugar mejor! 🚀
