# Lux_off — tienda de perfumes

Sitio estático para GitHub Pages con catálogo conectado a Supabase, carrito y flujo de pedidos/reservas que prepara un mensaje de seguimiento para WhatsApp.

## Estado actual
- `index.html`: página inicial de la tienda, diseño negro y dorado, catálogo demostrativo, carrito y solicitud de perfume.
- `supabase-schema.sql`: esquema inicial de base de datos.
- `supabase-orders-migration.sql`: migración para alinear columnas de productos y conectar pedidos, reservas, confirmación/cancelación y panel administrativo.
- WhatsApp de atención: 951 203 8764.

**Importante:** el flujo de pedidos requiere ejecutar `supabase-orders-migration.sql` en el proyecto Supabase correcto y verificar que el usuario administrador esté en `public.admin_users`. La reserva no se confirma como venta hasta que el administrador pulse “Confirmar venta”. Prueba el flujo completo antes de usarlo con clientes reales.

## Publicar en GitHub Pages
1. Abre Settings → Pages.
2. En Build and deployment, elige Deploy from a branch.
3. Selecciona rama main y carpeta /(root); pulsa Save.
4. Espera el enlace que GitHub muestra en esa sección.

## Configuración de Supabase
1. Crea un proyecto en https://supabase.com/.
2. En SQL Editor ejecuta el esquema inicial `supabase-schema.sql` si todavía no lo habías aplicado.
3. Después, abre `supabase-orders-migration.sql`, copia todo su contenido en una consulta nueva del SQL Editor y ejecútalo.
4. En Authentication → Users confirma que existe tu usuario administrador y copia su UUID.
5. Si tu usuario no se copió desde `public.lux_admins`, ejecuta en SQL Editor: `insert into public.admin_users(user_id) values ('UUID-DEL-USUARIO') on conflict do nothing;` sustituyendo el texto por el UUID real.
6. La página usa Project URL y una clave publicable. Nunca expongas la clave service_role.
7. Prueba una reserva, la confirmación y la cancelación antes de usar el inventario real.

No se procesan pagos en línea. La venta se confirma directamente por WhatsApp.
