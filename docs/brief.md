# Brief del proyecto: Inventario de una tienda de patines

## 1. Pregunta de negocio
¿Qué productos de la tienda se están agotando, cuáles se quedan sin rotar y cuánto debería comprar la tienda el próximo mes para no perder ventas ni acumular inventario?

## 2. Quién decide
- **Decisor:** la persona dueña o administradora de la tienda.
- **Decisión que apoya:** qué referencias reponer, en qué cantidad y a qué proveedor, y qué productos poner en promoción.

## 3. Fuente de datos
- Dataset sintético (inventado para este ejercicio), en archivos CSV:
  `productos`, `proveedores`, `movimientos_inventario`.
- Periodo cubierto: enero a diciembre de 2026.
- Actualización: archivos estáticos; no hay conexión a un sistema en vivo.

## 4. Alcance
- Control de existencias por producto (talla, color, categoría).
- Entradas por compras a proveedores y salidas por ventas.
- Indicadores: stock actual, rotación, productos bajo el punto de reorden y productos sin movimiento.

## 5. Qué NO incluye
- Ventas detalladas por cliente ni datos de clientes.
- Contabilidad, impuestos ni facturación.
- Predicción avanzada de demanda.
- Datos personales reales: todo el dataset es inventado.

## 6. Riesgos de calidad de datos
| Riesgo | Cómo lo reviso |
|---|---|
| Un mismo producto escrito de formas distintas (por ejemplo "Patin" y "Patín") | Estandarizar nombres y usar siempre el código de producto |
| Stock negativo por ventas registradas sin entrada previa | Revisar que ningún saldo baje de cero |
| Movimientos con productos que no existen en el catálogo | Cruzar `id_producto` entre tablas |
| Tallas o categorías mal digitadas | Usar una lista cerrada de valores |
| Fechas en formatos mezclados | Unificar a AAAA-MM-DD |
| Costos o precios en cero o vacíos | Contar vacíos y decidir cómo tratarlos |
