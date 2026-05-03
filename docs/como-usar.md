# Cómo usar las SKILLs

Esta guía explica el modelo mental detrás del catálogo y cómo orquestar varias SKILLs en un mismo trabajo de auditoría.

## El modelo: dos dimensiones complementarias

Las SKILLs están organizadas en dos dimensiones que se combinan:

| Dimensión | ¿Qué responde? | Cuándo se usan |
|---|---|---|
| **Especialidad** | *"¿Qué estoy auditando?"* | Una o dos por engagement |
| **Proceso** | *"¿En qué etapa estoy?"* | Varias en secuencia o en paralelo |

Una auditoría real **siempre** combina al menos una SKILL de especialidad con varias SKILLs de proceso.

```
            ┌──────────────────────────────────────────┐
            │      ESPECIALIDAD (¿qué auditás?)        │
            │  financiera · TI · forense · ESG · etc.  │
            └──────────────────────────────────────────┘
                              │
                              ▼
       ┌──────────────────────────────────────────────────┐
       │           PROCESO (¿en qué etapa?)               │
       │   planeación → ejecución → comunicación → seg.   │
       └──────────────────────────────────────────────────┘
```

---

## Flujo estándar de una auditoría

```
1. Activar la SKILL de ESPECIALIDAD que corresponda al objeto auditado
   (ej. auditoria-ciberseguridad)
                          ↓
2. PLANEACIÓN
   └─ planeacion-basada-riesgos
                          ↓
3. EJECUCIÓN
   ├─ evaluacion-controles      (siempre)
   ├─ analitica-datos           (cuando hay datos)
   └─ muestreo                  (cuando se prueba selección)
                          ↓
4. DOCUMENTACIÓN
   └─ papeles-trabajo           (transversal a TODA la ejecución)
                          ↓
5. COMUNICACIÓN
   └─ comunicacion-hallazgos
                          ↓
6. POST-INFORME
   └─ seguimiento-recomendaciones
                          ↓
7. CALIDAD DE LA FUNCIÓN
   └─ aseguramiento-calidad     (transversal y periódico)
```

---

## Tres patrones de orquestación

### Patrón A — Engagement individual

Una sola auditoría de inicio a fin. Mantén activas:
- **1 especialidad** (la del objeto auditado).
- **5–6 procesos** (planeación, controles, muestreo, papeles, hallazgos, seguimiento).

Ejemplo: auditoría de cierre contable trimestral.

### Patrón B — Auditoría híbrida o integrada

Dos dominios que se cruzan (ej. ciberseguridad + cumplimiento regulatorio).

Activa:
- **2 especialidades** (`auditoria-ciberseguridad` + `auditoria-cumplimiento`).
- **4–5 procesos**, asegurándote de combinar evidencia de ambas especialidades en `papeles-trabajo` y `comunicacion-hallazgos`.

### Patrón C — Función completa de auditoría

Diseño y operación de toda la función (típico de un CAE o de un consultor estructurando una unidad nueva).

Activa todo el catálogo, pero úsalo como **referencia**, no como contexto simultáneo. Es preferible cargar SKILLs por fase de trabajo.

---

## Buenas prácticas con agentes de IA

### 1. No mezclar más SKILLs de las necesarias

Cargar las 20 SKILLs simultáneamente diluye la atención del modelo y puede saturar el contexto. Selecciona las relevantes al engagement.

### 2. Activar SKILLs por fase, no de una sola vez

Si tu plataforma lo permite (Claude Code, Custom GPTs con varias instancias), activá las SKILLs según avances:
- Empezá con `planeacion-basada-riesgos` + especialidad.
- Cuando entres a ejecución, cargá `evaluacion-controles`, `muestreo`, `analitica-datos`.
- Para el cierre, sumá `comunicacion-hallazgos`.

### 3. Pedile siempre al agente que cite la norma

Buen prompt:
> *"Diseñá las pruebas de operación para los controles del ciclo de ingresos. Citá la NIA o el principio COSO que sustenta cada prueba."*

### 4. Documentar el rastro de razonamiento

Cualquier juicio profesional aplicado por el agente debe quedar escrito en el papel de trabajo correspondiente. La SKILL `papeles-trabajo` lo refuerza.

### 5. Triangular evidencia

Una sola fuente raramente es suficiente. Pedile al agente que combine entrevistas, inspección documental y pruebas analíticas antes de concluir.

### 6. Verificar versiones de normas

Cuando el agente cite una norma (ISO, NIST, NIA, IFRS), confirma que estás trabajando con la versión vigente. Las SKILLs anclan versiones, pero los estándares evolucionan.

---

## Ejemplo de prompt para arrancar una auditoría

```
Acabo de iniciar una auditoría de ciberseguridad para una empresa
del sector financiero, regulada en Colombia. Tienen ~800 empleados,
infraestructura híbrida (on-prem + AWS) y un SOC tercerizado.

Activá las SKILLs auditoria-ciberseguridad y planeacion-basada-riesgos.

Necesito que:
1. Construyas la matriz de riesgos de ciberseguridad inicial usando
   NIST CSF 2.0 como anclaje.
2. Propongas el alcance del engagement (qué entra y qué no).
3. Identifiques los 5–7 controles más críticos a probar.
4. Estimes esfuerzo en horas-hombre.

Citá las funciones de NIST CSF en cada propuesta.
```

---

## Próximos pasos

- Revisá [`casos-de-uso.md`](casos-de-uso.md) para ver combinaciones típicas por tipo de auditoría.
- Inspirate con los escenarios end-to-end en [`../examples/`](../examples/).
- Si querés crear tu propia SKILL, leé [`crear-nueva-skill.md`](crear-nueva-skill.md).
