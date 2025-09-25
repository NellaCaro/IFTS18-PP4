# Retail EDA & Cleaning

Notebook modular para limpiar un dataset de ventas, crear features analíticas y exportar un CSV listo para Tableau.

## Estructura del pipeline (módulos 1–9)
1. Parámetros & Paths  
2. Setup (imports + helpers)  
3. Carga de datos (robusta, múltiples encodings)  
4. Normalización & limpieza básica (snake_case, duplicados, strings)  
5. Tipificación (números & fechas, date-safe parsing)  
6. Features retail (status_bucket, gross_revenue, tiempo, flags, AOV)  
7. Calidad de datos & reglas (inconsistencias y `is_negative_revenue`)  
8. Estadísticas & gráficos (sanity + tendencias + Top-N)  
9. Export para Tableau (`amazon_cleaned_for_tableau.csv`)

## Requisitos
- Python 3.9+  
- `pandas`, `numpy`, `matplotlib`

## Uso rápido
1. Copiá `Amazon Sale Report.csv` junto al notebook.  
2. Abrí `Retail_EDA_Cleaning.ipynb` y ejecutá las celdas en orden.  
3. Encontrarás el resultado en `amazon_cleaned_for_tableau.csv`.

## Decisiones de diseño
- **Fechas seguras**: solo columnas que lo son (evita romper IDs).  
- **Revenue fiel**: devoluciones/cancelaciones se mantienen (negativos o bucket).  
- **Tableau-ready**: `aov_by_order` disponible por línea para evitar LODs.
