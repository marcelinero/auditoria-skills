# Changelog

Todos los cambios notables a este proyecto se documentan en este archivo.

El formato sigue [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y este proyecto adhiere a [Semantic Versioning](https://semver.org/lang/es/).

## [No publicado]

## [1.1.0] — 2026-05-24

### Agregado

- Servidor MCP (`mcp/server.py`) que expone las 20 SKILLs como herramientas nativas para clientes compatibles con Model Context Protocol (Claude Desktop, Claude Code, agentes via SDK).
  - Herramienta `listar_skills`: devuelve el catálogo completo con tipos, categorías y marcos normativos.
  - Herramienta `obtener_skill`: carga el contenido completo de una SKILL por nombre.
  - Herramienta `buscar_skills`: filtra por tipo (`proceso`/`especialidad`) y/o marco normativo.
- Documentación del servidor MCP (`mcp/README.md`) con instrucciones de configuración para Claude Desktop (Windows, macOS, Linux), Claude Code CLI y Python directo.
- Sección "Servidor MCP" en el `README.md` principal con quickstart y tabla de herramientas.

## [1.0.0] — 2026-05-01

### Agregado

- Estructura inicial del repositorio para publicación pública.
- 8 SKILLs de proceso transversal:
  - `planeacion-basada-riesgos`
  - `evaluacion-controles`
  - `muestreo`
  - `papeles-trabajo`
  - `comunicacion-hallazgos`
  - `seguimiento-recomendaciones`
  - `aseguramiento-calidad`
  - `analitica-datos`
- 12 SKILLs de especialidad:
  - `auditoria-financiera`
  - `auditoria-operativa`
  - `auditoria-tecnologia-informacion`
  - `auditoria-forense`
  - `auditoria-cumplimiento`
  - `auditoria-esg-sostenibilidad`
  - `auditoria-ciberseguridad`
  - `auditoria-inteligencia-artificial`
  - `auditoria-calidad`
  - `auditoria-ambiental`
  - `auditoria-gestion-desempeno`
  - `auditoria-continua`
- Documentación de uso (`docs/`):
  - Guía de instalación por plataforma.
  - Guía de orquestación de SKILLs.
  - Catálogo de casos de uso por tipo de auditoría.
  - Glosario de términos.
  - Plantilla para crear nuevas SKILLs.
- Tres ejemplos end-to-end en `examples/`.
- Plantillas de *issues* y *pull requests*.
- Catálogo legible por máquina (`catalog.json`).
- `LICENSE` (CC BY-SA 4.0), `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`.
