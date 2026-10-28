# Lux_off — tienda de perfumes

Sitio estático para GitHub Pages. Incluye catálogo de demostración, carrito y formularios que preparan un mensaje para WhatsApp.

## Estado actual
- `index.html`: página inicial de la tienda, diseño negro y dorado, catálogo demostrativo, carrito y solicitud de perfume.
- `supabase-schema.sql`: esquema inicial de base de datos para inventario compartido, reservas y acciones administrativas.
- WhatsApp de atención: 951 203 8764.

**Importante:** el inventario que se ve en la página inicial es demostrativo y no se reserva de forma compartida. El panel de administración todavía requiere integración con Supabase. No uses la tienda para ventas reales hasta configurar y probar el backend. No introduzcas contraseñas reales en el panel de demostración.

## Publicar en GitHub Pages
1. Abre Settings → Pages.
2. En Build and deployment, elige Deploy from a branch.
3. Selecciona rama main y carpeta /(root); pulsa Save.
4. Espera el enlace que GitHub muestra en esa sección.

## Configuración de Supabase
1. Crea un proyecto en https://supabase.com/.
2. En SQL Editor crea una consulta nueva, pega todo `supabase-schema.sql` y ejecútala.
3. En Authentication → Users crea el usuario administrador y copia su UUID.
4. Ejecuta en SQL Editor: `insert into public.admin_users(user_id) values ('UUID-DEL-USUARIO');` sustituyendo el texto por el UUID real.
5. La integración frontend aún debe conectarse al Project URL y a la clave anon/public. Nunca expongas la clave service_role.
6. Prueba reservas, cancelación y confirmación antes de usar el inventario real.

No se procesan pagos en línea. La venta se confirma directamente por WhatsApp.
