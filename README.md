# 💊 Farmacia Alertas

Sistema de inventario multi-cliente para farmacias, con alertas de vencimiento, reposición de stock y notificaciones automáticas por correo.

🔗 **App en vivo:** https://jeremias123r.github.io/farmacia-alertas/

---

## ✨ Funcionalidades

- **Login seguro** por farmacia (Supabase Auth), con sesión persistente y recuperación de contraseña
- **Gestión de medicamentos**: alta, edición, venta y eliminación, con control de cantidad y stock mínimo
- **Alertas visuales por color**: vencido, por vencer (30 días), stock bajo, en orden
- **Buscador** por nombre, laboratorio, lote o fecha
- **Historial / Kardex**: registro automático de cada alta, entrada y salida de stock
- **Multi-tenant**: cada farmacia ve únicamente sus propios datos, aislados mediante Row Level Security (RLS)
- **Alertas automáticas por correo**: un script diario revisa el inventario y notifica si hay medicamentos vencidos o por vencer
- **Instalable como PWA**: funciona como app nativa en Android/escritorio, sin pasar por una tienda de aplicaciones

---

## 🏗️ Stack técnico

| Capa | Tecnología |
|---|---|
| Frontend | HTML + CSS + JavaScript (vanilla) |
| Backend / Base de datos | [Supabase](https://supabase.com) (PostgreSQL + Auth) |
| Seguridad | Row Level Security (RLS) por `farmacia_id` |
| Automatización de alertas | Python + GitHub Actions |
| Envío de correos | [Resend](https://resend.com) |
| Hosting | GitHub Pages |

---

## 📂 Estructura del proyecto

```
├── index.html          # Aplicación completa (frontend)
├── manifest.json        # Configuración de la PWA
├── sw.js                 # Service Worker (soporte offline/instalación)
├── alertas.py            # Script de alertas diarias por correo
└── .github/
    └── workflows/
        └── alertas.yml   # GitHub Action que ejecuta alertas.py todos los días
```

---

## 🗄️ Modelo de datos

- **`farmacias`** — una fila por cliente (id, nombre)
- **`Medicamentos`** — nombre, cantidad, stock mínimo, fecha de vencimiento, lote, laboratorio, presentación, `farmacia_id`
- **`movimientos`** — kardex: tipo (alta/entrada/salida), cantidad, stock resultante, `farmacia_id`

Cada fila de `Medicamentos` y `movimientos` está protegida por políticas RLS que solo permiten el acceso a usuarios cuyo `farmacia_id` (guardado en su sesión) coincide con el de la fila.

---

## 🔐 Variables de entorno (GitHub Secrets)

El workflow de alertas requiere estos secretos configurados en **Settings → Secrets and variables → Actions**:

| Secreto | Descripción |
|---|---|
| `SUPABASE_URL` | URL del proyecto de Supabase |
| `SUPABASE_KEY` | Llave `service_role` de Supabase (necesaria para que el script vea todos los datos pese a RLS) |
| `RESEND_API_KEY` | Llave de API de Resend |
| `CORREO_DESTINO` | Correo al que se envían las alertas |

---

## 🚀 Estado del proyecto

En uso activo por varias farmacias clientes. Próximas mejoras en evaluación: notificaciones por WhatsApp, importación masiva de medicamentos vía planilla, y escaneo de cajas por cámara.

---

Proyecto desarrollado por [Jeremías Robles Ochoa](https://github.com/Jeremias123R).
