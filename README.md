# Piscinas Andinas

> **Escaparate público.** Versión de portafolio de este producto para demostrar diseño,
> arquitectura y flujos. No incluye infraestructura, configuración ni credenciales.

**High-conversion fiberglass pool company site**

**Version:** 1.0.0 · **Year:** 2026 · **Status:** LIVE

## Overview

A production-oriented marketing and lead-generation web app for a fiberglass pool company: A/B testing, analytics instrumentation, conversion tracking, live chat, SEO metadata, accessibility helpers, and runtime monitoring.

## Vitrina — capturas y documentación técnica

**[`vitrina/`](vitrina/README.md)** reúne la presentación pública del proyecto: 7 capturas del
sitio compilado (desktop y móvil), arquitectura, funcionalidades y ficha técnica.

| Documento | Contenido |
|---|---|
| [`vitrina/README.md`](vitrina/README.md) | Presentación, capturas, qué resuelve, alcance |
| [`vitrina/docs/ARQUITECTURA.md`](vitrina/docs/ARQUITECTURA.md) | Orden de proveedores y decisiones |
| [`vitrina/docs/FUNCIONALIDADES.md`](vitrina/docs/FUNCIONALIDADES.md) | Módulos y para quién existe cada uno |
| [`vitrina/docs/FICHA-TECNICA.md`](vitrina/docs/FICHA-TECNICA.md) | Stack, métricas y defectos corregidos |

Las capturas se generan automáticamente con Playwright desde el build; no son montajes manuales.

### Galería

**Escritorio**

| <a href="vitrina/screenshots/home.jpg"><img src="vitrina/screenshots/thumbs/home.jpg" width="250" alt="Portada"></a><br><sub><b>Portada</b></sub> | <a href="vitrina/screenshots/servicios.jpg"><img src="vitrina/screenshots/thumbs/servicios.jpg" width="250" alt="Servicios"></a><br><sub><b>Servicios</b></sub> | <a href="vitrina/screenshots/nosotros.jpg"><img src="vitrina/screenshots/thumbs/nosotros.jpg" width="250" alt="Nosotros"></a><br><sub><b>Nosotros</b></sub> |
|---|---|---|
| <a href="vitrina/screenshots/contacto.jpg"><img src="vitrina/screenshots/thumbs/contacto.jpg" width="250" alt="Contacto"></a><br><sub><b>Contacto</b></sub> | &nbsp; | &nbsp; |

**Móvil**

| <a href="vitrina/screenshots/mobile-home.jpg"><img src="vitrina/screenshots/thumbs/mobile-home.jpg" width="140" alt="Móvil · Portada"></a><br><sub><b>Móvil · Portada</b></sub> | <a href="vitrina/screenshots/mobile-servicios.jpg"><img src="vitrina/screenshots/thumbs/mobile-servicios.jpg" width="140" alt="Móvil · Servicios"></a><br><sub><b>Móvil · Servicios</b></sub> | <a href="vitrina/screenshots/mobile-contacto.jpg"><img src="vitrina/screenshots/thumbs/mobile-contacto.jpg" width="140" alt="Móvil · Contacto"></a><br><sub><b>Móvil · Contacto</b></sub> |
|---|---|---|

*7 capturas del build real. Cada imagen abre la versión completa; todas están en [`vitrina/screenshots/`](vitrina/screenshots).*

## Architecture

The codebase follows a component-based architecture with typed domain models and service abstractions ready for backend integration. See the `docs/`, `src/`, or `app/` directories for the module structure.

## Tech Stack

React · TypeScript · Vite · GA4

## Key Features

- `web` · `leads` · `conversion`

## Project Status

**LIVE** — actively maintained.

## Technical Highlights

- Typed TypeScript architecture with reusable component system
- Client-first product experience with service abstractions for future backends
- Modern build tooling and code-quality conventions
