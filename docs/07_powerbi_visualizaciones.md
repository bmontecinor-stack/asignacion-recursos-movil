# 07 — Power BI: Visualizaciones y Métricas

## Propósito
Construir visuales para consumo de negocio y chapter técnico, asegurando trazabilidad (medidas claras) y consistencia.

## Entradas
- Modelo con:
  - Ingresos Final
  - Gasto de Venta
  - Relaciones/Dimensiones

## Visuales típicos (ejemplos)
- Ingreso vs Gasto por período
- Ingreso unitario por canal / segmento
- Participación por canal
- Métricas de eficiencia (ej: gasto/ingreso)
- Tendencias MoM / YoY (si aplica)

## Buenas prácticas
- Medidas DAX con naming consistente (prefijos: `M_` para measures).
- Tablas dimensión para ordenar categorías (sort by column).
- Página “Calidad” con checks: filas, periodos, % nulos, etc.

## Controles recomendados
- Totales coherentes al filtrar por canal/periodo.
- Revisión de medidas sensibles (promedios vs sumas).
- Validación de que “Ingresos” y “Gasto” están en la misma granularidad al comparar.
