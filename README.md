# Sistema Personal — PWA

App instalable en tu celular, **diseñada pensando en cómo funciona la atención cuando cuesta sostenerla (TDA/TDAH)**. Cinco pestañas: **Hoy** (pantalla por defecto: solo los bloques de hoy, con lo que va *ahora* y lo que *sigue*, un botón **Empezar** que abre un temporizador de foco con cuenta atrás, y **Hecho** para marcar el bloque completado con feedback inmediato), **Sentido** (documento de sentido), **Semana** (bloques semanales, cada uno con una conducta concreta y un propósito activo al que sirve), **Ideas** (captura rápida) y **Revisión** (revisión semanal). Además, el botón **"¿Desenfocado?"** recuerda, ante la distracción, ignorarla y volver al bloque (no esforzarse más). Funciona offline y guarda tus datos en el dispositivo (localStorage).

Los principios detrás del diseño (tiempo visible contra la ceguera al tiempo, recompensa inmediata al completar, una cosa a la vez, y cero mecánicas de culpa o rachas) están respaldados por evidencia; los estudios están enlazados dentro de la app, en **Menú → Acerca**.

## Archivos
- `index.html` — la app completa (Tailwind con tema custom blanco/negro + jQuery, vía CDN, sin build)
- `manifest.webmanifest` — hace la app instalable
- `sw.js` — service worker (offline)
- `icon-192.png`, `icon-512.png` — íconos de la app

## Publicar en GitHub Pages (repo `leobrines/thefocusleo`)

Este repo ya incluye un workflow (`.github/workflows/deploy-pages.yml`) que despliega
la app automáticamente en GitHub Pages cada vez que se hace push a `main`.

> ⚠️ **GitHub Pages gratis requiere repo público.** Este repo es **privado** ahora
> mismo. Para publicarlo gratis hay que hacerlo **público** (o tener plan de pago
> GitHub Pro para Pages en repos privados). Si prefieres mantenerlo privado y gratis,
> usa Netlify o Vercel (más abajo).
>
> **No hace falta crear una organización:** funciona igual en tu cuenta personal.

Pasos una vez fusionado a `main`:

1. (Vía gratuita) **Settings → General → Danger Zone → Change visibility → Make public**.
2. **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. El workflow corre solo. En 1-2 minutos la app estará en:
   `https://leobrines.github.io/thefocusleo/`

Todas las rutas del proyecto son relativas (`./…`), así que funciona sin cambios bajo
esa subruta.

## Instalar en el celular

**Android (Chrome):** abre la URL → menú ⋮ → **"Instalar aplicación"** (o "Añadir a pantalla de inicio").

**iPhone (Safari):** abre la URL → botón Compartir → **"Añadir a pantalla de inicio"**.

Queda como app con su ícono, pantalla completa y funciona sin internet.

## Alternativa con repo privado (Netlify, gratis)

1. Crea el repo **privado** en GitHub y sube los archivos.
2. En [netlify.com](https://netlify.com) → Add new site → Import from GitHub → elige tu repo.
3. Sin configuración de build (es estático). Deploy. Te da una URL `*.netlify.app`.

## Importante sobre tus datos

- Los datos viven en el **localStorage del navegador/dispositivo** donde uses la app.
- No se sincronizan entre dispositivos (celular y PC tienen datos separados).
- Si borras los datos del navegador, se pierden. Haz respaldos ocasionales copiando tus textos importantes.

## Actualizar la app

Edita `index.html` (o pídeselo a Claude pegándole el archivo), luego:
```bash
git add . && git commit -m "cambio" && git push
```
GitHub Pages se actualiza solo en ~1 minuto. En el celular, cierra y abre la app (el service worker descarga la nueva versión).
