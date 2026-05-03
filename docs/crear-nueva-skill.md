# Cómo crear una nueva SKILL

Esta guía describe la convención usada en este repositorio para crear una SKILL nueva, ya sea para sumarla al catálogo público o para crear tu propia variante privada.

## Antes de empezar

Antes de crear una SKILL, preguntate:

1. **¿Existe ya algo similar en el catálogo?** Revisá [`../README.md`](../README.md) y [`casos-de-uso.md`](casos-de-uso.md). Quizá lo que necesitás es enriquecer una SKILL existente, no crear una nueva.
2. **¿Es proceso o especialidad?**
   - **Proceso:** se aplica a *cualquier* tipo de auditoría (planeación, muestreo, papeles, etc.).
   - **Especialidad:** se aplica a *un* dominio (financiera, TI, ambiental, etc.).
3. **¿Tiene al menos dos estándares ancla?** Si no podés citar normas reconocidas, probablemente la SKILL no está madura todavía.

## Estructura de carpeta

Cada SKILL vive en su propia carpeta:

```
skills/
├── procesos/
│   └── <nombre-en-kebab-case>/
│       ├── SKILL.md         ← obligatorio
│       └── README.md        ← obligatorio
└── especialidades/
    └── <nombre-en-kebab-case>/
        ├── SKILL.md
        └── README.md
```

**Convenciones de nombre:**
- Carpeta y `name` del frontmatter: `kebab-case`.
- Especialidades: prefijo `auditoria-` (ej. `auditoria-ciberseguridad`).
- Procesos: sin prefijo (ej. `evaluacion-controles`).

## Plantilla de SKILL.md

```markdown
---
name: nombre-en-kebab-case
description: Una sola línea que (1) explica qué hace la SKILL, (2) lista disparadores léxicos (palabras clave que deben activarla). Empezar siempre con verbo en infinitivo. Activar siempre que se hable de <palabra1>, <palabra2>, <sigla>, <norma>, ...
---

# Título legible de la SKILL

## Propósito

Un párrafo explicando qué problema profesional resuelve esta SKILL y cuál es su entregable típico.

## Cuándo activar esta SKILL

- Lista de situaciones concretas (3–7 viñetas).
- Cada viñeta debe ser accionable y reconocible por el agente.

## Marco de referencia

### <Categoría 1>
- **<Estándar 1>** — qué cubre, versión vigente.
- **<Estándar 2>** — ...

### <Categoría 2>
- ...

## Procedimiento

Paso a paso o por fases. Cada paso debe ser ejecutable por un agente:

1. **<Acción>** — entradas esperadas, salidas esperadas, criterios de calidad.
2. **<Acción>** — ...

## Entregables

Listar los artefactos que la SKILL debe producir (matriz, memorando, papel de trabajo, informe, etc.).

## Consideraciones especiales

- Errores comunes a evitar.
- Casos límite.
- Cuándo escalar a un humano.

## Referencias cruzadas a otras SKILLs

Indicar con qué SKILLs del catálogo se combina típicamente y por qué.
```

## Plantilla de README.md (legible en GitHub)

```markdown
# SKILL · <nombre-en-kebab-case>

> **Tipo:** Proceso (transversal) | Especialidad · **Categoría:** <fase o dominio>

<Descripción de 1–2 frases.>

## Cuándo se activa

Cuando el usuario menciona: <lista de palabras clave>.

## Marcos de referencia anclados

- <Estándar 1>
- <Estándar 2>

## Se combina típicamente con

`skill-1` · `skill-2` · `skill-3`

## Archivo

[`SKILL.md`](SKILL.md)
```

## Reglas de redacción

- **Lenguaje:** español neutro, evitar localismos.
- **Tono:** profesional, no académico ni publicitario.
- **Brevedad:** preferí precisión sobre extensión. Una SKILL de 600 palabras bien dirigidas vale más que 2.000 palabras genéricas.
- **Referencias normativas:** citar nombre + número + versión cuando aplique.
- **Sin marcas comerciales innecesarias:** mencioná software sólo cuando es referencia obligada (ACL, IDEA, SAP). Nunca como recomendación.
- **Sin información confidencial:** ningún dato real de cliente, ningún papel de trabajo identificable.

## Disparadores léxicos en `description`

El campo `description` es lo que el agente lee para decidir si cargar la SKILL. Debe contener:

1. **Verbo + objeto** que describa la acción central (ej. "Auditar...", "Diseñar...", "Documentar...").
2. **Frase explícita "Activar siempre que..."** seguida de una lista de palabras clave separadas por comas.

Ejemplo bueno:
> *Auditar la postura de ciberseguridad aplicando NIST CSF 2.0, ISO 27001/27002 y CIS Controls. Activar siempre que se hable de ciberseguridad, NIST CSF, ISO 27001, MITRE ATT&CK, SIEM, SOC, EDR, IAM, MFA, ransomware, phishing, NIS 2, zero trust, threat hunting.*

Ejemplo malo:
> *SKILL para auditoría de seguridad informática.* (genérico, sin disparadores)

## Después de crear la SKILL

1. Actualizá [`../catalog.json`](../catalog.json) añadiendo la entrada.
2. Actualizá la tabla en [`../README.md`](../README.md).
3. Si tiene combinaciones típicas claras, actualizá [`casos-de-uso.md`](casos-de-uso.md).
4. Sumá una entrada en [`../CHANGELOG.md`](../CHANGELOG.md) bajo `[No publicado]`.
5. Abrí un Pull Request siguiendo [`../CONTRIBUTING.md`](../CONTRIBUTING.md).

## Validación rápida

Antes de enviar el PR, confirmá:

- [ ] Frontmatter YAML con `name` y `description` válidos.
- [ ] `description` contiene "Activar siempre que..." con disparadores.
- [ ] Al menos 2 estándares ancla citados con versión.
- [ ] `README.md` presente y siguiendo el patrón.
- [ ] Sin información confidencial.
- [ ] `catalog.json`, `README.md` raíz y `CHANGELOG.md` actualizados.
