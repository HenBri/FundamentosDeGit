# Taller de Git & GitHub: States y Commits

## Introducción

Git es un sistema de control de versiones distribuido que permite gestionar y registrar los cambios realizados en los archivos de un proyecto. Comprender cómo funcionan los diferentes estados de los archivos y el concepto de los commits es esencial para trabajar de forma efectiva con Git. Este documento explica de manera sencilla y práctica cómo se representan estos estados, qué es un commit, cómo se realiza y qué papel juega el puntero `HEAD`.

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

## Información adicional útil

- Es recomendable hacer commits pequeños y frecuentes en lugar de uno grande y ambiguo.
- Puedes revisar el historial de commits con `git log`.
- Si te equivocas, puedes deshacer cambios con comandos como `git reset`, `git checkout`, o `git revert`, dependiendo del caso.
- Los commits deben formar una narrativa coherente del desarrollo del proyecto.

---

## Conclusión

Entender los estados de los archivos y el proceso de hacer commits es fundamental para trabajar de forma eficiente con Git. Estos conceptos permiten llevar un control claro y preciso del desarrollo, facilitan el trabajo colaborativo y hacen posible la recuperación de versiones anteriores del proyecto en caso de errores. Practicar estos conceptos con ejemplos reales ayudará a consolidar el aprendizaje y a dominar Git con confianza.
