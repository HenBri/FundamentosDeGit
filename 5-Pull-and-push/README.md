# Taller de Git & GitHub

## Introducción

Git es un sistema de control de versiones distribuido que permite gestionar y registrar los cambios realizados en los archivos de un proyecto. GitHub, por su parte, es una plataforma de alojamiento en la nube para proyectos que utilizan Git. Juntos, Git y GitHub forman una poderosa combinación para el desarrollo colaborativo y el control del código fuente. Este README ofrece una guía básica sobre los estados de los archivos en Git, el uso de commits, y cómo trabajar con repositorios remotos en GitHub.

---

## Estados de los archivos en Git

En Git, un archivo puede encontrarse en uno de los siguientes tres estados:

| Estado     | Descripción                                                                 |
|------------|------------------------------------------------------------------------------|
| Modified   | El archivo ha sido creado, eliminado o contiene cambios que no han sido confirmados. |
| Staged     | El archivo ha sido marcado como preparado para ser confirmado en el repositorio local. |
| Committed  | El archivo ya está grabado en el repositorio local, mediante un *commit*.   |

Estos estados permiten a los desarrolladores tener un control detallado sobre qué cambios desean incluir en el historial del proyecto y cuáles no.

---

## ¿Qué es un commit?

Un **commit** es el mecanismo con el cual se registran los cambios dentro del repositorio. Se pueden entender como:

- Fotografías del estado del repositorio en un momento dado.
- Cada fotografía incluye información del autor, fecha, localización, entre otros.
- Un punto de restauración, como en un videojuego, al que se puede volver en caso de error.

Realizar commits con frecuencia ayuda a mantener un historial limpio y organizado, facilitando la colaboración y el seguimiento de errores.

---

## ¿Cómo hago un commit?

Para hacer un commit se deben seguir los siguientes pasos:

1. Modificar los archivos que se desean cambiar.
2. Añadir los archivos al área de preparación con `git add <archivo>`.
3. Confirmar los cambios con `git commit -m "Mensaje descriptivo"`.

> ⚠️ El mensaje del commit es **muy importante**: debe describir claramente qué cambios se realizaron y por qué.

---

## ¿Qué es el HEAD?

**HEAD** es un puntero que señala la posición actual en el historial de commits del repositorio. Puede entenderse como un "usted está aquí" en un mapa. Solo puede haber un HEAD activo a la vez.

Esto es relevante al trabajar con ramas y al retroceder a versiones anteriores del proyecto.

---

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
---

## Push, Pull y Pull Requests

### ¿Cuál es la diferencia entre `git push` y `git pull`?

| Comando   | Descripción                                                                 |
|-----------|------------------------------------------------------------------------------|
| `git push` | Envía los cambios del repositorio local al repositorio remoto.             |
| `git pull` | Descarga los cambios del repositorio remoto al repositorio local.          |

---

### Comandos y experimentos con `git push`

```bash
git push
git push -u origin <rama>
git push --all
git push origin <rama1> <rama2> <ramaN>
git push -f            # ⚠️ Peligroso, puede sobrescribir historial remoto
git push -d origin <rama>  # Borra ramas remotas
```

**Buenas prácticas con `git push`:**
- Evita `-f` a menos que sepas lo que haces.
- Usa `-u` para establecer upstream tracking la primera vez.

---

### Comandos y experimentos con `git pull`

```bash
git pull
git pull --set-upstream origin <rama>
git pull --all
git pull origin <rama1> <rama2> <ramaN>
```

**Conflictos posibles:** Sí, al hacer `git pull`, pueden surgir conflictos si los cambios locales y remotos se contradicen.

---

## ¿Qué es una Pull Request (PR)?

Una **Pull Request (PR)** es una solicitud para integrar cambios desde una rama (generalmente en un fork o una rama de desarrollo) hacia otra rama en el repositorio principal.

### ¿Cómo se crea una PR?

1. Subir tu rama con `git push`.
2. Crear la PR desde:
   - La sugerencia automática de GitHub después del push.
   - La pestaña "Pull Requests" del repositorio en GitHub.

### Consejos para hacer una buena PR

- **Enfócate en una sola cosa.**
- **Explica claramente tus cambios.** Usa imágenes, GIFs o vídeos si es útil.
- **Facilita la revisión.** Cambios pequeños y bien explicados son más fáciles de aprobar.

### Revisar una PR

- Sé constructivo y positivo.
- Da feedback claro y específico.
- Considera el contexto del código, a veces un "parche" cumple una necesidad temporal.

---