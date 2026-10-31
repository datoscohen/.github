# .github

Este repositorio público mantiene los archivos de salud de proyecto por defecto de la organización Cohen: plantillas de issues y PR, y otros recursos comunitarios.

## Qué contiene

GitHub usa estos defaults en los repositorios de la organización que no tienen su propio archivo del mismo tipo. Los issue templates son todo-o-nada: cualquier template propio reemplaza el conjunto completo de defaults. Además, aloja workflows reutilizables de GitHub Actions en `.github/workflows/` para automatizaciones comunes de la organización.

## Contribuir

Este repo no contiene una aplicación ni requiere un entorno para levantar. Los cambios se trabajan en ramas `issue/<n>` desde `dev`, se validan y se proponen mediante un PR a `dev`. Los cambios que llegan a `master` quedan activos para la organización.

Para las convenciones y validaciones, consultá [AGENTS.md](AGENTS.md).