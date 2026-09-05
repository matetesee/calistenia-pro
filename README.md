# Calistenia Pro — Quiz Funnel

Quiz funnel de venta para un programa de calistenia militar (nicho fitness), reconstruido a
partir del ángulo de mercado de [calisteniamilitar.site](https://calisteniamilitar.site) —
mismo flujo de 9 preguntas, mismo copy/oferta relevados del sitio original — pero como código
propio: sin sus bundles JS, sin sus pixels de tracking (Meta/TikTok/Utmify de su cuenta).

## Estructura
- `index.html` — el quiz completo (motor config-driven, 1 solo archivo, vanilla JS, sin frameworks).
- `server.js` — servidor estático minimalista (sin dependencias) para producción / Railway.
- `package.json` — script `start` que corre `server.js`.

## Correr en local

```bash
npm start
```

Abrí `http://localhost:3000`.

## Pendiente antes de vender de verdad
- **Checkout real:** el botón "INICIAR MISIÓN" apunta a `#` (placeholder). Conectá `STORE` y el
  `variantId` del plan en el bloque `CONFIG` de `index.html` (Shopify, Stripe, etc.) cuando
  tengas la tienda lista.
- **Meta Pixel:** todavía no conectado. Cuando tengas el Pixel ID, agregá el snippet estándar
  en el `<head>` de `index.html` (mismo patrón que `soonbody-tai-chi`) y seteá `META_PIXEL_ID` +
  `META_ACCESS_TOKEN` como variables de entorno en Railway para activar también el envío
  server-side (Conversions API) ya armado en `server.js`.
- **Imágenes:** `IMG.sale_hero` y `IMG.program`, y las fotos de las cards (edad), están vacías
  (se ve un placeholder). El sitio original usa fotos propias de su marca — para lanzar de
  verdad conseguí o generá fotos propias (no reusar las de calisteniamilitar.site) y pegá las
  URLs en el bloque `CONFIG`.
- **Precio:** el plan único ($7.90, antes $49.90) replica el del funnel analizado — ajustalo si
  cambia.

## Editar el quiz
Todo el contenido (marca, precio, pasos del quiz, testimonios, FAQ) vive en el bloque `CONFIG`
dentro de `index.html`. No hace falta tocar el resto del motor.

## Deploy en Railway
1. Entrá a [railway.app](https://railway.app) → **New Project** → **Deploy from GitHub repo**.
2. Elegí este repositorio.
3. Railway detecta Node automáticamente (via `package.json`) y corre `npm start`.
4. Cada push a `main` dispara un nuevo deploy automático.
