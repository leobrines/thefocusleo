# Sistema Personal — PWA

App instalable en tu celular, construida en torno a **un solo concepto**: la **intención de implementación** (Gollwitzer) — planes con la forma *"cuando surja la señal X, haré la conducta Y"*. No es una app de productividad ni una agenda por reloj: busca que **arranques lo que te cuesta iniciar**, **protejas el foco** y que lo que hagas **tenga sentido**. Pensada para cuando cuesta sostener la atención (TDA/TDAH). Tiene **dos modos con diseños distintos, switcheables** desde el header:

- **Construir** (fundación, para quien arranca de cero): un **asistente por pasos** calmado, sin presión de tiempo, para generar primero el **sentido** y el **plan** — Visión → Áreas (tus porqués = intenciones de meta) → Primer plan si-entonces. Es la base sobre la que actuar tiene sentido. Los usuarios nuevos arrancan aquí.
- **Actuar** (ejecución del día a día): arquitectura **de ejecución primero**, con tres modos en una **navegación inferior** (zona del pulgar):
  - **Ahora** (pantalla por defecto): reúne tus planes si-entonces de hoy y destaca **uno** en grande —"cuando [señal] → [conducta]"—. Sin agenda por reloj ni cuenta atrás: lo que dispara la acción es encontrar la señal. Botones **Empezar** (foco a pantalla completa, una cosa a la vez, **sin cronómetro**) y **Hecho** (marca el plan cumplido, se puede deshacer).
  - **Plan**: un solo lugar para decidir, con secciones colapsables — tus planes si-entonces (agrupados por día, más un grupo "cualquier día · por señal"; dos tipos: **para empezar** algo difícil de iniciar y **para cortar un hábito** no deseado), tu porqué (documento de sentido) y la bandeja de ideas capturadas.
  - **Avance**: una tira visual de tus últimos 7 días (lo que ya hiciste, sin rachas ni culpa) más la revisión semanal.

Un **botón flotante "+"** captura ideas desde cualquier pantalla (a un toque, para no perder el foco), y el botón **"¿Perdido?"** abre el ancla que, ante la distracción, recuerda ignorarla y volver al plan (no esforzarse más) — la intención de implementación "fría" del capítulo sobre proteger la meta en curso. Funciona offline y guarda tus datos en el dispositivo (localStorage).

El arco de la app es el del propio concepto (intención de meta → plan si-entonces para empezar → proteger la meta: ignorar distracciones y cortar hábitos), y cada pieza está respaldada por evidencia; los estudios están enlazados dentro de la app, en **Menú → Acerca**.

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
