# GitFlow: Flujo de Trabajo Profesional con Git 🌿🚀

![GitFlow Diagram](https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg)  
*Diagrama del flujo de trabajo GitFlow - [Fuente: Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)*

## 🔥 ¿Qué es GitFlow?

GitFlow es un **modelo de ramificación estandarizado** para Git que optimiza el desarrollo en equipos. Creado por Vincent Driessen, se centra en:

- ✅ **Ramas principales** (`main` y `develop`)  
- ✅ **Ramas de soporte** (features, releases, hotfixes)  
- ✅ **Control estricto** de versiones en producción  

**Características principales**:
- Utiliza ramas permanentes (`main` y `develop`) y ramas temporales (`feature`, `hotfix`, `release`).
- Facilita la colaboración al asignar roles claros a cada rama.
- Permite gestionar múltiples versiones de un proyecto simultáneamente.

| Elemento         | Descripción                              |
|------------------|------------------------------------------|
| Ramas permanentes| Ramas que siempre existen (`main`, `develop`) |
| Ramas temporales | Ramas creadas para tareas específicas    |


**Ventajas**:  
✔️ Control de versiones preciso  
✔️ Paralelismo en desarrollo  
✔️ Estabilidad en producción  

---

## 🛠️ Estructura Básica

| Rama | Propósito | Duración |
|------|-----------|----------|
| `main` | Versiones estables (producción) | Permanente |
| `develop` | Integración de features | Permanente |
| `feature/*` | Nuevas funcionalidades | Temporal |
| `release/*` | Preparación para producción | Temporal |
| `hotfix/*` | Correcciones urgentes | Temporal |

### Flujo de Trabajo en GitFlow

El flujo de trabajo en GitFlow sigue una estructura clara que he encontrado muy útil para mantener el orden en proyectos complejos:

1. **Desarrollo de una nueva funcionalidad**:
   - Creo una rama `feature` a partir de `develop`.
   - Trabajo en ella y hago commits.
   - Cuando termino, fusiono la rama en `develop`:
     ```bash
     $ git checkout develop
     $ git merge --no-ff feature/nueva-funcionalidad
     $ git branch -d feature/nueva-funcionalidad
     ```

2. **Preparación de un lanzamiento**:
   - Creo una rama `release` desde `develop`.
   - Realizo ajustes finales (correcciones, documentación, etc.).
   - Fusiono en `main` y `develop`, y etiqueto el lanzamiento:
     ```bash
     $ git checkout main
     $ git merge --no-ff release/1.0.0
     $ git tag -a 1.0.0
     $ git checkout develop
     $ git merge --no-ff release/1.0.0
     $ git branch -d release/1.0.0
     ```

3. **Corrección de errores en producción**:
   - Creo una rama `hotfix` desde `main`.
   - Resuelvo el problema y hago commits.
   - Fusiono en `main` y `develop`:
     ```bash
     $ git checkout main
     $ git merge --no-ff hotfix/1.0.1
     $ git tag -a 1.0.1
     $ git checkout develop
     $ git merge --no-ff hotfix/1.0.1
     $ git branch -d hotfix/1.0.1
     ```

**Nota**: El uso de `--no-ff` asegura que se cree un commit de merge, preservando el historial y facilitando el seguimiento.

