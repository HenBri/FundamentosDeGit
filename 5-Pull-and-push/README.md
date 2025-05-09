# CLASS: Push & Pull

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