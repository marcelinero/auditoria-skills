# auditoria-skills

> Catálogo abierto de **SKILLs** (instrucciones modulares para agentes de IA) basadas en buenas prácticas, normas y estándares globalmente aceptados para la función de auditoría — interna, externa, financiera, de TI, forense, ESG y más.

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](LICENSE)
[![Versión](https://img.shields.io/badge/versi%C3%B3n-1.0.0-blue.svg)](CHANGELOG.md)
[![SKILLs](https://img.shields.io/badge/SKILLs-20-brightgreen.svg)](catalog.json)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange.svg)](CONTRIBUTING.md)

---

## ¿Qué es esto?

Un repositorio de **20 SKILLs** listas para usar con cualquier agente de IA moderno (Claude Code, ChatGPT, Gemini, agentes propios via SDK), pensadas para acompañar al auditor en todas las fases de su trabajo:

- **8 SKILLs de proceso** — transversales a cualquier especialidad: planeación basada en riesgos, evaluación de controles, muestreo, papeles de trabajo, comunicación de hallazgos, seguimiento, aseguramiento de calidad y analítica de datos.
- **12 SKILLs de especialidad** — uno por dominio: financiera, TI, forense, cumplimiento, ESG, ciberseguridad, IA, calidad, ambiental, operativa, gestión de desempeño y auditoría continua.

Cada SKILL ancla sus procedimientos a normas reconocidas (IIA, COSO, NIA/ISA, COBIT, ISO, NIST, ISSB, ACFE…) y está redactada en español neutro, lista para que un agente la cargue como contexto y lo guíe profesionalmente.

---

## Quickstart

```bash
# Clonar el repositorio
git clone https://github.com/marcelinero/auditoria-skills.git

# (Claude Code) — instalación personal
cp -r auditoria-skills ~/.claude/skills/auditoria

# (Claude.ai Project) — sube los SKILL.md que necesites en "Project knowledge"
# (ChatGPT Custom GPT) — pega un SKILL.md como instrucciones, sube los demás como knowledge
```

Para instrucciones por plataforma, ver [`docs/instalacion.md`](docs/instalacion.md).

---

## Servidor MCP (recomendado para Claude Desktop y Claude Code)

Este repositorio incluye un **servidor MCP** listo para usar que expone las 20 SKILLs como herramientas nativas en cualquier cliente compatible.

### Configuración rápida (requiere [uv](https://docs.astral.sh/uv/))

Agregá esto a tu `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "auditoria-skills": {
      "command": "uv",
      "args": [
        "run",
        "--script",
        "/ruta/al/repo/auditoria-skills/mcp/server.py"
      ]
    }
  }
}
```

**Herramientas que expone el MCP:**

| Herramienta | Qué hace |
| --- | --- |
| `listar_skills` | Muestra el catálogo completo con tipos y marcos normativos |
| `obtener_skill` | Carga el contenido completo de una SKILL por nombre |
| `buscar_skills` | Filtra por tipo (`proceso`/`especialidad`) y/o marco (ISO, NIST, IIA…) |

Instrucciones completas de instalación y configuración → [`mcp/README.md`](mcp/README.md)

---

## Catálogo

### SKILLs de proceso (transversales)

| SKILL | Propósito | Estándares ancla |
| --- | --- | --- |
| [`planeacion-basada-riesgos`](skills/procesos/planeacion-basada-riesgos/) | Construir el universo auditable, evaluar riesgos y elaborar planes anuales y de engagement | IIA, COSO ERM, ISO 31000 |
| [`evaluacion-controles`](skills/procesos/evaluacion-controles/) | Identificar, documentar y probar diseño y operación de controles internos | COSO IC-IF, IIA, SOX 404 |
| [`muestreo`](skills/procesos/muestreo/) | Diseñar muestreo estadístico y no estadístico para pruebas de auditoría | NIA/ISA 530, AICPA |
| [`papeles-trabajo`](skills/procesos/papeles-trabajo/) | Documentar evidencia y conclusiones de manera reconstruible por un revisor | NIA/ISA 230, IIA |
| [`comunicacion-hallazgos`](skills/procesos/comunicacion-hallazgos/) | Estructurar hallazgos (CCCRA), redactar informes y comunicar a partes interesadas | IIA Standards |
| [`seguimiento-recomendaciones`](skills/procesos/seguimiento-recomendaciones/) | Monitorear implementación y verificar cierre efectivo de hallazgos | IIA Standards |
| [`aseguramiento-calidad`](skills/procesos/aseguramiento-calidad/) | Diseñar y operar el QAIP de la función de auditoría interna | IIA, IIA QA Manual |
| [`analitica-datos`](skills/procesos/analitica-datos/) | Aplicar ACL, IDEA, SQL, Python y R sobre poblaciones completas (CAATs) | GTAG 16, ISACA |

### SKILLs de especialidad

| SKILL | Dominio | Estándares ancla |
| --- | --- | --- |
| [`auditoria-financiera`](skills/especialidades/financiera/) | Estados financieros y aseveraciones contables | NIA/ISA, NIIF/IFRS, SOX, COSO IC-IF |
| [`auditoria-operativa`](skills/especialidades/operativa/) | Eficiencia, eficacia y economía de procesos | IIA, ISO 9001, INTOSAI |
| [`auditoria-tecnologia-informacion`](skills/especialidades/tecnologia-informacion/) | Gobierno y controles generales de TI (ITGCs) | COBIT 2019, ITAF, GTAGs, ISO 27001 |
| [`auditoria-forense`](skills/especialidades/forense/) | Investigación de fraude y conducta indebida | ACFE, NIA 240, FATF |
| [`auditoria-cumplimiento`](skills/especialidades/cumplimiento/) | Adherencia a leyes, regulación y normativa interna | ISO 37301, ISO 37001, marcos sectoriales |
| [`auditoria-esg-sostenibilidad`](skills/especialidades/esg-sostenibilidad/) | Reportes y desempeño ESG | ISSB (IFRS S1/S2), GRI, TCFD, SASB |
| [`auditoria-ciberseguridad`](skills/especialidades/ciberseguridad/) | Postura de ciberseguridad y resiliencia | NIST CSF 2.0, ISO 27001/27002, CIS |
| [`auditoria-inteligencia-artificial`](skills/especialidades/inteligencia-artificial/) | Sistemas de IA, modelos y algoritmos | ISO/IEC 42001, NIST AI RMF, EU AI Act |
| [`auditoria-calidad`](skills/especialidades/calidad/) | Sistemas de gestión de calidad | ISO 9001, ISO 19011 |
| [`auditoria-ambiental`](skills/especialidades/ambiental/) | Sistemas de gestión ambiental e inventarios GEI | ISO 14001, ISO 14064, GHG Protocol |
| [`auditoria-gestion-desempeno`](skills/especialidades/gestion-desempeno/) | Logro de objetivos y desempeño organizacional | IIA, INTOSAI ISSAI, COSO ERM |
| [`auditoria-continua`](skills/especialidades/continua/) | Auditoría y monitoreo continuos | GTAG 3, AICPA, ISACA |

> 📋 También disponible como índice machine-readable: [`catalog.json`](catalog.json).

---

## Cómo se combinan las SKILLs

Un trabajo de auditoría real **siempre** combina al menos una SKILL de especialidad con varias SKILLs de proceso:

```
   ESPECIALIDAD (¿qué auditás?)
            │
            ▼
   1. planeacion-basada-riesgos
            ↓
   2. evaluacion-controles  ←  3. analitica-datos / muestreo
            ↓
   4. papeles-trabajo (transversal)
            ↓
   5. comunicacion-hallazgos
            ↓
   6. seguimiento-recomendaciones
            ↓
   7. aseguramiento-calidad (transversal y periódico)
```

**Combinaciones típicas por tipo de auditoría →** [`docs/casos-de-uso.md`](docs/casos-de-uso.md)

**Ejemplos end-to-end con prompt y output esperado →** [`examples/`](examples/)

---

## Estructura del repositorio

```
auditoria-skills/
├── README.md                        ← este archivo
├── LICENSE                          ← CC BY-SA 4.0
├── CONTRIBUTING.md                  ← cómo aportar al catálogo
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── catalog.json                     ← índice machine-readable
├── .gitignore
│
├── skills/
│   ├── procesos/                    ← 8 SKILLs transversales
│   │   ├── analitica-datos/
│   │   ├── aseguramiento-calidad/
│   │   ├── comunicacion-hallazgos/
│   │   ├── evaluacion-controles/
│   │   ├── muestreo/
│   │   ├── papeles-trabajo/
│   │   ├── planeacion-basada-riesgos/
│   │   └── seguimiento-recomendaciones/
│   └── especialidades/              ← 12 SKILLs por dominio
│       ├── ambiental/
│       ├── calidad/
│       ├── ciberseguridad/
│       ├── continua/
│       ├── cumplimiento/
│       ├── esg-sostenibilidad/
│       ├── financiera/
│       ├── forense/
│       ├── gestion-desempeno/
│       ├── inteligencia-artificial/
│       ├── operativa/
│       └── tecnologia-informacion/
│
├── docs/
│   ├── instalacion.md               ← Claude Code, Projects, SDK, ChatGPT, Gemini
│   ├── como-usar.md                 ← orquestación y buenas prácticas
│   ├── casos-de-uso.md              ← combinaciones por tipo de auditoría
│   ├── glosario.md                  ← siglas y términos
│   └── crear-nueva-skill.md         ← plantilla y convenciones
│
├── examples/                        ← escenarios end-to-end ficticios
│   ├── auditoria-ciberseguridad-nist/
│   ├── auditoria-financiera-sox/
│   └── auditoria-esg-issb/
│
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── nueva-skill.md
    │   └── mejora-skill.md
    └── PULL_REQUEST_TEMPLATE.md
```

Cada carpeta de SKILL contiene:
- `SKILL.md` — frontmatter YAML + cuerpo de instrucciones (lo que carga el agente).
- `README.md` — ficha legible al navegar GitHub.

---

## Para quién es esto

- **Auditores internos y externos** que quieren acelerar su trabajo con un agente de IA confiable.
- **Áreas de auditoría** que están definiendo su política de uso de IA y necesitan una base sólida.
- **Consultores y firmas** que entrenan equipos junior en buenas prácticas.
- **Universidades** que enseñan auditoría con apoyo de IA.
- **Desarrolladores de agentes verticales** para gobierno, riesgo y cumplimiento (GRC).

---

## Marco normativo de referencia

El catálogo se construye sobre estos cuerpos normativos (versiones vigentes a la fecha de cada release):

- **Auditoría interna:** Normas Globales de Auditoría Interna del IIA (2025), Modelo de Tres Líneas (2020).
- **Control interno y riesgo:** COSO IC-IF (2013), COSO ERM (2017), ISO 31000.
- **Auditoría financiera:** NIA/ISA del IAASB, NIIF/IFRS, US GAAP, PCAOB AS, SOX.
- **TI y ciberseguridad:** COBIT 2019, ITAF, GTAGs, ISO/IEC 27001/27002, NIST CSF 2.0, CIS Controls v8.
- **Forense y antifraude:** ACFE Manual, NIA 240, FATF.
- **Cumplimiento:** ISO 37301, ISO 37001, OCDE.
- **ESG:** ISSB (IFRS S1/S2), GRI, TCFD, SASB, CSRD/ESRS.
- **IA:** ISO/IEC 42001, NIST AI RMF, EU AI Act.
- **Sistemas de gestión:** ISO 9001, ISO 14001, ISO 14064, GHG Protocol, ISO 19011.

---

## Principios de uso responsable

1. **No improvisar criterio normativo.** Si una norma cambió de versión, verificá la vigente antes de citarla.
2. **Triangular evidencia.** Una sola fuente raramente es suficiente.
3. **Documentar el rastro de razonamiento.** Todo juicio profesional aplicado por el agente debe quedar escrito en el papel de trabajo correspondiente.
4. **Respetar la independencia y objetividad.** El agente no debe participar en operaciones que luego va a auditar (autorrevisión).
5. **Conservar confidencialidad.** Información sensible obtenida en la auditoría no debe usarse fuera del propósito autorizado.
6. **El agente no sustituye al auditor.** Acompaña, acelera, sugiere — pero la opinión profesional y la firma siguen siendo del auditor.

---

## Contribuir

¡Las contribuciones son bienvenidas! Antes de empezar leé [`CONTRIBUTING.md`](CONTRIBUTING.md).

**Caminos típicos de contribución:**
- Reportar una norma desactualizada → [issue de mejora](.github/ISSUE_TEMPLATE/mejora-skill.md).
- Proponer una nueva SKILL → [issue de nueva SKILL](.github/ISSUE_TEMPLATE/nueva-skill.md).
- Aportar un caso de uso real (anonimizado) en `examples/`.
- Mejorar la documentación.

---

## Licencia

Este trabajo está licenciado bajo [Creative Commons Attribution-ShareAlike 4.0 International](LICENSE) (CC BY-SA 4.0).

Sos libre de compartir y adaptar el material —incluso comercialmente— siempre que (a) atribuyas adecuadamente y (b) compartas las obras derivadas bajo la misma licencia.

---

## Reconocimientos

Este catálogo se nutre del cuerpo de conocimiento construido durante décadas por el IIA, COSO, IAASB, ISACA, NIST, ISO, ACFE, IFRS Foundation y otros emisores de normas. Las SKILLs no reemplazan a las normas — las hacen accionables a través de un agente de IA.

---

## Contacto

- **Issues / propuestas:** abrí un issue en este repositorio.
- **Discusiones generales:** pestaña *Discussions* de GitHub.
