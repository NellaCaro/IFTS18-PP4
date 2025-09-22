# 📊 EDA – Amazon Sale Report

Este repositorio contiene el trabajo práctico de **Análisis Exploratorio de Datos (EDA)** realizado sobre el dataset **Amazon Sale Report**.

El proyecto incluye:
- Limpieza y preprocesamiento del dataset.
- Auditoría de calidad de datos.
- Desarrollo de nuevas variables.
- Estadísticas descriptivas y análisis de outliers.
- Extracción de insights iniciales.
- Export de dataset limpio para visualización en **Tableau**.

---

## 📂 Estructura del repositorio

├── Amazon Sale Report.csv # Dataset original
├── EDA_Amazon_Sales_ENHANCED.ipynb # Notebook con el EDA completo
├── Amazon_Sale_Report_CLEAN.csv # Dataset limpio (separador ; , coma decimal)
├── Amazon_Sale_Report_CLEAN_TABLEAU.tsv # Dataset limpio en TSV (para Tableau)
└── README.md # Este archivo


---

## 🚀 Flujo de trabajo

1. **Carga y vista inicial**
   - Exploración del dataset original.
   - Revisión de estructura, columnas y tipos de datos.

2. **Limpieza y preprocesamiento**
   - Estandarización de nombres de columnas.
   - Conversión de tipos (`Date`, `Qty`, `Amount`, `ship-postal-code`).
   - Normalización de `ship-city`, `ship-state`, `ship-country`.
   - Eliminación de duplicados.

3. **Auditoría de calidad**
   - Conteo de nulos.
   - Fechas inválidas.
   - Reglas de consistencia (ej. `Qty <= 0`, `Amount < 0`).
   - Revisión de categorías (`Status`, `Courier Status`, `currency`).

4. **Desarrollo de nuevas variables**
   - Variables temporales: `Year_num`, `Month_str`, `Day_num`, `Dow`.
   - Indicadores: `UnitPrice_est`, `Order_Status_Bucket`, `Sales_Channel_Bucket`.
   - Flags: `Amount_is_null`, `*_is_outlier`.

5. **Outliers y reglas de negocio**
   - Método IQR para `Amount` y `UnitPrice_est`.
   - Reglas de coherencia (cantidad cero con monto positivo, etc.).

6. **Estadísticas descriptivas**
   - Medidas básicas (`describe`).
   - Distribuciones categóricas (top categorías, estados, ciudades).
   - KPIs: ingresos totales, ticket promedio, % de pedidos exitosos.

7. **Insights preliminares**
   - Categoría y ciudad top por ingresos.
   - Evolución mensual (crecimiento y mes pico).
   - % de cancelaciones.
   - Registros outliers detectados.

8. **Export**
   - Dataset limpio en formatos **CSV** y **TSV** para análisis posterior en Tableau.

---

## 📈 Visualización en Tableau

El análisis visual se complementa en Tableau (no incluido en este repo), donde se desarrollan dashboards como:
- **Top 10 ciudades por ventas.**
- **Ventas por categoría.**
- **Tendencia mensual de ingresos.**
- **Distribución de pedidos exitosos vs cancelados.**

---

## 🧾 Recomendaciones y decisiones tomadas

- Conservar registros con nulos en `Amount`, pero añadir flag para filtrar en BI.
- Normalizar ubicaciones para evitar duplicados por diferencias de escritura.
- No eliminar outliers automáticamente: se marcan para revisión.
- Agregar variables derivadas para enriquecer el análisis descriptivo.
- Exportar datasets en formatos compatibles tanto con Python como con Tableau.

---

## 🛠️ Tecnologías utilizadas

- **Python** (pandas, numpy, re)
- **Jupyter Notebook**
- **Tableau** (visualización)
- **GitHub** (control de versiones y presentación)
