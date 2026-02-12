# 05 — 2. CONSOLIDADO INGRESOS FINAL

## Propósito
Aplicar curvas de permanencia y calcular ingresos proyectados a 12 meses, generando la base final para Power BI.

## Inputs
- `Consolidado FLO + QNP + GGTT+PRE_ING.parquet`
- `PERMANENCIAS\Permanencias Control de Gestión Móvil v2.xlsx` (curvas por canal)
- `PERMANENCIAS\Permanencias Control de Gestión Móvil v2 segmentos.xlsx` (curvas por segmento)

## Output
- `Consolidado Ingresos Final Movil.parquet`

## Reglas / Transformaciones (alto nivel)
- Generación/normalización de llaves:
  - `LLAVE_MIS` y `LLAVE_NO_MIS`
- Asignación de curvas:
  - `Curva Ingreso 12m (Canales)`
  - `Curva Ingresos 12m (Segmentos)`
- Cálculos de ingreso:
  - `Ingreso Actividad 12M`
  - `Ingreso Actividad 12M TOTAL CANAL`
  - `Ingreso Actividad 12M TOTAL SEGMENTO`

## Controles recomendados
- % filas con curva asignada (canal/segmento)
- Revisión de periodos problemáticos (ej. 202601)
- Outliers de ingresos y precios
