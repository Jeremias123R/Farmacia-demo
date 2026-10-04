# Inventario de farmacia

Aplicación web para controlar el inventario de una farmacia, con alertas de vencimiento y de reposición de stock. Funciona desde el celular y se puede instalar como app.

**Ver demo:** https://jeremias123r.github.io/Farmacia-demo/

Cuenta de prueba: `demo@farmacia` / `farmacia2026` (datos ficticios)

## Qué hace

- Inicio de sesión por usuario. Cada farmacia ve solo sus propios datos.
- Lista de medicamentos agrupada por laboratorio, con buscador por nombre, laboratorio, lote o fecha.
- Alertas de vencimiento (vencidos y por vencer en 30 días) y de stock bajo.
- **Ingreso de mercadería:** cantidad, número de factura o recibo, lote y vencimiento. Si llega un lote distinto, se crea como registro nuevo.
- Etiqueta **"Sale primero"** en el lote que vence antes, cuando hay varios lotes del mismo medicamento.
- **Dar salida** de unidades del inventario.
- **Historial completo** de movimientos (productos nuevos, mercadería que llegó, salidas), con buscador, filtro por tipo, número de factura y botón "Ver más".
- Cambio de contraseña y recuperación por correo.
- Alertas automáticas con Python y GitHub Actions.
- App instalable en el celular (PWA).

## Tecnologías

HTML, CSS y JavaScript · Supabase (autenticación, base de datos PostgreSQL y políticas de seguridad por fila) · Python · GitHub Actions · GitHub Pages

## Datos y privacidad

La demo usa un proyecto aparte, con datos 100% ficticios. No contiene información de ninguna farmacia real.

## Pendiente

- Completar la tabla de lotes con descuento automático del lote que vence primero.
- Registrar las eliminaciones en el historial.
- Diferenciar ventas, retiros y mermas en las salidas.

## Autor

Jeremías Robles Ochoa
