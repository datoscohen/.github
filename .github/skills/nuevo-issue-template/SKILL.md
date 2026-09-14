---
name: nuevo-issue-template
description: 'Crea o actualiza un issue form YAML por defecto de la organización en .github/ISSUE_TEMPLATE/. Usar cuando se pida un nuevo template o formulario de issues, agregar o quitar campos de uno existente, migrar un template Markdown a YAML forms, o configurar config.yml y contact_links.'
---

# Nuevo issue template de la organización

Workflow para agregar o modificar un issue form por defecto en este repo. Antes de empezar, leé [issue-forms.instructions.md](../../instructions/issue-forms.instructions.md) para el esquema y los errores frecuentes.

## 1. Definir el propósito

Preguntá al usuario (usá la herramienta de preguntas si está disponible) y no avances sin esto:

- ¿Qué tipo de issue cubre? (bug, feature, acceso, consulta, incidente…)
- ¿Quién lo va a completar? (equipo interno vs. externo — cambia el nivel de detalle y el tono)
- ¿Qué información es **imprescindible** para triage? Cada campo obligatorio tiene que justificar su existencia.
- ¿Qué labels o `type` debe aplicar? Confirmá que ya existan en la organización.

## 2. Revisar lo existente

Listá `.github/ISSUE_TEMPLATE/`. Si ya hay un template con propósito solapado, proponé **extenderlo** en vez de crear uno nuevo: más templates en el selector reduce la tasa de uso correcto.

## 3. Escribir el archivo

- Ruta: `.github/ISSUE_TEMPLATE/<nombre-en-ingles-kebab-case>.yml`.
- Partí de [templates/issue-form.yml](templates/issue-form.yml) y borrá lo que no aplique.
- Textos en español, `id` en inglés kebab-case.
- Meta: 4–7 campos. Si te pasás, el formulario se abandona.

## 4. Actualizar `config.yml`

Si es el primer template, creá `.github/ISSUE_TEMPLATE/config.yml`. Decidí explícitamente con el usuario si `blank_issues_enabled` va en `true` o `false`.

## 5. Verificar

- Parseá el YAML localmente.
- Recorré la checklist de errores frecuentes de las instrucciones (`render` + `required`, `default` numérico, `name` duplicado, labels inexistentes).
- Avisá al usuario que: (a) el cambio impacta en **todos** los repos de la org al mergear, (b) los errores de validación aparecen como banner en la pestaña Issues, no en el PR, y (c) cualquier repo con su propio `ISSUE_TEMPLATE/` ignora estos defaults por completo.
