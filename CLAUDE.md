# Sitio de Ashiō

Sitio estático de ashio.mx. Sin framework, sin build, sin dependencias.
HTML y CSS escritos a mano.

## Cómo se publica

El repo es `brandonchipotle/Ashio.mx`. Hostinger sirve el dominio desde
este repo, pero **no jala los commits de forma automática**: después de
cada push hay que entrar al panel de Git en Hostinger y desplegar a mano.
Mientras eso no ocurra, ashio.mx sigue mostrando la versión anterior.

Al revisar un cambio, descartar primero el caché: recarga forzada
(Cmd + Option + R en Safari).

## Estructura

```
index.html                         portada de "próximamente"
blog/index.html                    índice de artículos
blog/<slug>/index.html             un artículo por carpeta
assets/blog.css                    hoja compartida del blog
assets/logo-horizontal.svg         logotipo, versión horizontal
assets/logo-vertical.svg           logotipo, versión vertical
assets/favicon.svg                 símbolo solo
```

La portada tiene su CSS en línea. El blog usa `assets/blog.css`.

## Sistema visual

Viene de la hoja de estilo de marca de Ashiō. No inventar valores.

| Token | Valor | Uso |
|---|---|---|
| `--brand-black` | `#0d0d0d` | fondo |
| `--brand-bone` | `#f3efee` | texto |
| `--accent` | `#cf7457` | óxido, único acento |
| `--muted` | `#aaaaaa` | texto secundario |
| `--line` | `#282828` | filetes |

Tipografía: Hanken Grotesk, pesos 300 a 600.

Perillas de layout en `assets/blog.css`:

- `--col` ancho máximo del contenido. Hoy 75rem (1200px).
- `--medida` ancho del cuerpo de texto. Hoy 100%, llena el marco.
  Ponerlo en 46rem devuelve la medida de lectura corta.
- `padding` del `body` margen lateral. Hoy `clamp(1.25rem,4vw,4.5rem)`.

### Reglas del logotipo

Vienen del documento de marca y no se negocian:

- Solo negro o hueso. El logotipo nunca lleva el color de acento.
- El macrón siempre del mismo color que el resto.
- No deformar, rotar, ni separar el símbolo del nombre.
- Ancho mínimo 100px en pantalla.
- Se usa siempre desde el SVG original. Nunca se reescribe con la
  tipografía.

Pendiente del equipo: los SVG claros originales del logo horizontal y
del símbolo usan un blanco frío `#eff8f8` en lugar del hueso oficial.
Las copias de este repo usan `currentColor`, así que toman el hueso
correcto.

## Convenciones de código

- **Texto, no imágenes.** Los diagramas se construyen con HTML y CSS
  para que el texto se seleccione, se busque, se traduzca y escale.
- **Degradación.** Sin CSS, un diagrama debe seguir leyéndose como
  lista ordenada y una tesis destacada como cita.
- **Reglas acotadas.** Escribir selectores con alcance explícito
  (`article > ol > li`, no `ol li`). Una regla genérica se filtra en
  cuanto se agrega una figura que usa el mismo elemento.
- **Área táctil mínima** de 44px en cualquier cosa que se toque.
- Soportar `prefers-reduced-motion` y `prefers-contrast`.

## Convenciones de escritura

Tono de Ashiō: directo, afirmativo, frases cortas de cierre,
conversacional sin decoración. Regio en actitud, sin modismos.

- **Prohibido el guion largo.** Usar coma, dos puntos o punto.
- Sin lenguaje de gurú ni tono de agencia.
- Sin hedging ("casi siempre", "usualmente").
- Párrafos de tres a cinco oraciones. Los párrafos de una sola idea se
  leen como frases sueltas al ancho completo del blog.
- Nada de datos o estudios sin fuente verificable. Si no se puede
  anclar, se dice o no se publica.

## Decisiones tomadas

- **La portada se queda en "próximamente".** El blog entra como pestaña
  en la navegación, no como bloque suelto en la portada.
- **El frost es solo de la portada.** Las páginas del blog no llevan
  panel translúcido: encajonaba la lectura.
- **Esquinas a 18px en la portada.** La hoja de marca fija radio 0, así
  que ese redondeo es una excepción documentada, no un token nuevo.
- **Densidad visual.** El artículo de ventas por accidente lleva cuatro
  bloques destacados en 790 palabras. No es un patrón repetible por
  simetría: un artículo sin cuatro momentos de esa carga debe llevar
  menos. "¿Cómo le creyeron?" lleva tres en 2,813 palabras.
- **Componentes del blog.** Viven en `assets/blog.css` y se reusan entre
  artículos: `.ciclo` lista de intentos, `.clave` tesis destacada,
  `.comparacion` dos casos que se confunden, `.ruta` pasos encadenados,
  `.pilares` tres elementos sobre una base, `.fuentes` referencias al
  pie. Antes de inventar uno nuevo, revisar si alguno de estos sirve.
- **Fuentes al pie.** Un artículo con datos verificables cierra con una
  sección de Fuentes. No se citan dentro del cuerpo para no romper la
  lectura.

## Pendientes

- Activar despliegue automático en Hostinger si el panel lo permite.
- Definir qué elemento visual lleva cada artículo antes de escribirlo.
- Revisar si el blog adopta la medida de lectura corta o se queda a
  todo lo ancho.
