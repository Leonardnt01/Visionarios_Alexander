# Landing Los Visionarios

Vista previa estática de la landing basada en la pantalla de Stitch **«Los Visionarios - Landing Page Web Telegram»** (proyecto `11270664529725289685`, pantalla `5bbabe24c30e494bb79ba23a5d217690`).

## Ver en local

Desde esta carpeta:

```powershell
npm install
npm run dev
```

Abrir la URL local indicada por Astro (normalmente `http://127.0.0.1:4321/`). Para generar la versión publicable: `npm run build`; el resultado queda en `dist/`.

La página usa Astro con salida estática. La composición y los estilos proceden del HTML exportado por Stitch, que carga Tailwind desde CDN, además de Outfit y Space Grotesk desde Google Fonts. Para publicar con independencia de esos servicios externos, hay que integrar los estilos en el build.

## Estado

- `src/pages/index.astro`: pantalla completa de Stitch adaptada a Astro con cifras, operaciones y reseñas ficticias de prueba.
- `stitch-reference/original.html`: HTML original exportado por Stitch, conservado solo como referencia.
- `stitch-reference/screen.png`: captura original exportada por Stitch.
- `design.md`: especificación visual inicial basada en la primera captura móvil.

Los enlaces de Telegram están deshabilitados porque todavía no hay URL. El contador, los cupos, las métricas financieras, las operaciones y los testimonios son datos ficticios estáticos de prueba; se identifican como tales en la franja superior y el aviso legal. No deben publicarse como resultados reales. El recurso del logo del HTML original devolvió una página HTML en lugar de una imagen; por eso se usa un monograma CSS temporal.

## Antes de publicar

1. Sustituir el monograma por el logo autorizado.
2. Configurar el destino real de Telegram y habilitar el CTA.
3. Revisar el texto de riesgo y cualquier afirmación sobre resultados.
4. Si se desean contador, cupos, métricas o testimonios, aportar fuente verificable y definir cómo se actualizarán.
