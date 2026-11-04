# Design spec — landing «Los Visionarios Community»

## Objetivo y referencia

Recrear la sección principal de la landing que aparece en la captura proporcionada: una invitación a unirse a una comunidad que comparte entradas sobre oro (XAUUSD). La referencia es **mobile first** y muestra solo una parte de la página. Las medidas y colores siguientes son aproximaciones visuales, no valores extraídos del sitio original.

La barra de estado del teléfono y los controles del navegador de Instagram **no forman parte de la landing**. El contenido web empieza en el fondo oscuro debajo de esa barra.

**Actualización 2026-11-04:** se obtuvo también la pantalla desktop de Stitch (proyecto `11270664529725289685`, pantalla `5bbabe24c30e494bb79ba23a5d217690`). Su HTML y captura están en `stitch-reference/`. El export confirma Outfit para texto y titulares y Space Grotesk para etiquetas y cifras. La implementación local usa esos estilos como referencia, pero no publica las métricas, los testimonios ni la urgencia del export porque no se aportaron fuentes verificables.

## Composición

- Fondo negro casi puro, con halos dorados suaves alrededor del encabezado, el botón y las tarjetas.
- Una sola columna centrada. En móvil, contenido con `max-width: 640px` y `padding-inline: 24px`; bloques principales alineados al centro.
- Orden vertical: marca en cápsula → separador fino → titular → descripción → llamada de atención rosa → indicadores hacia abajo → CTA → contador → cupos → separador con punto luminoso → aviso de riesgo.
- Ritmo vertical amplio, especialmente entre descripción, llamada de atención y CTA. No aparece menú de navegación.

## Tokens visuales propuestos

| Uso | Valor aproximado |
| --- | --- |
| Fondo | `#050505` |
| Superficie dorada oscura | `#1A1609` |
| Texto principal | `#FAFAF8` |
| Texto secundario | `#E8E3DA` |
| Dorado principal | `#F8C94A` |
| Dorado claro | `#FFE08A` |
| Borde dorado translúcido | `rgba(248, 201, 74, .42)` |
| Rosa de énfasis | `#FF315D` |
| Aviso secundario | `#89847B` |

Usar una sans geométrica de peso alto para titulares y cifras (por ejemplo, **Montserrat**). La familia exacta no se puede determinar con certeza por la captura. Reservar los pesos `700–800` para el título y CTA, y `400–500` para el cuerpo. Si se carga una fuente externa, incluir fallback `Arial, sans-serif`.

## Componentes

### Identidad

Cápsula de ancho casi completo, borde dorado de 1 px, esquinas totalmente redondeadas, relleno oscuro y brillo dorado tenue. Contiene un isotipo circular dorado, `LOS VISIONARIOS` en mayúsculas y negrita, divisor vertical fino, y `Community` en peso regular. El isotipo debe ser un recurso propio; la captura no proporciona el archivo del logo. No reconstruirlo con una imagen borrosa recortada de la captura.

### Hero

Titular centrado, muy grueso, con interlineado compacto (`~1.05`) y tamaño adaptable (`clamp(2.3rem, 9vw, 4rem)`). Mantener este énfasis por fragmentos:

> ¿Te gustaría **copiar la próxima operación** que mandemos en **tiempo real?**

La primera y penúltima parte van en blanco; «copiar la próxima operación» va en dorado. «tiempo real?» lleva texto negro sobre una franja dorada irregular, tipo cinta. Implementar la franja con CSS/SVG decorativo y conservar el texto como HTML seleccionable. Permitir saltos de línea naturales según el ancho.

Debajo, texto centrado de aproximadamente `1.1–1.25rem`, interlineado `1.35`:

> Únete a **los visionarios** y recibe nuestras próximas entradas en el oro **(XAUUSD)** de lunes a viernes.

Los fragmentos en negrita usan dorado.

### CTA

«CLICK AL BOTÓN» aparece en mayúsculas, rosa intenso, peso alto y con resplandor rosa. Debajo hay cuatro indicadores hacia abajo, visualmente amarillos. Para accesibilidad, estos indicadores son decorativos y se ocultan a lectores de pantalla.

Botón principal de ancho completo, alto aproximado de `64–72px` en un viewport móvil de unos `375px` CSS, borde redondeado de `14–18px`, relleno de degradado dorado claro a amarillo, texto negro en negrita: `ÚNETE AHORA`. El icono de entrada a la izquierda y la flecha a la derecha son decorativos. Debe ser un enlace si lleva a otra página o aplicación, y un botón si abre un formulario dentro de la página. El destino aún debe definirse.

### Contador y cupos

Tres tarjetas iguales en fila, con borde dorado fino, fondo oscuro, esquinas de `14–18px` y halo discreto. Cada una muestra un valor grande dorado y una etiqueta blanca en mayúsculas con tracking: `HORAS`, `MINUTOS`, `SEGUNDOS`. La captura muestra `19:43:27`, solo como estado fotografiado; **no es un valor inicial fijo**.

Debajo: «Últimos **100** espacios disponibles», con `100` en dorado. Mostrar contador y cupos únicamente si existe una fecha límite y una disponibilidad reales y verificables. Si no existen, retirar ambos bloques sin reemplazarlos por una urgencia simulada. El contador debe tener un estado al vencer y no reiniciarse al recargar la página.

### Pie visible

Separador horizontal dorado muy tenue con un punto blanco luminoso en el centro. Debajo comienza un aviso de riesgo en gris, pequeño y centrado. La captura corta el texto: **no inventar ni completar el aviso a partir de la imagen**. Redactar y revisar el texto legal antes de publicar, junto con cualquier afirmación de rendimiento o de «copiar operaciones».

## Responsive y comportamiento

- Diseñar primero a `360–390px` CSS. La imagen adjunta mide `738 × 1600px`, pero parece una captura de teléfono con escalado; no usar esos píxeles como ancho CSS.
- En `320px`, reducir el título, los espacios y el tracking de las etiquetas para evitar desbordamiento; mantener las tres tarjetas si siguen siendo legibles.
- En tablet/desktop, limitar el hero a `640–720px`, mantener los elementos centrados y evitar que el titular se extienda a una línea demasiado larga. El CTA puede tener `max-width: 560px`.
- Usar HTML semántico (`main`, `h1`, `p`, enlace/botón). Conservar foco visible y contraste suficiente. Los brillos no deben ser la única forma de comunicar una acción.
- El contador, si se implementa, debe actualizarse sin anunciar cada segundo a lectores de pantalla; ofrecer una descripción estática comprensible.
- Respetar `prefers-reduced-motion` si se añaden pulsos o animaciones.

## Recursos y decisiones pendientes

- Logo original o isotipo autorizado.
- URL o acción exacta de «ÚNETE AHORA».
- Fecha límite y fuente de cupos, si se mostrarán.
- Texto legal completo y revisión de las afirmaciones sobre señales/operaciones financieras.

## Criterios de revisión

1. En móvil, el orden, jerarquía, colores y proporciones se reconocen frente a la referencia sin copiar la interfaz de Instagram.
2. No hay desbordamiento horizontal a `320px`, `375px` y `768px`.
3. El CTA funciona con teclado y tiene un destino real.
4. El contador y los cupos reflejan datos reales o no aparecen.
5. El aviso de riesgo está completo antes de publicar.
