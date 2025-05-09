# CLASS: Deshacer Cambios en Git

## Introducción

Como estudiante explorando Git, he preparado este README para explicar cómo deshacer cambios en este sistema de control de versiones, basándome en el archivo PDF proporcionado. Git es una herramienta poderosa para gestionar proyectos, pero a veces cometemos errores o necesitamos revertir cambios. Este documento detalla los casos en los que es necesario deshacer modificaciones y los comandos clave para hacerlo, presentados de forma clara y visual para facilitar el aprendizaje.

## Desarrollo

### Casos para Deshacer Cambios

En mi experiencia aprendiendo Git, he notado que deshacer cambios es útil en varias situaciones comunes. Por ejemplo, cuando un proyecto deja de funcionar tras una modificación, quiero recuperar código eliminado accidentalmente, o necesito restaurar archivos borrados. Estas scenarios reflejan la importancia de conocer las herramientas de Git para corregir errores sin perder el control del proyecto.

| Situación | Descripción |
|-----------|-------------|
| Proyecto no funcional | Un cambio reciente rompe el código. |
| Código eliminado | Necesito recuperar una parte del código borrada. |
| Archivos eliminados | Quiero restaurar archivos eliminados del proyecto. |

<!-- Comentario: Aquí entra una imagen + "Captura de un terminal mostrando un error tras un commit, ilustrando la necesidad de deshacer cambios." -->

### Comandos Destructivos vs. No Destructivos

Algo que me sorprendió al estudiar Git es la diferencia entre comandos destructivos y no destructivos. Los comandos destructivos alteran el historial de commits, lo que puede ser riesgoso si no se usan con cuidado. En cambio, los no destructivos trabajan sobre el historial sin modificarlo, siendo más seguros para corregir errores sin afectar el proyecto.

- **Destructivos**: Modifican el historial de commits (e.g., `git reset --hard`).
- **No destructivos**: Preservan el historial (e.g., `git revert`).

### Uso de `git reset`

El comando `git reset` es uno de los primeros que aprendí para deshacer cambios. Tiene dos opciones principales que me resultaron útiles:

- **Soft**: Conserva los cambios en el área de trabajo, permitiéndome ajustar commits sin perder mi trabajo.
- **Hard**: Descarta todos los cambios, devolviendo el proyecto a un estado anterior. ¡Hay que usarlo con cuidado!

**Ejemplo**:
```bash
$ git reset --soft HEAD~1  # Mantiene cambios, pero deshace el último commit
$ git reset --hard HEAD~1  # Elimina cambios y el último commit
```

<!-- Comentario: Aquí entra una imagen + "Diagrama comparando los efectos de git reset --soft vs. --hard en el historial de commits." -->

### Uso de `git revert`

Me pareció súper útil `git revert` porque crea un nuevo commit que deshace los cambios de un commit anterior, sin alterar el historial. Esto es ideal para proyectos colaborativos, ya que mantiene la trazabilidad. Por ejemplo, si un commit rompió algo, puedo revertirlo sin afectar el trabajo de otros.

**Ejemplo**:
```bash
$ git revert <SHA>  # Crea un nuevo commit que revierte los cambios del commit especificado
```

### Uso de `git checkout`

El comando `git checkout` me permite recuperar código específico de un commit anterior. Es genial para explorar versiones antiguas o restaurar partes de un archivo sin cambiar todo el proyecto. Aunque sé que ahora `git switch` o `git restore` son más modernos, `checkout` sigue siendo útil en muchos casos.

**Ejemplo**:
```bash
$ git checkout <SHA> -- archivo.txt  # Recupera la versión de archivo.txt de un commit específico
```

<!-- Comentario: Aquí entra una imagen + "Captura de pantalla de un terminal ejecutando git checkout para recuperar un archivo." -->

### Comando `git reset --hard` con Referencias

Un comando que me llamó la atención es `git reset --hard`, especialmente cuando se usa con `HEAD~N` o un SHA específico. Esto me permite retroceder varios commits o ir a un punto exacto en el historial, aunque pierdo todos los cambios posteriores. Es como un "botón de reset" para el proyecto, pero hay que estar seguro antes de usarlo.

**Ejemplo**:
```bash
$ git reset --hard HEAD~2  # Retrocede dos commits, descartando cambios
$ git reset --hard <SHA>   # Va a un commit específico, descartando cambios
```

| Comando | Efecto |
|---------|--------|
| `git reset --hard HEAD~N` | Retrocede N commits, elimina cambios. |
| `git reset --hard <SHA>` | Va al commit con el SHA especificado, elimina cambios. |

## Conclusión

Aprender a deshacer cambios en Git ha sido un gran paso en mi camino como estudiante de desarrollo. Comandos como `git reset`, `git revert` y `git checkout` me dan el control para corregir errores y experimentar sin miedo, siempre que entienda sus efectos. Este README resume lo que he aprendido del material proporcionado, y espero que te sirva para manejar tus proyectos con más confianza. ¡Git es una herramienta increíble, y dominarla vale la pena!
