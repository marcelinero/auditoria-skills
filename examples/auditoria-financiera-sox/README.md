# Ejemplo · Certificación SOX 404 — Ciclo de ingresos

## Contexto del engagement (ficticio)

**Cliente:** *RetailLatam Inc.*, retailer omnichannel listado en NYSE (foreign private issuer), USD 850 M en ingresos anuales.

**Solicitante:** Dirección de Auditoría Interna (función de SOX in-house).

**Objetivo:** Certificación anual SOX 404 sobre el ciclo de ingresos (B2C ecommerce + B2B mayorista). Producir evidencia para la opinión del auditor externo sobre ICFR.

**Restricciones:**
- Año fiscal cerró el 31-dic-2025; opinión debe emitirse antes del 28-feb-2026.
- 8 auditores, 10 semanas de trabajo de campo.
- ERP: SAP S/4HANA. Plataforma e-commerce: Salesforce Commerce Cloud + integraciones custom.
- 12 entidades legales en 5 países; alcance acordado: las 4 entidades > 10% de ingresos consolidados.

---

## SKILLs activadas

| SKILL | Rol en el engagement |
|---|---|
| ⭐ `auditoria-financiera` | Especialidad ancla — define aseveraciones, marco contable |
| ⭐ `auditoria-tecnologia-informacion` | Para ITGCs y controles automatizados de aplicación |
| `evaluacion-controles` | Diseño y operación de controles (núcleo de SOX 404) |
| `muestreo` | Selección de transacciones para pruebas de operación |
| `analitica-datos` | Pruebas masivas (3-way match, cut-off, duplicados) |
| `papeles-trabajo` | Documentación auditable por externos |
| `comunicacion-hallazgos` | Reporting de deficiencias (CD / SD / MW) |

---

## Prompt inicial al agente

```
Activá las SKILLs auditoria-financiera, auditoria-tecnologia-informacion,
evaluacion-controles, muestreo, analitica-datos, papeles-trabajo,
comunicacion-hallazgos.

CONTEXTO:
RetailLatam Inc. (retailer omnichannel, USD 850M, listed NYSE FPI).
Año fiscal 2025 cerró 31-dic. Certificación SOX 404 sobre ciclo de
ingresos. SAP S/4HANA + Salesforce Commerce Cloud + integraciones custom.
Alcance: 4 entidades (>10% ingresos consolidados c/u).

OBJETIVO:
Producir evidencia para la opinión externa sobre ICFR del ciclo de
ingresos (revenue recognition bajo IFRS 15 / ASC 606).

NECESITO:
1. Mapeo de riesgos del ciclo de ingresos a aseveraciones afectadas
   (existencia, integridad, exactitud, corte, valuación, presentación).
2. Identificación de controles clave (key controls):
   - Manuales (entity-level + process-level)
   - Automatizados de aplicación (ITAC)
   - ITGCs dependientes
3. Para cada control clave, definí:
   - Frecuencia (anual, mensual, diaria, por evento)
   - Población esperada
   - Tamaño de muestra para pruebas de operación
   - Fuente de evidencia primaria
4. Definí un programa de analítica para complementar muestreo:
   - Cut-off de ingresos al cierre
   - Match factura-pedido-shipment (3-way match)
   - Duplicados de notas de crédito
   - Variaciones inusuales de margen por SKU
5. Esquema de clasificación de deficiencias:
   - Control deficiency (CD)
   - Significant deficiency (SD)
   - Material weakness (MW)

Citá COSO IC-IF 2013 y AS 2201 PCAOB en cada decisión relevante.
```

---

## Output esperado del agente (resumen)

### 1. Riesgos vs. aseveraciones (extracto)

| Riesgo | Existencia | Integridad | Exactitud | Corte | Valuación |
|---|:-:|:-:|:-:|:-:|:-:|
| Ingresos ficticios (channel stuffing) | ✓ | | ✓ | ✓ | |
| Ingresos no registrados | | ✓ | | ✓ | |
| Reconocimiento prematuro pre-shipment | ✓ | | | ✓ | ✓ |
| Cálculo incorrecto de descuentos / rebates | | | ✓ | | ✓ |
| Notas de crédito post-cierre con efecto retroactivo | ✓ | | ✓ | ✓ | ✓ |

### 2. Controles clave seleccionados (extracto)

| # | Control | Tipo | Frecuencia | Población | n muestra |
|---|---|---|---|---|---|
| C-01 | Aprobación de master data de cliente | Manual | Por evento | ~120/mes | 25 |
| C-02 | Validación 3-way match en SAP MM/SD | Automatizado (ITAC) | Real-time | N/A | Re-perform 1 caso |
| C-03 | Reconciliación diaria GL vs. e-commerce gateway | Manual | Diaria | ~250/año | 25 |
| C-04 | Aprobación gerencial de notas de crédito > USD 5K | Manual | Por evento | ~80/mes | 25 |
| C-05 | Cierre de período en SAP (transacción FAGLB03) | Automatizado + manual | Mensual | 12/año | 4 |
| C-06 | Provisión de devoluciones (modelo de retorno) | Manual EUC | Mensual | 12/año | 3 |

**ITGCs dependientes (extracto):**
- ITGC-Access-01: Provisioning/de-provisioning en SAP (si falla, falla C-01, C-04)
- ITGC-Change-01: Gestión de cambios en SAP customizations (si falla, falla C-02, C-05)
- ITGC-Ops-01: Ejecución de jobs batch de cierre (si falla, falla C-05)

### 3. Programa de analítica complementaria

| Prueba | Periodicidad | Población | Tecnología sugerida |
|---|---|---|---|
| Cut-off pre y post cierre (±5 días) | Una vez al cierre | 100% transacciones del rango | SQL sobre extract SAP + comparativa con WMS |
| 3-way match completo | Trimestral, último mes | 100% facturas | Python + pandas |
| Duplicados de notas de crédito | Mensual | 100% NC del mes | SQL |
| Margen anómalo por SKU | Mensual | 100% líneas | Python (z-score por SKU) |
| Ingresos manuales (journal entries directos a cuenta de revenue) | Trimestral | 100% JE manuales | SQL + revisión de documentación de respaldo |

### 4. Esquema de clasificación de deficiencias

```
            ¿La deficiencia, sola o combinada,
            podría resultar en un error material
            no prevenido o detectado oportunamente?
                          │
              ┌───────────┴───────────┐
              No                      Sí
              │                       │
              ▼                       ▼
       Control deficiency      ¿Es razonablemente posible
            (CD)               que el error material ocurra?
                                  │
                         ┌────────┴────────┐
                        No                Sí
                         │                 │
                         ▼                 ▼
              Significant deficiency  Material weakness
                       (SD)                (MW)
                                  ↓
                       MW debe revelarse en el 10-K
```

---

## Consideraciones de juicio profesional

1. **Top-down approach.** Empezar por entity-level controls, luego process-level. AS 2201 lo exige.

2. **Riesgo de fraude (ROMM).** Channel stuffing y revenue cut-off son riesgos significativos por presunción regulatoria. Asignar partner-level review.

3. **EUCs (End-User Computing).** El control C-06 (provisión de devoluciones) suele ser un Excel — tratarlo como EUC con controles compensatorios (locking, version control, revisión independiente).

4. **ITAC + ITGC bundling.** No se puede confiar en un control automatizado (ITAC) si los ITGCs subyacentes no son efectivos. La SKILL `auditoria-tecnologia-informacion` lo refuerza.

5. **Deficiencias agregadas.** Una colección de CDs en el mismo ciclo puede agregarse a SD o MW. Documentar la lógica de agregación.

6. **Walkthroughs anuales obligatorios.** Una vez por proceso, por año, mínimo. No se puede heredar del año anterior sin actualización formal.

---

## Entregables esperados al cierre

- Risk and Control Matrix (RCM) actualizada por ciclo.
- Workpapers por control (objetivo, atributos, muestra, resultados, conclusión).
- Programa de analítica con scripts versionados.
- Memo de evaluación de deficiencias con clasificación.
- Resumen ejecutivo para Comité de Auditoría.
- Paquete entregable al auditor externo (typical request list pre-cumplida).
