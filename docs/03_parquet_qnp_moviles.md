# 03 — PARQUET QNP MOVILES 2025

## Propósito
Consolidar bases mensuales de QNP en un parquet incremental.

## Input
Carpeta:
`C:\Users\bmontecino\OneDrive - Entel\A.R GO TO MARKET\MÓVIL\BASES QNP`

Formato: Excel  
Hoja: `Base` o `Hoja1` (según archivo)

## Output
`A.R GO TO MARKET\MÓVIL\Consolidado QNP.parquet`

## Reglas / Lógica
- Incremental por `id_mes`.
- Limpieza/estandarización de tipos y columnas críticas.

## Controles recomendados
- Periodos faltantes.
- Distribución de QNP por mes (sanity check).
