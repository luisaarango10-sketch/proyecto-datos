# Modelo de datos: inventario de la tienda de patines

Es un **dataset** (archivos CSV), no una base de datos. Las tablas se relacionan por columnas llave.

## Relaciones
- `proveedores` (1) → (N) `productos` por `id_proveedor`
- `productos` (1) → (N) `movimientos_inventario` por `id_producto`

## Tabla: productos
Un registro por producto (referencia, talla y color). Archivo: `productos.csv`

| Columna | Tipo | Significado |
|---|---|---|
| id_producto | texto | Código único del producto (llave primaria), ej. PAT-0001 |
| nombre | texto | Nombre comercial, ej. "Patín en línea Pro" |
| categoria | texto | Patines en línea, patines clásicos, protecciones, repuestos |
| marca | texto | Marca del producto |
| talla | texto | Talla del producto, si aplica |
| color | texto | Color del producto |
| costo_unitario | número | Lo que le cuesta a la tienda cada unidad |
| precio_venta | número | Precio al público |
| stock_minimo | entero | Unidades mínimas antes de pedir más (punto de reorden) |
| id_proveedor | texto | Llave foránea → proveedores.id_proveedor |

## Tabla: proveedores
Un registro por proveedor. Archivo: `proveedores.csv`

| Columna | Tipo | Significado |
|---|---|---|
| id_proveedor | texto | Código único del proveedor (llave primaria) |
| nombre_empresa | texto | Nombre de la empresa proveedora (ficticia) |
| ciudad | texto | Ciudad del proveedor |
| dias_entrega | entero | Días que tarda en entregar un pedido |

## Tabla: movimientos_inventario
Un registro por cada entrada o salida de mercancía. Archivo: `movimientos_inventario.csv`

| Columna | Tipo | Significado |
|---|---|---|
| id_movimiento | texto | Código único del movimiento (llave primaria) |
| fecha | fecha | Fecha del movimiento (AAAA-MM-DD) |
| id_producto | texto | Llave foránea → productos.id_producto |
| tipo_movimiento | texto | "entrada" (compra) o "salida" (venta) |
| cantidad | entero | Unidades que entran o salen |
| observacion | texto | Nota opcional, ej. "devolución" |

## Cálculo del stock
Stock actual de un producto = suma de entradas − suma de salidas.

## Notas
- Todos los datos son inventados; no hay datos personales reales.
