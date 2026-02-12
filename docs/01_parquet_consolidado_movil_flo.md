# 01 — PARQUET CONSOLIDADO MOVIL FLO

## Propósito
Consolidar archivos mensuales de Segmentos (FLO) en una sábana madre incremental en formato parquet.

## Input
Carpeta:
`C:\Users\bmontecino\OneDrive - Entel\Archivos de Saavedra Cabrera Florencia - 15. Segmentos`

Formato: Excel  
Hoja: `Base` (case-insensitive)

## Output
Archivo parquet:
`A.R GO TO MARKET\MÓVIL\Consolidado Movil Hogar FLO.parquet`

## Reglas / Lógica
- Consolidación incremental por `Mes (numérico)`.
- Si el período existe en el parquet → reemplazo completo del período.
- Si no existe → append del período.

## Controles recomendados
- Conteo de filas por período (antes vs después).
- Periodos detectados correctos.
- Validación de columnas mínimas esperadas.
