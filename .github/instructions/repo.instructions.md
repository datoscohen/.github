---
description: 'Datos propios de .github para las skills comunes: repo, rama, entorno, validación y contexto.'
---

# Datos del repo

| Clave | Valor |
|---|---|
| `Repo` | `datoscohen/.github` |
| `Rama de trabajo` | `issue/<n>` |
| `Entorno` | `Agents` |
| `Versión del plugin` | `0.32.0` |

## Validación

- Parsear el YAML de los issue forms y revisar el esquema vigente de GitHub.
- No hay build, CI ni tests; validar el cambio mediante revisión del PR.

## Alcance

- Los cambios que llegan a `master` activan defaults globales de GitHub.
- Los issue templates son todo-o-nada: si un repo define alguno propio, no recibe estos defaults.
- Los cambios requieren PR y revisión.

## Fuentes

- Leer `.github/instructions/issue-forms.instructions.md` antes de editar formularios.
- Verificar que los labels referenciados existan tanto acá como en el repo destino.

## Documentación

- Actualizar `README.md` y `AGENTS.md` cuando cambien el flujo o las convenciones del repo.
- La documentación funcional en `docs/` queda para un issue separado.

## Contexto técnico

- El repo define community health files y issue forms por defecto para la organización; no contiene código de aplicación.
- Las ramas de issue salen de `dev` con el formato `issue/<n>` y los PRs de trabajo apuntan a `dev`.
