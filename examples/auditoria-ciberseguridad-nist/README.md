# Ejemplo · Auditoría de madurez de ciberseguridad (NIST CSF 2.0)

## Contexto del engagement (ficticio)

**Cliente:** *Banco Andes S.A.*, banco mediano (Tier 2), ~1.200 empleados, presencia en 4 países hispanohablantes.

**Solicitante:** Comité de Auditoría.

**Objetivo:** Evaluar la madurez de la postura de ciberseguridad usando NIST CSF 2.0 como marco de referencia, con foco en las funciones **Govern**, **Identify** y **Protect**.

**Restricciones:**
- 6 semanas calendario.
- 3 auditores asignados.
- No se puede ejecutar pruebas intrusivas (sin pentesting).
- Debe entregarse opinión cuantitativa por subcategoría (escala 0–4 NIST).

---

## SKILLs activadas

| SKILL | Rol en el engagement |
|---|---|
| ⭐ `auditoria-ciberseguridad` | Especialidad ancla — define qué evaluar y bajo qué marco |
| `planeacion-basada-riesgos` | Construir el alcance, priorizar funciones/categorías |
| `evaluacion-controles` | Diseño y ejecución de pruebas de controles |
| `papeles-trabajo` | Documentación de evidencia (transversal) |
| `comunicacion-hallazgos` | Estructura del informe final con recomendaciones |

> No usamos `muestreo` porque no se prueban transacciones. No usamos `analitica-datos` porque la evaluación es de madurez, no de comportamiento transaccional.

---

## Prompt inicial al agente

```
Tengo activadas las siguientes SKILLs: auditoria-ciberseguridad,
planeacion-basada-riesgos, evaluacion-controles, papeles-trabajo,
comunicacion-hallazgos.

CONTEXTO:
Banco Andes S.A. — banco mediano regulado, 1.200 empleados, 4 países,
infraestructura híbrida (50% AWS, 50% on-prem en 2 datacenters).
Equipo de seguridad: 12 personas + SOC tercerizado 24/7.

OBJETIVO DEL ENGAGEMENT:
Auditoría de madurez bajo NIST CSF 2.0, alcance limitado a las funciones
GOVERN, IDENTIFY y PROTECT. Producir scoring por subcategoría (0–4) y
hoja de ruta priorizada.

RESTRICCIONES:
- 6 semanas, 3 auditores
- Sin pruebas intrusivas (sin pentesting / red team)
- Reporte final al Comité de Auditoría

Por favor:
1. Construí la matriz de riesgos inicial específica al sector financiero
   y a la arquitectura híbrida descrita, listando los 8 riesgos top.
2. Proponé el alcance detallado: qué subcategorías de GOVERN, IDENTIFY
   y PROTECT son las más críticas para este banco y por qué.
3. Diseñá el plan de trabajo semana por semana.
4. Proponé los 12 controles prioritarios a probar y, para cada uno,
   el procedimiento de auditoría no intrusivo aplicable.
5. Definí la rúbrica de scoring (qué evidencia justifica un nivel
   1, 2, 3 o 4).

Citá NIST CSF 2.0 con identificador de subcategoría en cada propuesta.
```

---

## Output esperado del agente (resumen)

### 1. Matriz de riesgos top (extracto)

| # | Riesgo | NIST Function | Probabilidad | Impacto |
|---|---|---|---|---|
| 1 | Ransomware sobre datacenters on-prem | PR.DS, RC.RP | Alta | Crítico |
| 2 | Compromiso de credenciales privilegiadas | PR.AA-01, PR.AA-05 | Alta | Crítico |
| 3 | Fuga de datos vía SaaS no aprobado | ID.AM-04, PR.DS-01 | Media | Alto |
| ... | ... | ... | ... | ... |

### 2. Alcance — subcategorías priorizadas

**GOVERN (15 subcategorías priorizadas de 32):**
- GV.OC-01 a 05 (entendimiento del contexto organizacional)
- GV.RM-01 a 03 (estrategia de riesgo)
- GV.RR-01 a 04 (roles y responsabilidades)
- GV.SC-01 a 04 (gestión de riesgo de cadena de suministro)

**IDENTIFY (12 subcategorías):**
- ID.AM-01 a 08 (gestión de activos completa)
- ID.RA-01 a 04 (evaluación de riesgo)

**PROTECT (18 subcategorías):**
- Foco en PR.AA (autenticación), PR.DS (seguridad de datos), PR.PS (plataforma).

### 3. Cronograma (alto nivel)

| Semana | Actividad |
|---|---|
| 1 | Kickoff, levantamiento de inventario, planning detallado |
| 2 | Entrevistas a líderes (CISO, IT Ops, GRC) — GOVERN + IDENTIFY |
| 3 | Recolección de evidencia documental — políticas, procedimientos |
| 4 | Inspección técnica no intrusiva (configs, IAM, logs) |
| 5 | Scoring, validación cruzada, hallazgos preliminares |
| 6 | Drafting del informe, exit meeting, presentación al Comité |

### 4. Controles prioritarios a probar (extracto)

| # | Subcategoría NIST | Control | Procedimiento no intrusivo |
|---|---|---|---|
| 1 | PR.AA-01 | Gestión de identidades únicas | Inspección de IAM (lista de usuarios privilegiados, MFA habilitado) |
| 2 | PR.AA-05 | Permisos según rol | Revisión de matriz de roles vs. asignaciones reales en Active Directory y AWS IAM |
| 3 | PR.DS-01 | Datos en reposo cifrados | Inspección de configuración de cifrado (KMS, BitLocker, TDE) |
| 4 | DE.CM-01 | Monitoreo continuo de la red | Revisión de cobertura de SIEM, logs ingeridos, casos de uso activos |
| ... | ... | ... | ... |

### 5. Rúbrica de scoring

| Nivel | Etiqueta | Evidencia mínima |
|---|---|---|
| 0 | No existente | Ningún proceso ni evidencia |
| 1 | Inicial / ad hoc | Práctica informal, sin documentar |
| 2 | Repetible | Documentado pero inconsistente |
| 3 | Definido | Documentado, ejecutado consistentemente, con métricas |
| 4 | Adaptable | Mejora continua basada en métricas y *threat intelligence* |

---

## Consideraciones de juicio profesional

1. **No prometer "bueno o malo".** El scoring de NIST CSF es relativo al *target profile* de la organización, no absoluto. Definir el target con el Comité antes de calificar.

2. **Subcategorías GV son foundational.** Si GV.RM (estrategia de riesgo) está en nivel 0–1, todo lo demás colapsa. Empezar por ahí.

3. **Cuidado con la cadena de suministro.** GV.SC se ve a menudo subestimado en bancos medianos. El SOC tercerizado *es* parte de la cadena.

4. **Reporte cuantitativo + narrativo.** Comité de Auditoría suele pedir números, pero las decisiones se toman con narrativa. Ambos son obligatorios.

5. **Independencia del SOC tercerizado.** Si auditamos al SOC, ese vendor no puede ser fuente única de evidencia sobre sí mismo. Triangular.

---

## SKILLs útiles para iteraciones siguientes

- `auditoria-tecnologia-informacion` — si surge un hallazgo en ITGCs.
- `auditoria-cumplimiento` — si la madurez baja en GV.OC implica gaps regulatorios.
- `auditoria-continua` — para diseñar la fase 2 (monitoreo recurrente post-auditoría).
- `seguimiento-recomendaciones` — para el ciclo de cierre de hallazgos en los siguientes 6–12 meses.
