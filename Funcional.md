# Objetivo
Limpieza y normalización del dataset de ventas, creación de features analíticas “Tableau-ready”, estadísticas descriptivas y export de un CSV final para reporting.

- Entradas: Amazon Sale Report.csv (crudo)
- Salidas: amazon_cleaned_for_tableau.csv (limpio, listo para Tableau)

# Alcances y exclusiones

- Incluido: limpieza, tipificación, features retail, sanity checks, EDA básica y export.
- Excluido: módulos avanzados (RFM, cohortes, missingness, IQR, duplicados, category mapping). Se removieron para esta entrega.

# Pipeline (visión de módulos)

## Parámetros & Paths: 
Centraliza rutas y listas de candidatos de columnas (fecha, qty, amount, price, status, order_id, etc.). Ajustando aquí, se adapta todo el flujo.

## Setup (imports + helpers): 
slugify (snake_case), to_number (coerción numérica robusta), find_first (auto-detección de columnas), normalize_status (buckets de estado).

## Carga de datos (robusta): 
Intenta utf-8→latin-1→cp1252, low_memory=False, manejo explícito de errores. Vista rápida (head) y shape.

## Normalización & limpieza básica: 
snake_case; elimina columnas totalmente nulas y duplicados exactos; sanea strings (espacios, "nan" textual → NaN).

## Tiempopificación (números & fechas): 
Heurística >70% para detectar numéricas y convertir con to_number. Date-safe parsing solo en columnas que son fechas (según DATE_COL_PRIORITY y DATEFIRST), sin tocar IDs.

# Features retail

- status_bucket (fulfilled / not_fulfilled / unknown).
- gross_revenue = amount o qty * price.
- Particiones de tiempo: order_year, order_month, order_week, order_weekday, order_hour, is_weekend.
- Flags: is_b2b, has_promo.
- Agregados por pedido: order_total, order_line_count, aov_by_order (repetido por línea para Tableau).

# Calidad de datos & reglas

- Conserva devoluciones/cancelaciones; elimina inconsistencias (p.ej., qty <= 0 con revenue positivo). Crea is_negative_revenue.

# Estadísticas & gráficos

- Filas/columnas, revenue total, #órdenes, AOV mean/median; distribución status_bucket; revenue por mes; Top categorías/SKUs.

# Export para Tableau

- Escribe amazon_cleaned_for_tableau.csv sin índice. Opcionalmente se pueden generar variantes (fulfilled_only, “light”) si hiciera falta.

# Decisiones clave

- No “arreglar” contablemente: devoluciones y cancelaciones se mantienen (negativas o not_fulfilled) y se filtran en reporting cuando aplique.
- Fechas seguras: solo se parsean columnas que lo son; IDs quedan a salvo.
- AOV accesible: aov_by_order duplicado por línea para evitar LODs en Tableau.
