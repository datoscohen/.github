---
description: 'Esquema, convenciones y errores frecuentes al escribir issue forms YAML y config.yml por defecto de la organización.'
applyTo: '.github/ISSUE_TEMPLATE/**'
---

# Issue forms por defecto de la organización

Los archivos de esta carpeta se aplican a **todos los repos de la organización** que no tengan su propio `.github/ISSUE_TEMPLATE/`. Es todo-o-nada: si un repo define el suyo, nada de acá se usa.

## Claves de nivel superior

Obligatorias: `name`, `description`, `body`.

| Clave | Notas |
|---|---|
| `name` | Único entre todos los templates (incluidos los `.md`). Aparece en el selector. |
| `description` | Obligatoria. Aparece en el selector. |
| `title` | Prefijo precargado, ej. `"[Bug]: "`. Dejá el espacio final. |
| `labels` | Array. Solo se aplica si el label **ya existe** en este repo y en el repo destino. |
| `type` | Issue type definido a nivel organización. Preferilo por sobre labels cuando exista. |
| `assignees` | Array de usuarios. Evitar asignar personas en templates globales. |
| `projects` | Formato `owner/número`. Requiere que quien abre el issue tenga permiso de escritura en el proyecto; en templates globales casi siempre es mejor omitirlo y usar el auto-add del proyecto. |
| `body` | Array de elementos del formulario. |

## Tipos de elemento en `body`

- `markdown` — texto fijo, no genera respuesta. Solo `attributes.value`. **No** acepta `id` ni `validations`.
- `input` — una línea. `label`, `description`, `placeholder`, `value`.
- `textarea` — multilínea. Además acepta `render: <lenguaje>` para formatear la respuesta como bloque de código.
- `dropdown` — `options` (lista de strings), `multiple: true` opcional, `default: <índice entero>`.
- `checkboxes` — `options` como lista de objetos `{ label, required }`.
- `upload` — adjuntar archivos/capturas.

`validations.required: true` se aplica a `input`, `textarea`, `dropdown` y `upload`; en `checkboxes` el `required` va por opción.

## Reglas del proyecto

- Poné `id` explícito y en inglés kebab-case a **todo** elemento que capture datos. Los `id` son el contrato para automatizaciones futuras; cambiarlos rompe workflows.
- Los `id` deben ser únicos dentro del archivo y contener solo alfanuméricos, `-` y `_`.
- **No** agregues checkboxes de "busqué duplicados": todos los tildan sin leer y solo suman fricción. Reservá los `checkboxes` obligatorios para confirmaciones con consecuencia real (por ejemplo, no pegar credenciales).
- Usá `markdown` solo si aporta algo; nunca como bienvenida decorativa.
- Mantené los formularios cortos: si un campo no cambia la decisión de triage, no va.
- Textos en español; `id` y nombre de archivo en inglés.

## Errores frecuentes que rompen el formulario

- `render` en un `textarea` **no puede** combinarse con `validations.required: true`.
- Un `body` compuesto únicamente de elementos `markdown` es inválido: necesita al menos un campo de entrada.
- `default` en `dropdown` es un **índice numérico**, no el texto de la opción.
- Dos claves `name` iguales entre templates hacen que GitHub descarte uno.
- Dos puntos sin comillas en `title` o `description` rompen el YAML: `title: "[Bug]: "`.
- Labels inexistentes no fallan ruidosamente, simplemente **no se aplican**.

GitHub reporta estos errores como banner en la pestaña **Issues** del repo, no en el PR. Ver [Common validation errors](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/common-validation-errors-when-creating-issue-forms).

## `config.yml`

No es un template. Controla el selector:

```yaml
blank_issues_enabled: false
contact_links:
  - name: Nombre visible
    url: https://...
    about: Para qué sirve este canal.
```

Si `blank_issues_enabled: false`, asegurate de que exista al menos un template o un `contact_link`, o nadie va a poder abrir issues.
