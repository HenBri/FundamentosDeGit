# CLASS: Hooks, Alias y Trucos en Git

## Introducción

¡Hola! Soy un estudiante entusiasmado con Git, y en este README quiero compartir lo que he aprendido sobre hooks, alias y trucos de Git, basándome en el archivo PDF del taller. Estas herramientas me han ayudado a personalizar y optimizar mi flujo de trabajo en proyectos de desarrollo. Mi objetivo es explicarte de forma clara y con un toque práctico cómo usar estas funcionalidades para hacer tu experiencia con Git más eficiente y divertida.

## Desarrollo

### ¿Qué son los Hooks en Git?

Los hooks son como pequeños ayudantes automáticos en Git. Son scripts que se ejecutan cuando ocurre un evento específico, como hacer un commit o empujar cambios a un servidor. Me parece súper útil que existan hooks tanto del lado del cliente (en mi computadora) como del servidor (en plataformas como GitHub). Esto permite automatizar tareas repetitivas o verificar cosas antes de que se guarden cambios.

| Tipo de Hook | Ubicación | Ejemplo de Uso |
|--------------|-----------|----------------|
| Cliente      | Computadora local | Verificar código antes de un commit |
| Servidor     | Repositorio remoto | Comprobar permisos al recibir cambios |

<!-- Comentario: Aquí entra una imagen + "Diagrama mostrando el flujo de un hook pre-commit ejecutándose antes de guardar un commit." -->

### Hooks del Lado del Cliente

Los hooks del lado del cliente me han parecido geniales para personalizar mi flujo de trabajo. Aquí van los más importantes que aprendí:

- **pre-commit**: Antes de hacer un commit, puedo verificar si mi código cumple ciertas reglas, como un formato correcto.
- **prepare-commit-msg**: Puedo modificar el mensaje del commit automáticamente, añadiendo detalles como el número de tarea.
- **commit-msg**: Perfecto para asegurarme de que los mensajes de commit sigan un estándar, como incluir un ticket de proyecto.
- **post-commit**: Útil para enviar notificaciones, por ejemplo, a un canal de Slack tras un commit.
- **pre-push**: Antes de empujar cambios, puedo ejecutar pruebas para evitar subir código roto.
- **post-checkout/post-merge**: Me ayudan a actualizar mi directorio o limpiar ramas obsoletas tras un checkout o merge.

**Ejemplo**: Un hook `pre-commit` en Bash para verificar el formato del código:
```bash
#!/bin/bash
# Archivo: .git/hooks/pre-commit
if ! npm run lint; then
    echo "Error: Corrige el formato del código antes de hacer commit."
    exit 1
fi
```

<!-- Comentario: Aquí entra una imagen + "Captura de pantalla de un terminal mostrando la ejecución de un hook pre-commit." -->

### Hooks del Lado del Servidor

Los hooks del servidor son más comunes en plataformas como GitHub o GitLab. Me sorprendió cómo se usan para mantener el control de los repositorios remotos:

- **pre-receive**: Verifica que los commits estén bien formados o que el usuario tenga permisos antes de aceptar cambios.
- **update**: Permite bloquear actualizaciones específicas, como evitar cambios en ciertas ramas.
- **post-receive**: Notifica a los usuarios (por correo o UI) cuando se guardan nuevos cambios o actualiza interfaces gráficas.

| Hook | Función Principal |
|------|-------------------|
| pre-receive | Validar commits y permisos |
| update | Control granular de actualizaciones |
| post-receive | Notificaciones y actualizaciones de UI |

### Creando un Hook

Crear un hook es más fácil de lo que pensé. Solo tengo que añadir un script con el nombre del hook (como `pre-commit`) en la carpeta `.git/hooks` de mi repositorio. Puedo usar cualquier lenguaje, como Bash, Python o Node.js, lo que me da mucha libertad para personalizarlo.

**Ejemplo de creación**:
1. Creo el archivo `.git/hooks/pre-commit`.
2. Añado un script en Bash o Python.
3. Le doy permisos de ejecución: `chmod +x .git/hooks/pre-commit`.

### Alias en Git

Los alias son atajos que me ahorran tiempo al usar comandos frecuentes. En lugar de escribir `git status` cada vez, puedo usar `git st`. También puedo crear alias complejos para combinar varios comandos. Esto hace que mi trabajo sea más rápido y cómodo.

**Ejemplo de alias simples**:
```bash
$ git config --global alias.co "commit"
$ git config --global alias.st "status"
```
Ahora, `git co -m "Mensaje"` es lo mismo que `git commit -m "Mensaje"`.

<!-- Comentario: Aquí entra una imagen + "Captura de un terminal mostrando la ejecución de un alias como git st." -->

### Creando un Alias

Para crear un alias, uso el comando `git config`. Me gusta configurarlos como globales para usarlos en todos mis proyectos. Es tan simple como escribir el nombre del alias y el comando que quiero abreviar.

**Ejemplo**:
```bash
$ git config --global alias.lg "log --oneline --graph"
```
Con esto, `git lg` muestra un log visual y compacto.

### Trucos Útiles de Git

El PDF también mencionaba trucos que me han salvado en más de una ocasión. Aquí van mis favoritos:

- **Git Stash**: Guardo cambios temporales cuando quiero cambiar de tarea sin hacer commit.
  ```bash
  $ git stash       # Guarda cambios
  $ git stash -u    # Incluye archivos no rastreados
  $ git stash pop   # Recupera los cambios
  ```
- **Git Cherry-pick**: Copio un commit específico de otra rama. ¡Súper útil para correcciones rápidas!
  ```bash
  $ git cherry-pick <SHA>
  ```
- **Git Bisect**: Me ayuda a encontrar el commit que introdujo un error, como un detective de bugs.
  ```bash
  $ git bisect start
  $ git bisect bad   # Estado actual con error
  $ git bisect good <SHA>  # Commit sin error
  $ git bisect reset # Termina la búsqueda
  ```
- **Modificar un Commit**: Cambio el mensaje de un commit reciente.
  ```bash
  $ git commit --amend -m "Nuevo mensaje"
  ```
- **Recuperar un Archivo**: Extraigo un archivo de un commit o rama específica.
  ```bash
  $ git checkout <SHA> -- archivo.txt
  ```

| Truco | Uso Principal |
|-------|---------------|
| `git stash` | Guardar cambios temporales |
| `git cherry-pick` | Aplicar un commit específico |
| `git bisect` | Encontrar bugs en el historial |
| `git commit --amend` | Modificar mensaje de commit |
| `git checkout <SHA> -- <archivo>` | Recuperar archivo específico |

<!-- Comentario: Aquí entra una imagen + "Captura de un terminal ejecutando git bisect para encontrar un commit con error." -->

## Conclusión

Explorar hooks, alias y trucos de Git ha sido una experiencia increíble como estudiante. Los hooks me permiten automatizar tareas, los alias hacen mi trabajo más rápido, y los trucos me dan soluciones prácticas para problemas comunes. Este README, basado en el taller, resume estas herramientas de forma clara y espero que te motive a probarlas. ¡Git es mucho más que commits, y estas funcionalidades lo hacen aún más poderoso!
