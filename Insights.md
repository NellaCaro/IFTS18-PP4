# Insights & Hallazgos

## Snapshot de métricas clave

### Panel económico (reporting “de resultados”) — usa solo cumplidas

- Pedidos únicos: 100.358
- Revenue total (líneas): 69.673.721
- AOV (media/mediana): 694,25 / 635,00
- Pedidos de 1 ítem: 94,23%

### Panel operativo (calidad del proceso) — universo completo

- Filas: 128.975 | Columnas: 30
- Pedidos únicos: 120.378
- No cumplidas: 15,84% (KPI de salud)
- Pedidos de 1 ítem: 94,31%

Nota: 
    Económico = status_bucket = 'fulfilled'. 
    Operativo = todas las líneas (incluye cancel/return/refund). 
    Las devoluciones impactan como negativos en revenue. Cálculo de AOV: suma por pedido / pedidos.

# Patrones, tendencias e insights
### Tasa de no cumplimiento elevada (~15,8%)
- Riesgo: erosiona margen y experiencia.
- Siguientes pasos: desglose por SKU / categoría / canal para detectar responsables; revisar fit/talles, expectativa de despacho, y fricción de pago.
- Métrica de seguimiento: not_fulfilled_rate semanal y por campaña.

### Carritos de un solo ítem (~94%)
- Oportunidad: cross-sell inteligente (accesorios/colores/talles).
- Implementación: “Frequently bought together”, bundles dinámicos y ofertas 2× (pricing en escalones).
- Métrica: attach rate (items por pedido) y uplift AOV.

### Concentración de revenue en pocas categorías/SKUs
- Pro: foco para campañas y stock.
- Contra: dependencia; si el líder cae, el mes se resiente.
- Acción: asegurar stock crítico y diseñar derivaciones (recomendaciones) hacia 2ª/3ª categoría.

### Geografía como palanca
- Estados líderes: Maharashtra, Karnataka, Telangana, Uttar Pradesh, Tamil Nadu.
- Acciones: optimizar logística y CPA en paid media; testear ofertas localizadas.
- Métricas: margen post-envío por estado y tiempo a entrega (sumar ship_date para medir SLA real).
