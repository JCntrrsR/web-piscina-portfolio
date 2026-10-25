# Arquitectura

> Documento de vitrina: explica **cómo está construido** el sitio sin publicar el código.

## Decisión principal: proveedores ordenados por dependencia de la ruta

La aplicación acumula responsabilidades transversales —contexto de app, pruebas A/B, embudo de
conversión, CRM, notificaciones, rendimiento— y casi todas necesitan saber **en qué página está el
visitante**. Por eso el enrutador se monta por encima de ellas:

```
ErrorBoundary (Sentry)
└── Helmet (metadatos)
    └── Router                ← a partir de aquí los hooks de ruta funcionan
        └── Contexto de app
            └── A/B
                └── Embudo
                    └── CRM
                        └── Notificaciones
                            └── Rendimiento
                                └── Analítica · Chat · Consentimiento
                                    └── Layout → rutas
```

**Por qué se documenta esto:** en este tipo de árbol, mover un proveedor un nivel arriba del
enrutador no da error de compilación. Falla en ejecución, tumba toda la aplicación y deja una
pantalla de error genérica. Es el defecto más caro de detectar y el que más veces apareció en este
proyecto.

## Capas

| Capa | Responsabilidad | Ejemplo |
|---|---|---|
| **Presentación** | páginas y layout | inicio, servicios, nosotros, contacto |
| **Dominio** | componentes con lógica de negocio | catálogo, comparativa, formularios |
| **Transversal** | servicios que observan y miden | analítica, embudo, rendimiento, errores |
| **Adaptadores** | integraciones externas | correo, chat, píxel, cookies |

## Decisiones que sostienen el proyecto

**Configuración por entorno, con degradación explícita.**
Cada integración revisa si tiene clave antes de inicializarse. Sin identificador de analítica no se
envía nada; sin identificador de chat no se inyecta el script. El resultado es un escaparate que no
llama a servicios ajenos ni deja errores en consola.

**Los servicios se inicializan una sola vez.**
Las mediciones y el monitoreo arrancan al montar la aplicación, no en cada componente. Evita
observadores duplicados y envíos repetidos.

**Los componentes se agrupan por dominio, no por página.**
Una tarjeta de modelo, una tabla comparativa o un formulario de cotización se reutilizan en varias
vistas. Cambiar el diseño de la tarjeta cambia todas las apariciones a la vez.

**El fallo se contiene, no se propaga.**
Hay una frontera de error con reporte remoto y una pantalla de recuperación. Un módulo caído no
debe dejar al visitante mirando una página en blanco.

## Flujo de una cotización

```
landing → comparativa → catálogo de modelos
        → formulario de cotización (datos del terreno)
        → validación → confirmación en pantalla
        → clasificación del lead (interés alto / medio / bajo)
        → seguimiento por chat o correo
```

## Rendimiento y entrega

| Medida | Valor |
|---|---|
| Peso del build | ~3,2 MB |
| Fragmentos separados | vendor · router · formularios · analítica · monitoreo |
| Sourcemaps en producción | **desactivados** (publicaban el código original) |
| Estrategia PWA | cachea el shell y permite navegar sin conexión |

## Construcción

```
npm run build      →  compila TypeScript y agrupa con presupuesto de tamaño
npm run test       →  pruebas de componentes
npm run lighthouse →  auditoría de rendimiento y accesibilidad
```
