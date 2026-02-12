# 📊 ASIGNACIÓN DE RECURSOS – MÓVIL

## 1. Objetivo del proceso

El proceso de **Asignación de Recursos – Móvil** tiene como objetivo:

- Consolidar información operativa y financiera de múltiples fuentes.
- Integrar datos de ventas, QNP, cierres GGTT y permanencias.
- Calcular ingresos proyectados a 12 meses.
- Generar una sábana consolidada final para análisis estratégico y toma de decisiones.

Este flujo permite transformar bases operativas dispersas en un modelo consolidado de ingresos y curvas de permanencia.

---

## 2. Alcance

Incluye:

- Consolidación incremental mensual
- Cruce de bases FLO, GGTT y QNP
- Generación de TNP para curvas
- Aplicación de curvas de permanencia
- Cálculo de ingresos proyectados
- Generación de parquet final consolidado

No incluye:
- Modelamiento en Power BI
- Análisis de performance o visualizaciones

---

## 3. Arquitectura General del Pipeline

Excel FLO (Segmentos)
        ↓
PARQUET CONSOLIDADO MOVIL FLO
        ↓
Excel QNP → PARQUET QNP
        ↓
Excel GGTT → PARQUET CIERRES GGTT
        ↓
1. FLO + QNP + GGTT + PRE_ING + TNP
        ↓
TNP para curvas.xlsx
        ↓
Permanencias Control Gestión v2
        ↓
2. CONSOLIDADO INGRESOS FINAL
        ↓
Consolidado Ingresos Final Movil.parquet

---

## 4. Estructura del Proceso

El pipeline está dividido en 5 módulos independientes:

1. Consolidación FLO
2. Consolidación GGTT
3. Consolidación QNP
4. Integración + PRE_ING + generación TNP
5. Aplicación de curvas + cálculo final de ingresos

Cada módulo puede ejecutarse de forma independiente y es incremental por período.

---

## 5. Inputs Principales

| Fuente | Tipo | Frecuencia |
|--------|------|------------|
| Segmentos (FLO) | Excel | Mensual |
| Cierres GGTT | Excel | Mensual |
| QNP | Excel | Mensual |
| Permanencias Control Gestión v2 | Excel | Actualización periódica |
| Diccionario | Excel | Bajo demanda |

---

## 6. Outputs Principales

| Archivo | Descripción |
|---------|-------------|
| Consolidado Movil Hogar FLO.parquet | Sábana madre operacional |
| Consolidado QNP.parquet | Base QNP consolidada |
| Consolidado GGTT.parquet | Cierres canal GGTT |
| Consolidado FLO + QNP + GGTT + PRE_ING.parquet | Base enriquecida pre-ingresos |
| TNP para curvas.xlsx | Input para curvas |
| Consolidado Ingresos Final Movil.parquet | Base final lista para análisis |

---

## 7. Lógica de Negocio Clave

- Consolidación incremental por Mes (numérico)
- Reemplazo completo del período si ya existe
- Cruces mediante llaves normalizadas
- Aplicación diferenciada de curvas:
  - MIS
  - NO MIS
- Cálculo de:
  - Precio A.R
  - Ingreso Churn 12M
  - Ingreso Actividad 12M
  - Ingreso Total Canal / Segmento

---

## 8. Controles de Calidad Recomendados

- Validación de periodos detectados
- % match en cruces
- Duplicados por llave
- Validación de ingresos negativos o nulos
- Consistencia de curvas asignadas

---

## 9. Owner del Proceso

Responsable funcional y técnico:
Bernardo Montecino  
Líder de Proyecto – Entel
