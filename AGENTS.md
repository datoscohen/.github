# Repositorio `.github` de la organización Cohen

Este repo **no contiene código de aplicación**. Su función es definir **parametría global de GitHub y workflows reutilizables para toda la organización**: archivos *community health* por defecto, plantillas de issues y PR, la portada pública de la organización y workflows reutilizables de GitHub Actions en `.github/workflows/`.

Todo lo que se mergea a `master` queda **activo de inmediato en todos los repos de la organización**. No hay build, deploy ni tests. Tratá cada cambio como un cambio de producción: PR + revisión.

## Cómo funcionan los defaults de la organización

- El repo debe ser **público**. Si es privado, GitHub ignora los defaults.
- Un archivo por defecto se usa en cualquier repo de la org (público o privado) que **no tenga su propio archivo de ese tipo**.
- Orden de precedencia de ubicaciones (tanto acá como en el repo consumidor): `.github/` → raíz → `docs/`.
- **Los issue templates son todo-o-nada**: si un repo tiene *cualquier* contenido válido en su propio `.github/ISSUE_TEMPLATE/`, se descarta **todo** el `ISSUE_TEMPLATE/` por defecto de este repo. No hay merge parcial.
- No se puede definir un `LICENSE` por defecto. Va repo por repo.

Referencia: [Creating a default community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).

## Entorno

No hay aplicación, entorno de ejecución ni contenedor que levantar. Los cambios se limitan a la configuración y documentación de GitHub.

## Flujo Git

- Crear ramas `issue/<n>` desde `dev` y abrir los PRs de trabajo hacia `dev`.
- Cuando el cambio llega a `master`, queda activo como default de la organización.
- Seguir las skills del plugin para crear, trabajar y cerrar issues.

## Ubicaciones obligatorias

Estas rutas son impuestas por GitHub y **no son negociables**:

| Contenido | Ruta exacta |
|---|---|
| Workflows reutilizables de la organización | `.github/workflows/` |
| Issue forms y su configuración | `.github/ISSUE_TEMPLATE/` |
| Formularios de discusiones | `.github/DISCUSSION_TEMPLATE/` |
| Botón de sponsor | `.github/FUNDING.yml` |
| Template de pull request | `.github/PULL_REQUEST_TEMPLATE.md` |
| Portada pública de la organización | `profile/README.md` |
| Resto (`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `SUPPORT.md`, `GOVERNANCE.md`) | raíz, `.github/` o `docs/` |

Las carpetas `.github/instructions/`, `.github/prompts/`, `.github/agents/` y `.github/skills/` son personalización de Copilot y **no** son interpretadas por GitHub.

## Convenciones

- **Idioma**: todo el contenido visible para usuarios (títulos, descripciones, labels, textos de formularios) en **español rioplatense**, tono claro y directo. Los nombres de archivo y los `id` de campos, en **inglés kebab-case**.
- **Nombres de archivo**: `kebab-case.yml` para issue forms (ej. `reporte-de-bug.yml`), `SCREAMING_CASE.md` para community health files.
- **Extensión YAML**: siempre `.yml`, nunca `.yaml`.
- **Labels**: un label referenciado en un template solo se aplica si **ya existe** tanto en este repo como en el repo destino. Antes de agregar un label a un template, verificá que exista o pedí que se cree.
- **Cambios acotados**: un PR = un cambio de parametría. Evitá tocar varios templates a la vez.

## Validación

No hay linter ni CI todavía. Antes de proponer un cambio:

1. Verificá que el YAML parsee (cualquier parser local sirve).
2. Revisá el esquema contra [Syntax for issue forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms) y [Common validation errors](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/common-validation-errors-when-creating-issue-forms).
3. Recordá que GitHub muestra los errores de validación de los issue forms como un banner en la pestaña **Issues**, no en el PR.

Para trabajar sobre `.github/ISSUE_TEMPLATE/**` seguí también [issue-forms.instructions.md](.github/instructions/issue-forms.instructions.md).

## Skills del plugin

Usá las skills del plugin para crear, trabajar y cerrar issues. Las instrucciones específicas de este repo están en [repo.instructions.md](.github/instructions/repo.instructions.md).
