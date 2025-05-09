# CLASS: Buenas prácticas en Git

Git es una herramienta fundamental en el desarrollo de software moderno. Para trabajar de manera eficiente en equipo y mantener un código limpio y bien organizado, es crucial seguir ciertas buenas prácticas. A continuación, se describen algunas de las mejores prácticas para trabajar con Git.

## 1. Usa commits pequeños y frecuentes

### Descripción:
Realizar commits pequeños y frecuentes ayuda a mantener el historial de cambios limpio y fácil de seguir. Cada commit debe representar una única unidad de trabajo y debe ser lo más específico posible.

### Ejemplo:
- **Malo:** `git commit -m "Actualización del proyecto"`
- **Bueno:** `git commit -m "Arreglado bug en el formulario de contacto"`

## 2. Escribe mensajes de commit claros y descriptivos

### Descripción:
Los mensajes de commit deben ser claros, descriptivos y explicar el *por qué* de los cambios, no solo el *qué*. Esto facilita la revisión y la comprensión del historial del proyecto.

### Ejemplo de mensaje:
```bash
git commit -m "Corregido error de validación en el campo de email"
```

## 3. Buenas prácticas para ramas
### Descripción
Las ramas permiten aislar trabajo en desarrollo sin afectar la línea principal.

### Normas
Nombre descriptivo: Usa un prefijo y nombre claro, por ejemplo:
```bash
    feature/login
    fix/form-error
```


Ramas de corta vida: Manténlas vivas solo hasta completar la tarea. Elimina tras merge.

### Sincronización:

```bash
    git fetch origin
    git rebase origin/main
```
       


Flujo de trabajo
Paso	Acción	Comando
Crear rama	Nueva característica o corrección	git checkout -b feature/xyz
Trabajar en la rama	Commits atómicos y descriptivos	git commit -m "Descripción corta"
Sincronizar	Rebase sobre main antes de Pull Request	git fetch && git rebase origin/main
Integrar cambios	Abrir Pull Request y hacer merge o rebase	Proceso en plataforma (GitHub/GitLab)
Borrar rama local	Una vez merged	git branch -d feature/xyz
