# 💊 Farmacia Alertas — Demo

Demo funcional de un sistema de inventario para farmacias, desarrollado para demostrar gestión de inventario, alertas, autenticación, seguridad, automatización y despliegue web.

🔗 **App demo:** https://jeremias123r.github.io/Farmacia-demo/

> Esta versión es una demostración separada del sistema original y no contiene datos reales de clientes o pacientes.

---

## ✨ Funcionalidades

- **Login por farmacia** mediante Supabase Auth.
- **Sesión persistente** y recuperación de contraseña.
- **Gestión de medicamentos**: alta, edición, venta y eliminación.
- **Control de cantidad y stock mínimo**.
- **Alertas visuales** para medicamentos vencidos, próximos a vencer y stock bajo.
- **Buscador** por nombre, laboratorio, lote o fecha.
- **Historial de movimientos (Kardex)**.
- **Arquitectura multi-cliente (multi-tenant)**.
- **Aislamiento de datos** mediante Row Level Security (RLS).
- **Alertas automáticas por correo**.
- **Automatización diaria** mediante GitHub Actions.
- **Aplicación instalable como PWA**.
  ---

## 🏗️ Stack técnico

| Capa | Tecnología |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend / Base de datos | Supabase, PostgreSQL |
| Autenticación | Supabase Auth |
| Seguridad | Row Level Security (RLS) |
| Automatización | Python, GitHub Actions |
| Correo | Resend |
| Hosting | GitHub Pages |
| Aplicación | PWA |

---

## 🗄️ Modelo de datos

El sistema trabaja principalmente con:

### `farmacias`

Contiene la información de cada farmacia cliente.

### `Medicamentos`

Almacena información como:

- Nombre
- Cantidad
- Stock mínimo
- Fecha de vencimiento
- Lote
- Laboratorio
- Presentación
- `farmacia_id`

### `movimientos`

Registra el historial de movimientos del inventario:

- Alta
- Entrada
- Salida
- Cantidad
- Stock resultante
- `farmacia_id`

Las políticas de **Row Level Security (RLS)** permiten que cada farmacia pueda acceder únicamente a sus propios registros.
---

## 🔐 Seguridad

El proyecto utiliza **Supabase Auth** para la autenticación de usuarios y **Row Level Security (RLS)** para separar los datos de cada farmacia.

La relación mediante `farmacia_id` permite establecer qué registros pertenecen a cada cliente.

---

## 🤖 Automatización

El proyecto incorpora un script desarrollado en **Python** encargado de revisar el inventario.

El proceso puede detectar medicamentos:

- Vencidos.
- Próximos a vencer.

La ejecución se automatiza mediante **GitHub Actions**.

---

## 📧 Notificaciones

Para el envío de correos se utiliza **Resend**.

El flujo general es:

Inventario → Python → Revisión de vencimientos → Alerta → Correo electrónico

---

## 📱 PWA

La aplicación incorpora características de **Progressive Web App (PWA)**.

Incluye:

- `manifest.json`
- Service Worker
- Instalación en Android y escritorio
- Experiencia similar a una aplicación instalada

---

## 📂 Estructura del proyecto

```text
├── index.html
├── manifest.json
├── sw.js
├── alertas.py
└── .github/
    └── workflows/
        └── alertas.yml
🎯 Objetivo del proyecto
Este proyecto demuestra conocimientos en:
Desarrollo frontend
JavaScript
Bases de datos
Autenticación
Seguridad mediante RLS
Arquitecturas multi-tenant
Python
Automatización
GitHub Actions
APIs externas
PWA
Despliegue web
🚀 Próximas mejoras
Notificaciones mediante WhatsApp.
Importación masiva de medicamentos desde planillas.
Escaneo de productos mediante cámara.
Mejoras en reportes e indicadores.
Mayor automatización de procesos.
👨‍💻 Autor
Proyecto desarrollado por Jeremías Robles Ochoa como parte de su portafolio de desarrollo web y soluciones digitales.

Después de pegarlo, **no guardes todavía**. Dime **“listo”** y revisamos que todo esté bien antes de hacer el `Commit changes`.
