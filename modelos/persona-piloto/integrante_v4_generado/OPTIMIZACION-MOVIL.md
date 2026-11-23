# Variante móvil del integrante v4

La aplicación selecciona `persona-articulada-integrante-v4-mobile.glb` en pantallas pequeñas o con entrada táctil. La versión original permanece como recurso para escritorio.

## Cambios

- Tamaño GLB: 70.85 MB → 14.51 MB (−79.5 %).
- Se conservan los 832,005 vértices, 4,500,000 índices, los 67 huesos Mixamo y sus pesos. El GLB no contiene clips de animación; la aplicación sigue aplicando las poses canónicas al rig. Los atributos geométricos se cuantizan y comprimen con `EXT_meshopt_compression`.
- La textura de color de 4096² px se reduce a 2048² px. Las texturas normal y metal-rough ya estaban en 2048² px.
- El cálculo estimado de memoria GPU de texturas pasa de ~134 MB a ~67 MB.
- En móvil los canvas usan DPR 1, desactivan sombras WebGL y antialiasing; el canvas del despiece se libera cuando termina su fundido.

## Regeneración

Desde la raíz del repositorio, con `@gltf-transform/cli` 4.5.1:

```sh
npx @gltf-transform/cli resize \
  modelos/persona-piloto/integrante_v4_generado/persona-articulada-integrante-v4.glb \
  /tmp/persona-v4-resized.glb --width 2048 --height 2048
npx @gltf-transform/cli meshopt \
  /tmp/persona-v4-resized.glb \
  modelos/persona-piloto/integrante_v4_generado/persona-articulada-integrante-v4-mobile.glb
```

Three.js `GLTFLoader` decodifica Meshopt mediante `MeshoptDecoder`; la aplicación configura el decoder en `src/escena/Persona.tsx`.

## Validación

El candidato se cargó en la escena web local con Chrome emulado a 390×844 y 320×640. La pose sentada, el rig y los materiales se ven en ambas resoluciones; el archivo GLB mide 14,509,444 bytes y el documento no presenta overflow horizontal a 320 px. No se midieron FPS ni se probó en un teléfono físico; las advertencias de tangentes y de jerarquía del GLB ya existían en el original.
