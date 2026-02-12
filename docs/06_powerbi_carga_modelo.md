# 06 — Power BI: Carga y Modelo (Ingresos + Gasto de Venta)

## Propósito
Cargar en Power BI las dos “sábanas” principales y construir el modelo relacional para análisis.

## Fuentes en Power BI
1) **Ingresos**
- `Consolidado Ingresos Final Movil.parquet`

2) **Costos**
- Base `GASTO DE VENTA` (costos por canal-proceso)

## Resultado esperado
- Ambas bases cargadas.
- Tablas de dimensiones (si aplica) creadas/ordenadas.
- Relaciones definidas para cruzar ingresos vs gasto.

## Reglas recomendadas (modelo)
- Definir una **llave de periodo** común (ej: `PERIODO` tipo YYYYMM).
- Alinear dimensiones:
  - Canal / Canal Gestión Final
  - Proceso
  - Segmento (si corresponde)
- Preferir un esquema tipo estrella (facts + dims) cuando sea posible.

## Controles recomendados
- Revisar cardinalidad y dirección de filtro en relaciones.
- Validar totales de ingresos y gastos por periodo.
- Validar que el slicer de periodo filtre ambas tablas.
