# CLASS: Gestión de Ramas, Merge y Conflictos en Git


<div aling="center">
  <img src="https://git-scm.com/book/en/v2/images/basic-branching-6.png" width="650" alt="Flujo de ramas en Git">
  <br>
  <em>Diagrama de flujo de trabajo con ramas</em>
</div>

## Introducción

EEstas funcionalidades son esenciales para trabajar de forma eficiente en proyectos colaborativos, ya que permiten desarrollar nuevas características de manera aislada, combinar cambios de forma ordenada y solucionar discrepancias entre versiones. Mi objetivo es presentar esta información de manera clara y estructurada, proporcionando ejemplos prácticos y explicaciones que faciliten la comprensión de estos conceptos fundamentales.

## Desarrollo

### Ramas en Git: Desarrollo Paralelo

Las ramas en Git permiten crear líneas independientes de desarrollo dentro de un mismo repositorio, lo que resulta ideal para trabajar en nuevas funcionalidades, correcciones de errores o experimentos sin afectar la rama principal (como `main`). Este enfoque asegura que el código estable permanezca intacto mientras se realizan modificaciones en paralelo.

**Creación y gestión de ramas**:
- Para crear una rama:
  ```bash
  $ git branch nueva-funcion
  ```
- Para cambiar a esa rama:
  ```bash
  $ git switch nueva-funcion
  ```
- O, de forma más eficiente, combinar ambos pasos:
  ```bash
  $ git switch -c nueva-funcion
  ```

| Comando                  | Descripción                     |
|--------------------------|---------------------------------|
| `git branch <nombre>`    | Crea una nueva rama             |
| `git switch <nombre>`    | Cambia a una rama existente     |
| `git switch -c <nombre>` | Crea y cambia a una rama        |


### Merge: Integración de Cambios

El proceso de merge (fusión) permite combinar los cambios de una rama en otra, integrando así el trabajo realizado. Es una operación clave para consolidar desarrollos paralelos, como incorporar una nueva funcionalidad a la rama principal una vez que ha sido probada y aprobada.

**Pasos para realizar un merge**:
1. Aseguro que estoy en la rama destino (por ejemplo, `main`):
   ```bash
   $ git switch main
   ```
2. Combino los cambios de la rama `nueva-funcion`:
   ```bash
   $ git merge nueva-funcion
   ```

Si no hay conflictos, Git creará un nuevo commit de merge automáticamente, preservando el historial de ambas ramas. Existen dos tipos principales de merge:

- **Fast-forward**: Si no hay cambios en la rama destino, Git simplemente mueve el puntero hacia adelante.
- **Merge commit**: Si ambas ramas tienen cambios, Git crea un commit que une ambas historias.

| Tipo de Merge      | Descripción                              |
|--------------------|------------------------------------------|
| Fast-forward      | Avanza el puntero sin crear nuevo commit |
| Merge commit      | Crea un commit que une las ramas         |


### Conflictos: Identificación y Resolución

Los conflictos ocurren cuando Git no puede combinar cambios automáticamente, generalmente porque se han modificado las mismas líneas en ambas ramas de forma diferente. Aunque al principio puede parecer intimidante, resolver conflictos es un proceso manejable con las herramientas adecuadas.

**Ejemplo de un conflicto**:
Supongamos que en `main` y `nueva-funcion` edité el mismo archivo `index.html` en la misma línea. Al intentar fusionar con:
```bash
$ git merge nueva-funcion
```
Git me notificará un conflicto:
```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

**Pasos para resolver un conflicto**:
1. Abro el archivo en conflicto (`index.html`). Git marca las secciones conflictivas así:
   ```
   <<<<<<< HEAD
   <h1>Versión en main</h1>
   =======
   <h1>Versión en nueva-funcion</h1>
   >>>>>>> nueva-funcion
   ```
2. Edito el archivo para decidir qué versión conservar o combino ambas:
   ```
   <h1>Versión combinada: main y nueva-funcion</h1>
   ```
3. Marco el conflicto como resuelto:
   ```bash
   $ git add index.html
   ```
4. Finalizo el merge creando un commit:
   ```bash
   $ git commit
   ```


| Etapa            | Acción                              |
|------------------|-------------------------------------|
| Identificar      | Revisar archivos marcados por Git  |
| Editar           | Resolver manualmente los conflictos|
| Confirmar        | Usar `git add` y `git commit`      |


### Buenas Prácticas para Evitar Conflictos

A lo largo de mi aprendizaje, he identificado algunas prácticas que minimizan la aparición de conflictos:

- **Commits pequeños y frecuentes**: Hacer cambios pequeños y confirmarlos regularmente facilita la integración.
- **Actualizar ramas con frecuencia**: Antes de trabajar en una rama, la actualizo con los últimos cambios de `main`:
  ```bash
  $ git switch nueva-funcion
  $ git merge main
  ```
- **Comunicación en equipo**: Si trabajo con otros, coordinamos quién edita qué archivo o sección.

## Conclusión

Dominar ramas, merge y conflictos en Git ha sido un paso crucial en mi desarrollo como programador. Las ramas me permiten experimentar con libertad, el merge integra mis cambios de manera ordenada, y saber resolver conflictos me da confianza para colaborar en proyectos más grandes. Este README recopila estos conceptos de forma práctica y estructurada, con ejemplos y buenas prácticas que espero te sean útiles. Si estás buscando mejorar tu flujo de trabajo con Git, ¡estás en el lugar correcto para dar el siguiente paso!
