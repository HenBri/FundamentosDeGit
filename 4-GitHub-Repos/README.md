# Taller de Git & GitHub

## ¿Git y GitHub son lo mismo?

| Git     | GitHub                                                              |
|---------|---------------------------------------------------------------------|
| Sistema de control de versiones. | Plataforma de alojamiento de código en la nube basada en Git. |
| Se ejecuta localmente.           | Permite colaboración remota, seguimiento de cambios y gestión de proyectos. |

---

## ¿GitHub es único?

No. Existen otras plataformas similares:

- **Bitbucket**: centrado en repositorios remotos; creado por Atlassian.
- **GitLab**: basado en la nube con herramientas DevOps integradas.

---

## Repositorios remotos

Un **repositorio remoto** es una copia hospedada en un servidor, que sirve como punto central de sincronización entre varios repositorios locales. GitHub es un ejemplo de este tipo de repositorios.

---

## Navegando por GitHub

GitHub permite gestionar múltiples aspectos del desarrollo desde su interfaz:

- **Repository > Code**: Visualizar el código.
- **Repository > Pull Requests**: Ver y gestionar contribuciones.
- **Repository > Actions**: Automatización CI/CD.
- **Repository > Projects**: Gestión de tareas tipo kanban.
- **Repository > Wiki**: Documentación.
- **Repository > Security**: Análisis de seguridad.
- **Repository > Insights**: Estadísticas y métricas.
- **Repository > Settings**: Configuraciones generales del repositorio.

---

## Enlazar un repositorio local con GitHub

```bash
git remote add origin <url>
git push origin <rama>
```

- `origin` es un alias común para el repositorio remoto principal.
- Es posible usar cualquier nombre de alias.

---

## Generar y usar una llave SSH

1. **Listar llaves existentes:**

```bash
ls -al ~/.ssh
```

2. **Generar una nueva llave:**

```bash
ssh-keygen -t rsa -b 4096 -C "tu.email@gmail.com"
```

3. **Activar el agente SSH:**

```bash
eval "$(ssh-agent -s)"
```

4. **Agregar la llave generada:**

```bash
ssh-add ~/.ssh/id_rsa
```

5. **Copiar y pegar en GitHub:**

```bash
clip < ~/.ssh/id_rsa.pub
```

Luego ir a [GitHub SSH settings](https://github.com/settings/ssh/new) y pegar la clave.

---

## Clonar y escribir en un repositorio remoto

- **Clonar repositorio:**

```bash
git clone <url_repositorio>
```

- **Enviar cambios a una rama:**

```bash
git push origin <rama>
```

---

## Gestión de ramas remotas

- **Ver todas las ramas (locales y remotas):**

```bash
git branch -a
```

- **Cambiar a una rama remota:**

```bash
git switch <rama_remota>
```

- **Eliminar ramas locales que ya no se usan:**

```bash
git remote prune origin
```

---

## Conclusión

Comprender los conceptos de estados de archivos, commits, y la interacción con repositorios remotos en GitHub es esencial para un desarrollo moderno y colaborativo. Esta guía te proporciona una base sólida para gestionar tu código de forma eficiente, segura y profesional.