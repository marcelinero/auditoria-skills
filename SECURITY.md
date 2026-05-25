# Política de seguridad

## Alcance

Este repositorio contiene únicamente archivos de texto (Markdown, JSON) e instrucciones para agentes de IA. No incluye código ejecutable de aplicación, credenciales, bases de datos ni infraestructura de producción.

El único componente ejecutable es el servidor MCP (`mcp/server.py`), que opera en modo solo lectura sobre los archivos del repositorio.

## Reportar una vulnerabilidad

Si encontrás un problema de seguridad — por ejemplo, una entrada maliciosa que permita leer archivos fuera del repositorio vía el servidor MCP — por favor **no lo publiques como issue público**.

Reportalo de forma privada mediante:

- **GitHub Private Vulnerability Reporting:** usá el botón *"Report a vulnerability"* en la pestaña *Security* de este repositorio.
- **Email:** marcelolinero@hotmail.com

Incluí en tu reporte:
1. Descripción del problema.
2. Pasos para reproducirlo.
3. Impacto potencial.
4. Sugerencia de fix (opcional).

## Tiempos de respuesta

| Evento | Plazo objetivo |
| --- | --- |
| Acuse de recibo | 5 días hábiles |
| Evaluación inicial | 10 días hábiles |
| Fix o plan de mitigación | 30 días hábiles |

## Versiones soportadas

Solo se mantiene la versión más reciente del repositorio (`main`). No se emiten parches para versiones anteriores.
