# Ejemplo · Aseguramiento limitado de divulgaciones IFRS S2

## Contexto del engagement (ficticio)

**Cliente:** *AgroNorte S.A.*, agroindustrial regional, USD 320 M en ingresos. Primera vez que reporta bajo IFRS S2 (clima).

**Solicitante:** Junta Directiva (no es exigencia regulatoria todavía, es preparación para CSRD por exposición a la UE).

**Objetivo:** Aseguramiento de **alcance limitado** sobre el reporte de sostenibilidad 2025, con foco en las divulgaciones climáticas de IFRS S2 y el inventario GEI Alcance 1, 2 y 3 (parcial — categorías materiales).

**Restricciones:**
- 8 semanas calendario.
- 4 auditores; 1 con expertise en ESG, 3 generalistas.
- Datos de Alcance 3 dependen fuertemente de proveedores.
- Expectativa de la Junta: opinión "limited assurance" formal con caveats explícitos.

---

## SKILLs activadas

| SKILL | Rol en el engagement |
|---|---|
| ⭐ `auditoria-esg-sostenibilidad` | Especialidad ancla — IFRS S2, doble materialidad, framework |
| `auditoria-ambiental` | Para inventario GEI (ISO 14064-3 como guía de verificación) |
| `planeacion-basada-riesgos` | Evaluación de materialidad financiera + impacto |
| `evaluacion-controles` | Sobre los controles de captura, agregación y reporte de datos ESG |
| `papeles-trabajo` | Documentación con trazabilidad a fuente primaria |
| `comunicacion-hallazgos` | Estructura del informe de aseguramiento |

---

## Prompt inicial al agente

```
Activá las SKILLs auditoria-esg-sostenibilidad, auditoria-ambiental,
planeacion-basada-riesgos, evaluacion-controles, papeles-trabajo,
comunicacion-hallazgos.

CONTEXTO:
AgroNorte S.A. (agroindustria, USD 320M, 7 plantas en 3 países).
Primer año reportando bajo IFRS S2. Aseguramiento limitado solicitado
voluntariamente por la Junta. Inventario GEI:
- Alcance 1: combustión estacionaria + flota
- Alcance 2: electricidad comprada
- Alcance 3: parcial — categorías 1 (bienes y servicios), 4 (transporte
  upstream), 11 (uso de productos vendidos)

OBJETIVO:
Plan de aseguramiento limitado conforme a ISAE 3000 (revised) +
ISAE 3410 para GEI, alineado a IFRS S2.

NECESITO:
1. Definición de la materialidad cuantitativa para el inventario GEI
   (porcentaje aceptado en el sector y rationale).
2. Procedimientos diferenciados:
   - Alcance 1: pruebas detalladas (mayor confianza)
   - Alcance 2: pruebas analíticas + validación de factores de emisión
   - Alcance 3: indagaciones + revisión de metodología + spot checks
3. Mapeo de los 11 elementos de divulgación de IFRS S2 al alcance:
   - Governance
   - Strategy (incluye análisis de escenarios)
   - Risk management
   - Metrics & targets
4. Identificación de los controles internos relevantes sobre datos ESG
   (captura, agregación, validación, aprobación).
5. Estructura del informe de aseguramiento limitado con conclusión
   en formato negativo.

Citá IFRS S2, ISAE 3000 e ISAE 3410 en cada decisión relevante.
Usá GHG Protocol Corporate Standard para clasificación de alcances.
```

---

## Output esperado del agente (resumen)

### 1. Materialidad cuantitativa para GEI

**Materialidad de inventario:** 5% del total de emisiones declaradas por alcance (estándar de mercado bajo ISAE 3410 para limited assurance; para reasonable assurance se usaría 2–3%).

**Rationale:** sector agroindustrial tiene mayor variabilidad inherente en Alcance 3 categoría 11 (uso de productos vendidos depende de supuestos). 5% balancea costo de auditoría con utilidad para el usuario.

### 2. Procedimientos por alcance

| Alcance | Tipo de prueba | Cobertura | Evidencia primaria |
|---|---|---|---|
| **Scope 1** | Pruebas detalladas | 100% de plantas, muestra de transacciones de combustible (n=40) | Facturas de combustible, registros de flota, factores DEFRA/IPCC vigentes |
| **Scope 2** | Procedimientos analíticos + sustantivos limitados | 100% de electricidad, validación de factores de la red por país | Facturas de energía, factores de emisión de la red (location-based + market-based) |
| **Scope 3 cat 1** | Indagación + revisión de metodología + sample (n=15 proveedores top 80% spend) | Cobertura por spend | Spend data + factor de emisión por categoría (EEIO o supplier-specific) |
| **Scope 3 cat 4** | Pruebas analíticas + sample de 20 envíos | Top 80% ton-km | Datos del operador logístico |
| **Scope 3 cat 11** | Revisión de modelo + sensibilidad de supuestos | 100% de productos clave | Documentación del modelo, fuentes de supuestos |

### 3. Mapeo IFRS S2 (extracto)

| Elemento de divulgación | Procedimiento de aseguramiento | Riesgo principal |
|---|---|---|
| **Governance** — supervisión de la junta | Indagación + lectura de actas | Sobreestimación de actividad real de la junta |
| **Governance** — rol de la administración | Indagación + revisión de TORs de comités | Brecha entre rol declarado y real |
| **Strategy** — riesgos físicos del clima | Revisión de evaluación + benchmark sectorial | Identificación incompleta |
| **Strategy** — análisis de escenarios | Revisión de metodología + supuestos | Escenario único, sin sensibilidad |
| **Risk management** — integración con ERM | Walkthrough del proceso de riesgo | Proceso paralelo no integrado |
| **Metrics** — emisiones GEI | Procedimientos de Scope 1/2/3 detallados arriba | Errores en factores de emisión |
| **Metrics** — métricas industria-específica | Comparación con SASB Food & Beverage | Métricas omitidas |
| **Targets** — metas de reducción | Revisión de baseline, trayectoria, science-based alignment | Targets no alineados con SBTi |

### 4. Controles internos sobre datos ESG (extracto)

| Control | Tipo | Riesgo cubierto |
|---|---|---|
| Validación de extracción mensual de medidores | Manual | Captura incompleta |
| Reconciliación de datos por planta vs. ERP | Manual | Errores de agregación |
| Aprobación gerencial del inventario GEI | Manual | Falta de revisión |
| Segregación entre quien captura y quien agrega | Estructural | Manipulación |
| Versionado del modelo de Scope 3 cat 11 | Documental | Cambios no rastreables |

### 5. Estructura del informe (limited assurance)

```
1. Título: Independent limited assurance report on selected
   sustainability information

2. Destinatarios: Junta Directiva de AgroNorte S.A.

3. Información sujeta a aseguramiento (lista explícita de divulgaciones
   y métricas, con páginas del reporte de sostenibilidad).

4. Criterios aplicados: IFRS S2, GHG Protocol Corporate Standard,
   metodología propia de AgroNorte (referenciada y revisada).

5. Responsabilidades de la administración.

6. Responsabilidades del auditor (bajo ISAE 3000 revised + ISAE 3410).

7. Resumen del trabajo realizado (descripción de procedimientos —
   exigido por ISAE 3000 para limited assurance).

8. Limitaciones inherentes (precisión de factores de emisión,
   dependencia de datos de proveedores, juicios en Scope 3 cat 11).

9. Conclusión en forma negativa:
   "Sobre la base del trabajo realizado y la evidencia obtenida,
    no se ha puesto en nuestro conocimiento ningún asunto que nos
    haga creer que la Información sujeta a aseguramiento, en todos
    sus aspectos materiales, no está preparada de conformidad con
    los Criterios."

10. Materias de énfasis (si aplica):
    - Primera aplicación de IFRS S2 — comparativos no aseguraros.
    - Cambio metodológico en Scope 3 cat 11 desde año anterior.

11. Firma y fecha.
```

---

## Consideraciones de juicio profesional

1. **Limited ≠ Reasonable.** Limited assurance produce conclusión en negativo; reasonable produce conclusión en positivo. Procedimientos y costo difieren ~3x. La Junta debe entender la diferencia.

2. **Doble materialidad (CSRD/ESRS).** IFRS S2 cubre solo materialidad financiera. Si el cliente apunta a CSRD en el futuro, planificar gap analysis hacia doble materialidad como entregable adicional.

3. **Scope 3 categoría 11.** Es el más subjetivo. Documentar exhaustivamente los supuestos y testear sensibilidad. Si el cliente cambia metodología año a año, marcarlo en énfasis.

4. **Independencia.** Si la firma asesoró en la construcción del inventario GEI, no puede asegurarlo. Es autorrevisión.

5. **Factores de emisión vigentes.** Los factores DEFRA/IPCC se actualizan anualmente. Verificar que se use la versión correspondiente al período reportado.

6. **Análisis de escenarios.** No emitir opinión sobre la *probabilidad* de los escenarios, solo sobre la *consistencia* con la metodología declarada.

---

## SKILLs útiles para iteraciones siguientes

- `auditoria-cumplimiento` — si en años siguientes CSRD se vuelve obligatoria y hay gaps regulatorios.
- `auditoria-tecnologia-informacion` — si los datos ESG vienen de un sistema dedicado (ENABLON, Sphera, etc.) que requiere ITGCs.
- `seguimiento-recomendaciones` — para el siguiente ciclo, cerrando observaciones de captura de datos.
