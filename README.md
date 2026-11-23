# EcoUrban — experiencia de presentación

Sitio estático interactivo para presentar la banca EcoUrban, su despiece animado por scroll y una secuencia visual de fabricación. La escena usa React, TypeScript, Three.js, React Three Fiber, Anime.js y Vite.

## Desarrollo local

```sh
npm ci
npm run dev
```

## Validación y build

```sh
npm run typecheck
GITHUB_PAGES=true npm run build
```

El workflow de GitHub Actions publica automáticamente en GitHub Pages al actualizar `main`. El sitio es una pieza de presentación pública; no incluye API, persistencia de datos ni formularios con información sensible.

## Alcance visual

La experiencia incluye el modelo 3D de la banca, vistas por capítulo, anotaciones informativas, animación reversible por scroll, una escena del proceso en diez etapas, alternativa sin WebGL y soporte para `prefers-reduced-motion`. Los detalles y la secuencia se presentan visualmente con base en los documentos y referencias del proyecto.

La escena de la banca es una visualización conceptual. La página no sustituye planos CAD, BOM, validación de ingeniería ni confirmación de fabricación.
