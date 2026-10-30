# Lugar libre (beta)

Web con mapa donde conductores comparten su ubicación real (con permiso), marcan "me voy" y otro conductor puede aceptar el espacio liberado dentro de una ventana de 4 minutos.

## Stack
- Front: HTML estático (Leaflet + OpenStreetMap)
- Backend: Supabase (Auth anónimo, Postgres con RLS, Realtime)

## Configuración
- En Supabase, activar *Anonymous sign-ins* (Authentication → Sign In / Providers).
- La clave en `index.html` es la publishable key; la seguridad está en las reglas RLS y en las funciones `release_spot`, `update_position`, `accept_spot`, `cancel_my_spot`, `server_now`.

## Acceso
- Código de acceso de la beta: se valida con la función `join_with_code` contra la tabla `access_codes` (no está en el front).
- Solo las sesiones en `allowed_users` ven espacios y pueden usar las funciones (`is_allowed`).
