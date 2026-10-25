# Ficha técnica

## Stack

| Capa | Tecnología | Por qué |
|---|---|---|
| Framework | **React 18 + Vite** | interfaz reactiva y build rápido con fragmentos separados |
| Lenguaje | **TypeScript** | catálogo y cotización con tipos, sin `any` sueltos |
| Estilos | **Tailwind CSS** | consistencia visual sin CSS disperso |
| Rutas | **React Router** | navegación sin recarga |
| Metadatos | **React Helmet Async** | título y datos estructurados por ruta |
| Formularios | **Formspree** | envío sin backend propio (desactivado en la vitrina) |
| Monitoreo | **Sentry** | captura de errores y trazas |
| Analítica | **react-ga4 + Hotjar** | medición de tráfico y comportamiento |
| PWA | **vite-plugin-pwa** | instalable y con soporte sin conexión |
| Iconografía | **Lucide** | iconos consistentes y livianos |

## Tamaño del proyecto

| Métrica | Valor |
|---|---|
| Archivos `.ts` / `.tsx` | 60 |
| Líneas de código | ~14.100 |
| Dependencias de producción | 11 |
| Familias de componentes | 18 |
| Rutas | 4 |
| Peso del build | ~3,2 MB |

## Familias de componentes

`ABTesting` · `AI` · `Accessibility` · `Analytics` · `CRM` · `CookieConsent` · `EmailMarketing` ·
`ErrorBoundary` · `Forms` · `LazyImage` · `LiveChat` · `Loading` · `Modal` · `Notification` ·
`Performance` · `Retargeting` · `SEO` · `Layout`

## Verificación

```
npm run build   →  exit 0 · 0 sourcemaps · bundle de ~3,2 MB
npm run test    →  pruebas de componentes
npm run lint    →  sin errores
```

## Defectos corregidos en el escaparate público

Documentados porque explican el estado del repositorio:

| Defecto | Efecto | Corrección |
|---|---|---|
| `Sentry.withErrorBoundary` usado como componente | la app montaba **en blanco** | usar `Sentry.ErrorBoundary` |
| Router montado por debajo de los proveedores | `useLocation` sin contexto → pantalla de error | enrutador por encima |
| `generateSessionId` declarado después de usarse | zona muerta temporal → caída total | mover fuera del componente |
| `HotjarIntegration` sin props pero usando `hjid` | `ReferenceError` al montar | props opcionales con fallback a entorno |
| `measurementId` fuera de alcance | `ReferenceError` en analítica | declarar a nivel del hook |
| `sourcemap: true` en producción | publicaba ~2 MB de código original | desactivado |
| 19 imágenes pedidas a Pexels en caliente | sin red, sin imágenes | descargadas y locales |

## Límites conocidos

| Límite | Motivo |
|---|---|
| Sin backend ni envío de correo | el escaparate no debe depender de servicios |
| Chat en modo demostración | requiere servicio de mensajería |
| Analítica y píxel desactivados | sin claves reales; no se envían datos a terceros |
| Sin área de cliente | el proyecto no contempla cuentas |

## Qué demuestra al cliente

- Recorrido comercial completo: **entender → comparar → elegir modelo → cotizar**.
- Arquitectura con 18 dominios de componente reutilizables.
- Criterio de producción: nada se envía a terceros sin configuración explícita.
- Capacidad de rescatar un proyecto roto: aquí se corrigieron seis fallos que impedían renderizar.
