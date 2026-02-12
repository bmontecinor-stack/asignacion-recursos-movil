# 📊 ASIGNACIÓN DE RECURSOS – MÓVIL (End-to-End)

## 1) Objetivo

Este proyecto consolida información operativa y financiera para el proceso **Asignación de Recursos – Móvil**, integrando:
- Ventas / base operativa (FLO Segmentos)
- Cierres del canal GGTT
- QNP (calidad/no pago)
- Curvas de permanencia (por Canal y por Segmento)

El resultado final se utiliza en **Power BI** para análisis y visualización, relacionando:
- **Sábana de Ingresos Final (Móvil)** (ingresos proyectados + variables operativas)
- **Sábana de Gasto de Venta** (costos por canal-proceso)

---

## 2) Alcance

Incluye:
- Consolidación incremental mensual (parquets)
- Cruces FLO + QNP + GGTT
- Generación de archivo “TNP para curvas”
- Aplicación de curvas de permanencia
- Cálculo de ingresos proyectados a 12 meses
- Carga y modelamiento en Power BI (relaciones + transformaciones)
- Visualización de métricas de negocio

No incluye:
- Automatización de publicación (Service) ni pipelines DevOps (por ahora)

---

## 3) Fuentes y Salidas (alto nivel)

### Fuentes (Inputs)
- **FLO Segmentos (Excel)**: carpeta de Segmentos (mensual)
- **Cierres GGTT (Excel)**: carpeta cierres GGTT (mensual)
- **QNP (Excel)**: carpeta bases QNP (mensual)
- **Permanencias Control de Gestión Móvil v2 (Excel)**: curvas por canal
- **Permanencias Segmentos (Excel)**: curvas por segmento
- **DICCIONARIO.xlsx**: parametrizaciones y catálogos
- **GASTO DE VENTA (base para Power BI)**: costos por canal-proceso (fuente paralela a ingresos)

### Salidas (Outputs)
- **Consolidado Movil Hogar FLO.parquet** (sábana madre operacional)
- **Consolidado QNP.parquet**
- **Consolidado GGTT Cierre Mes 2025.parquet**
- **Consolidado FLO + QNP + GGTT+PRE_ING.parquet**
- **TNP para curvas.xlsx**
- **Consolidado Ingresos Final Movil.parquet** (base final para BI)
- **Power BI**: modelo con Ingresos Final + Gasto de Venta y visualizaciones

---

## 4) Arquitectura del Pipeline (end-to-end)

### A) Construcción de datos (Python → Parquet)
1. `PARQUET CONSOLIDADO MOVIL FLO`  
2. `PARQUET CIERRES GGTT`  
3. `PARQUET QNP MOVILES 2025`  
4. `1. FLO+QNP+GGTT+PRE_ING Y CREA TNP CURVAS`  
5. `2. CONSOLIDADO INGRESOS FINAL`  

### B) Consumo analítico (Power BI)
6. Power BI carga:
- `Consolidado Ingresos Final Movil.parquet`
- Base `GASTO DE VENTA` (costos canal-proceso)

7. Power BI:
- Relaciona ambas bases
- Aplica transformaciones/modelado
- Construye visuales y métricas de negocio

---

## 5) Lógica de negocio clave

- Consolidación incremental por **período** (Mes (numérico) / id_mes):
  - si el período ya existe → se reemplaza completo
  - si no existe → se agrega
- Cruces por llaves normalizadas (ej. orden / rut / teléfono según disponibilidad)
- Curvas aplicadas en dos niveles:
  - **Curva Canal**
  - **Curva Segmento**
- Ingresos:
  - cálculo de ingreso de actividad 12M (curva × precio) + ingreso churn
  - totales por canal y por segmento según curvas asignadas

---

## 6) Controles de calidad recomendados

- Periodos detectados vs esperados (ej. 202601 presente)
- % match por cruce (FLO↔QNP, FLO↔GGTT, PRE_ING↔Curvas)
- Duplicados por llaves relevantes (nro_orden / Número Orden)
- Validación de nulos en campos críticos (precio, curva, ingreso)
- Revisión de outliers de ingresos (negativos o extremos)

---

## 7) Documentación detallada

- Ver fichas de cada módulo en `/docs`
- Glosario y definiciones de campos en `/docs/00_glosario.md`

---

## 8) Owner

Bernardo Montecino — Líder de Proyecto (Entel)
