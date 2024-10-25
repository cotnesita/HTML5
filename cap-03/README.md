<center> <h1>Capítulo 3: ¿Qué significa todo esto?</h1></center>

## Introducción
El capítulo 3 llamado "¿Qué significa todo esto?" explica cómo HTML5 introdujo cambios iportantes para mejorar la estructura y el significado del código y cómo ahora ayuda a organizar mejor las páginas web para que sean más fáciles de entender, tanto para las personas como para las computadoras (por ejemplo, los motores de búsqueda o lectores de pantalla). HTML5 agrega nuevas etiquetas para estructurar mejor el contenido, haciendo que el código sea más claro y eficiente. Además, hace que las páginas web sean más accesibles para personas con discapacidades y permite que los navegadores interpreten la información correctamente.

## Desarrollo

<h3 style="color:lightblue">1. Doctype</h3>
El Doctype es la primera línea de un documento HTML y sirve para indicar al navegador cómo interpretar la página. Antes de HTML5, había diversas versiones del Doctype, lo que causaba que navegadores antiguos como Internet Explorer interpretaran las páginas de manera inconsistente tales como: modo peculiaridades, modo estándar y modo casi estándar.

HTML5 simplificó el Doctype a solo:

`<!DOCTYPE html>`

<h3 style="color:lightpink">2. Elementos para la estructura del documento HTML</h3>
La estructura de un documento HTML es como un árbol jerárquico con un elemento raíz y nodos hijos:

#### a) Elemento raíz:
El elemento raíz siempre es `<html>`, pero en HTML5 se eliminan atributos innecesarios como `xmlns`.

`<html lang="es">`

Define el idioma de la página con el atributo `lang`.

#### b) Elemento `<head>`:
Contiene metadatos e instrucciones para el navegador. Un ejemplo:

`<head>` <br>
  `<meta charset="utf-8">` <br>
  `<title>Mi sitio web</title>` <br>
  `<link rel="stylesheet" href="estilos.css">` <br>
`</head>`

#### c) Elemento <body>:
Contiene el contenido visible de la página.

<h3 style="color:#f5e1ab">3. Codificación de caracteres</h3>
La codificación de caracteres se refiere a cómo los caracteres (como letras y símbolos) se almacenan y se procesan por los navegadores y sistemas. La codificación más recomendada y usada en la web es UTF-8, ya que soporta casi todos los caracteres de todos los idiomas.

- Problema que soluciona: Antes, si no se especificaba una codificación, algunos navegadores no podían interpretar correctamente ciertos *caracteres especiales o raros* (como ñ, á o caracteres de otros alfabetos).

- Cómo se declara ahora: la recomendación para HTML5 es usar siempre UTF-8.
  
Ejemplo: <br>
`<meta charset="utf-8">`

Este método es más sencillo que el anterior de HTML4, que era más largo y más propenso a errores:

- Método anterior:

`<meta http-equiv="Content-Type" content="text/html; charset=utf-8">`

- Importante: No definir la codificación puede provocar vulnerabilidades de seguridad y errores de visualización en navegadores más antiguos. Incluso si tu página no usa *"caracteres raros"*, siempre es buena práctica incluir la declaración de codificación para evitar problemas.

<h3 style="color:#b0f5ab">4. Amigos y relaciones (enlace)</h3>
El concepto de "amigos y relaciones" en HTML5 se refiere a cómo las etiquetas de enlace (`<link>` y `<a>`) pueden tener **atributos `rel` que definen la relación entre la página actual y el recurso vinculado**. Estas relaciones ayudan a navegadores, motores de búsqueda y otros programas a entender mejor el propósito de un enlace.

#### Tipos comunes de `rel` en `<link>`:
1. `rel="stylesheet"`: Define un archivo de CSS relacionado con la página actual. <br>
   `<link rel="stylesheet" href="estilos.css">`
2. `rel="alternate"`: Señala una versión alternativa del contenido, como un feed RSS o una versión PDF de la página. <br>
   `<link rel="alternate" type="application/rss+xml" href="feed.rss">`
3. `rel="icon"`: Especifica el icono que aparece en la pestaña del navegador (favicon). <br>
   `<link rel="icon" href="/favicon.ico">`
#### Tipos comunes de `rel` en `<a>`:
1. `rel="nofollow"`: Indica que el enlace no debe influir en el ranking de los motores de búsqueda. <br>
   `<a href="https://spam.com" rel="nofollow">Enlace spam</a>`
2. `rel="license"`: Apunta a la licencia bajo la cual se distribuye el contenido. <br>
   `<a href="licencia.html" rel="license">Licencia</a>`
3. `rel="author"`: Vincula a información del autor de la página. <br>
   `<a href="autor.html" rel="author">Sobre el autor</a>`
4. `rel="prev"` y `rel="next"`: Usados para paginación, indican enlaces a la página anterior o siguiente en una serie. <br>
   `<a href="pagina2.html" rel="next">Siguiente página</a>`
#### Relaciones especiales para motores de búsqueda:
`rel="nofollow"`: Es comúnmente usado para evitar que enlaces de terceros (como en comentarios) influyan en el SEO de la página.

`rel="canonical"`: Informa a los motores de búsqueda cuál es la versión principal o canónica de una página cuando hay varias versiones del mismo contenido.

#### Ejemplo completo de un <link> con varios `rel`:
`<head>` <br>
  `<link rel="stylesheet" href="estilos.css">` <br>
  `<link rel="alternate" type="application/rss+xml" href="feed.rss" title="RSS Feed">` <br>
  `<link rel="icon" href="favicon.ico" sizes="16x16">` <br>
`</head>`

<h3 style="color:#b0f5ab">5. Nuevos elementos semánticos en HTML5</h3>
HTML5 introduce elementos semánticos que hacen que el código sea más claro y fácil de mantener pues ayudan a definir la estructura y el propósito del contenido.

a) `<article>`: Se usa para contenido independiente como un post o noticia.

Ejemplo:

`<article>` <br>
  `<h1>Artículo principal</h1>` <br>
  `<p>Contenido del artículo...</p>` <br>
`</article>`

b) `<section>`: Agrupa contenido relacionado temáticamente. Útil para dividir una página en secciones.

Ejemplo:

`<section>` <br>
  `<h2>Sección de noticias</h2>` <br>
  `<p>Texto de la sección...</p>` <br>
`</section>`

c) `<header>` y `<footer>`: Se usan para encabezados y pies de página.

Ejemplo:

`<header>` <br>
  `<h1>Bienvenido a mi web</h1>` <br>
  `<nav>` <br>
    `<a href="#">Inicio</a> | <a href="#">Contacto</a>` <br>
  `</nav>` <br>
`</header>` <br>

`<footer>` <br>
  `<p>© 2024 Mi Web</p>` <br>
`</footer>`

d) `<nav>`: Define bloques de navegación:

Ejemplo:

`<nav>` <br>
  `<ul>` <br>
    `<li><a href="#">Inicio</a></li>` <br>
    `<li><a href="#">Servicios</a></li>` <br>
  `</ul>` <br>
`</nav>`

e) `<aside>`: Contiene contenido relacionado pero no central, como anuncios o enlaces.

Ejemplo:

`<aside>` <br>
  `<p>Publicidad aquí.</p>` <br>
`</aside>`

f) `<time>`: Marca fechas o horas.

Ejemplo (fecha y hora):

`<time datetime="2024-10-21T15:30:00">21 de octubre, 15:30</time>`

Ejemplo (publicaciones con `pubdate`:

`<article>` <br>
  `<header>` <br>
    `<time datetime="2024-10-21" pubdate>21 de octubre de 2024</time>` <br>
    `<h1>Título del artículo</h1>` <br>
  `</header>` <br>
`</article>`

g) `<mark>`: Representa una serie de texto en un documento marcado o resaltado para fines de referencia.
h) `<hgroup>`: Representa el encabezado de una sección. Se utiliza para agrupar un conjunto de elementos cuando el encabezado tiene varios niveles (subtítulos, títulos alternativos o eslóganes).

#### Estilización de Nuevos Elementos
HTML5 introduce muchos elementos de bloque, pero navegadores antiguos los tratan como *inline* (en línea).

Para asegurar un estilo correcto, usa CSS:

`article, section, nav, aside {` <br>
    `display: block;` <br>
`}`

Este bloque asegura que los elementos como `<article>` y `<section>` se comporten como contenedores.

<h3 style="color:#b0f5ab">6. Una larga digresión sobre cómo los navegadores manejan los elementos desconocidos</h3>

Este apartado explica cómo los diferentes navegadores, especialmente los antiguos como *Internet Explorer*, manejan los elementos HTML desconocidos, que son aquellos que no existían en versiones anteriores de HTML, como los nuevos elementos semánticos introducidos en HTML5 (`<article>`, `<section>`, `<nav>`, etc.).

#### Elementos desconocidos y su renderización

Cuando un navegador se encuentra con un elemento que no reconoce (es decir, no está en su lista de elementos HTML válidos), lo trata de manera diferente según el navegador.

- Problemas comunes:

**Estilo por defecto**: La mayoría de los navegadores renderizan elementos desconocidos como `inline`, es decir, como si fueran elementos en línea (como `<span>` o `<a>`), incluso si deberían ser de bloque como `<div>.`

**Compatibilidad DOM**: Algunos navegadores antiguos, como *Internet Explorer 8 y anteriores*, no procesan correctamente estos elementos en el **DOM (Document Object Model)**. Estos navegadores pueden insertar incorrectamente los elementos nuevos como nodos vacíos, ignorando su contenido y colapsando la jerarquía del DOM.

#### Ejemplo de Renderización Incorrecta en IE8
Supongamos que tenemos un código HTML con el nuevo elemento `<article>`.

`<article>` <br>
  `<h1>Bienvenido</h1>` <br>
  `<p>Este es un artículo de prueba.</p>` <br>
`</article>`

En Internet Explorer 8, en lugar de interpretar `<article>` como un contenedor de bloque, se renderizará como un elemento vacío sin hijos. Es decir:

`article (sin hijos)` <br>
`h1 (hermano de article)` <br>
`p (hermano de h1)`

#### Solución para Compatibilidad
Para solucionar este problema en navegadores antiguos como *IE8*, se puede usar un truco en JavaScript que crea estos elementos **antes** de que el navegador procese la página. Así, aunque el navegador no entienda nativamente esos elementos, los interpretará correctamente. Es decir:

```
<script>
  document.createElement("article");
  document.createElement("section");
</script>
```
Este código asegura que el navegador reconozca `<article>`, `<section>`, y otros elementos nuevos como elementos de bloque, permitiendo aplicarles estilos con CSS.

#### Problemas con el DOM
Otro problema de los navegadores antiguos es que, al no reconocer los elementos nuevos, crean un DOM incorrecto. Por ejemplo, en lugar de que los elementos `<h1>` y `<p>` sean "hijos" de `<article>`, los trata como "hermanos".

**DOM esperado:**

`article` <br>
  `|-- h1` <br>
  `|-- p`

**DOM en navegadores antiguos (como IE8 sin HTML5shiv):**

`article (vacío)` <br>
`h1 (hermano de article)` <br>
`p (hermano de h1)` <br>