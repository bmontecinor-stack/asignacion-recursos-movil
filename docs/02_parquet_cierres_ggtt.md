# 02 — PARQUET CIERRES GGTT

## Propósito
Consolidar cierres mensuales del canal GGTT en un parquet incremental.

## Input
Carpeta:
`C:\Users\bmontecino\OneDrive - Entel\Archivos de Tapia Viaux Javiera Magdalena - Bases cierre mes GGTT 2025`

Formato: Excel  
Hoja: nombre que comience con `Base cierre` (case-insensitive)

## Output
`A.R GO TO MARKET\MÓVIL\Consolidado GGTT Cierre Mes 2025.parquet`

## Reglas / Lógica
- 1 archivo suele representar 1 período.
- Incremental por período (según columna de mes).
- Si existe el período → reemplazo completo.

## Controles recomendados
- Duplicados por `Número Orden` (si aplica).
- Periodos detectados coherentes.
