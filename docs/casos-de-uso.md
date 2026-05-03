# Casos de uso — combinaciones típicas

Esta tabla resume las combinaciones de SKILLs más usadas según el tipo de engagement. Es una guía, no una receta rígida — siempre ajustá al alcance y riesgos del trabajo concreto.

> **Convención:** las SKILLs marcadas con ⭐ son las "ancla" del engagement. Las demás complementan.

---

## Auditorías financieras y contables

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Auditoría de estados financieros | ⭐ `auditoria-financiera` | `planeacion-basada-riesgos`, `evaluacion-controles`, `muestreo`, `papeles-trabajo`, `comunicacion-hallazgos` |
| Certificación SOX 404 / ICFR | ⭐ `auditoria-financiera` + `auditoria-tecnologia-informacion` | `evaluacion-controles` ⭐, `muestreo`, `papeles-trabajo` |
| Revisión de cierre contable | ⭐ `auditoria-financiera` | `analitica-datos`, `papeles-trabajo` |
| Due diligence financiera | ⭐ `auditoria-financiera` | `analitica-datos`, `comunicacion-hallazgos` |

## Auditorías de tecnología

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Auditoría de ITGCs | ⭐ `auditoria-tecnologia-informacion` | `evaluacion-controles` ⭐, `muestreo`, `papeles-trabajo` |
| Auditoría cloud (AWS/Azure/GCP) | ⭐ `auditoria-tecnologia-informacion` + `auditoria-ciberseguridad` | `evaluacion-controles`, `analitica-datos` |
| Auditoría ERP (SAP/Oracle) | ⭐ `auditoria-tecnologia-informacion` | `evaluacion-controles`, `analitica-datos`, `muestreo` |
| Pre-implementación de sistema | ⭐ `auditoria-tecnologia-informacion` | `planeacion-basada-riesgos`, `evaluacion-controles` |

## Auditorías de ciberseguridad

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Madurez de ciberseguridad (NIST CSF) | ⭐ `auditoria-ciberseguridad` | `planeacion-basada-riesgos`, `evaluacion-controles`, `comunicacion-hallazgos` |
| Auditoría ISO 27001 | ⭐ `auditoria-ciberseguridad` | `evaluacion-controles`, `papeles-trabajo` |
| Resiliencia / respuesta a incidentes | ⭐ `auditoria-ciberseguridad` | `evaluacion-controles`, `auditoria-continua` |
| Auditoría de IAM / accesos | ⭐ `auditoria-ciberseguridad` + `auditoria-tecnologia-informacion` | `analitica-datos` ⭐, `muestreo` |

## Auditorías forenses e investigaciones

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Investigación de fraude transaccional | ⭐ `auditoria-forense` | `analitica-datos` ⭐, `papeles-trabajo`, `evaluacion-controles` |
| Investigación de soborno / corrupción | ⭐ `auditoria-forense` + `auditoria-cumplimiento` | `papeles-trabajo`, `comunicacion-hallazgos` |
| Detección de patrones AML | ⭐ `auditoria-forense` | `analitica-datos` ⭐, `auditoria-continua` |
| Conflictos de interés | ⭐ `auditoria-forense` | `analitica-datos`, `papeles-trabajo` |

## Auditorías de cumplimiento

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Programa de cumplimiento (ISO 37301) | ⭐ `auditoria-cumplimiento` | `planeacion-basada-riesgos`, `evaluacion-controles` |
| Anti-soborno (ISO 37001 / FCPA) | ⭐ `auditoria-cumplimiento` + `auditoria-forense` | `analitica-datos`, `evaluacion-controles` |
| AML/CFT (SAGRILAFT, SARLAFT) | ⭐ `auditoria-cumplimiento` + `auditoria-forense` | `analitica-datos` ⭐, `auditoria-continua` |
| Protección de datos (GDPR / hábeas data) | ⭐ `auditoria-cumplimiento` + `auditoria-tecnologia-informacion` | `evaluacion-controles`, `papeles-trabajo` |

## Auditorías ESG y ambientales

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Aseguramiento de reporte ESG (ISSB / GRI) | ⭐ `auditoria-esg-sostenibilidad` | `planeacion-basada-riesgos`, `evaluacion-controles`, `papeles-trabajo` |
| Verificación de inventario GEI | ⭐ `auditoria-ambiental` + `auditoria-esg-sostenibilidad` | `evaluacion-controles`, `analitica-datos` |
| Sistema de gestión ambiental (ISO 14001) | ⭐ `auditoria-ambiental` | `evaluacion-controles`, `comunicacion-hallazgos` |
| Doble materialidad (CSRD/ESRS) | ⭐ `auditoria-esg-sostenibilidad` | `planeacion-basada-riesgos` ⭐, `comunicacion-hallazgos` |

## Auditorías operativas y de gestión

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Eficiencia de proceso operativo | ⭐ `auditoria-operativa` | `analitica-datos`, `evaluacion-controles`, `comunicacion-hallazgos` |
| Performance audit (sector público) | ⭐ `auditoria-gestion-desempeno` + `auditoria-operativa` | `planeacion-basada-riesgos`, `analitica-datos` |
| Auditoría de gobierno corporativo | ⭐ `auditoria-gestion-desempeno` | `evaluacion-controles`, `comunicacion-hallazgos` |
| Calidad (ISO 9001) | ⭐ `auditoria-calidad` | `evaluacion-controles`, `comunicacion-hallazgos` |

## Auditorías sobre IA y modelos

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Auditoría de modelo de ML en producción | ⭐ `auditoria-inteligencia-artificial` | `evaluacion-controles` ⭐, `analitica-datos` |
| Cumplimiento EU AI Act | ⭐ `auditoria-inteligencia-artificial` + `auditoria-cumplimiento` | `evaluacion-controles`, `papeles-trabajo` |
| Auditoría de sistema GenAI / LLM | ⭐ `auditoria-inteligencia-artificial` + `auditoria-ciberseguridad` | `evaluacion-controles`, `auditoria-continua` |
| Evaluación de sesgo y fairness | ⭐ `auditoria-inteligencia-artificial` | `analitica-datos` ⭐, `papeles-trabajo` |

## Función de auditoría (no engagements)

| Tipo de trabajo | Especialidad | Procesos clave |
|---|---|---|
| Diseño del plan anual de auditoría | — | ⭐ `planeacion-basada-riesgos` + `aseguramiento-calidad` |
| Implementación de QAIP | — | ⭐ `aseguramiento-calidad` |
| Implementación de auditoría continua | — | ⭐ `auditoria-continua` + `analitica-datos` |
| Maduración de la función | — | ⭐ `aseguramiento-calidad` + `planeacion-basada-riesgos` |

---

## ¿No encontrás tu caso?

Abrí un *issue* con la etiqueta `caso-de-uso` describiendo el tipo de trabajo y lo añadimos en una próxima versión.
