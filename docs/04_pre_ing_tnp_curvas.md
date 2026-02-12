# 04 — 1. FLO + QNP + GGTT + PRE_ING y crea TNP CURVAS

## Propósito
Integrar los parquets consolidados (FLO, QNP, GGTT) y generar:
- Base enriquecida `PRE_ING`
- Archivo `TNP para curvas.xlsx` para soporte de actualización de curvas

## Inputs
- `Consolidado Movil Hogar FLO.parquet`
- `Consolidado QNP.parquet`
- `Consolidado GGTT Cierre Mes 2025.parquet`
- `DICCIONARIO.xlsx`

## Outputs
- `Consolidado FLO + QNP + GGTT+PRE_ING.parquet`
- `TNP para curvas.xlsx`

## Reglas / Transformaciones (alto nivel)
- Cruces por llaves normalizadas.
- Creación y/o recalculo de campos como:
  - `Precio A.R`, `PF RW`, `ARPU MIS`, `PM12`, `Ingreso Churn 12M`
- Preparación de llaves para etapas posteriores (curvas).

## Controles recomendados
- % match en cruces (FLO↔QNP, FLO↔GGTT)
- Revisión de valores nulos en `Precio A.R`
- Revisión de filas sin curva esperada (casos especiales)
