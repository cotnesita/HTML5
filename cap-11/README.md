<center> <h1>Capítulo 11: Manipulando la historia para divertirse y obtener ganancias mostrar tabla de contenidos</h1></center>

## Introducción
El capítulo 11 titutlado "Manipulando la historia para divertirse y obtener ganancias mostrar tabla de contenidos" aborda la **API de Historial de HTML5**, una herramienta que permite manipular el historial del navegador de manera más eficiente y dinámica. Este enfoque elimina la necesidad de recargar páginas enteras cuando se actualizan partes específicas, mejorando la experiencia del usuario en aplicaciones web modernas.

## Desarrollo

<h3 style="color:lightblue">0. ¿Qué es la API de Historial de HTML5?</h3>
La barra de direcciones y el botón Atrás del navegador son esenciales para navegar en la web. La API de Historial mejora estas funciones al permitir:

- Cambiar la URL sin recargar la página.
- Agregar entradas al historial del navegador.
- Escuchar eventos cuando el usuario navega hacia atrás o adelante.

<h3 style="color:#facdcd">1. El porqué</h3>

#### ¿Por qué manipular la ubicación del navegador?

- **URLs únicas**: Las URLs permiten identificar y compartir recursos. La API de historial asegura que estas sigan siendo útiles en aplicaciones dinámicas.
- **Optimización**: Cambiar la URL sin recargar ahorra tiempo y recursos, especialmente cuando las páginas comparten gran parte de su contenido.
- **Escenario práctico**: Si el 90% de dos páginas es similar, la API permite actualizar solo el 10% distinto, simulando una navegación sin refrescar la página completa.

#### Ejemplo básico:

- Carga solo el contenido nuevo con `XMLHttpRequest`.
- Actualiza el contenido visible con métodos como `innerHTML`.
- Cambia la URL en la barra de direcciones con `history.pushState`.

<h3 style="color:#deeb8a">2. El cómo</h3>

#### ¿Cómo funciona la API de historial?

Incluye métodos como `pushState`, `replaceState`, y eventos como `popstate`.

1. **`history.pushState(state, title, url)`**:
  - Cambia la URL en la barra de direcciones.
  - No recarga la página.
  - `state`: Datos asociados al estado de la URL.
  - `title`: Título de la página (poco utilizado actualmente).
  - `url`: Nueva dirección URL.

2. **Evento `popstate`**:
  - Se activa cuando el usuario navega hacia atrás o adelante en el historial.
  - Permite actualizar el contenido dinámicamente según la URL.

#### Ejemplo práctico: galería de fotos dinámica
Una galería que actualiza la foto y la URL sin recargar.

#### HTML inicial:
```html
<aside id="gallery">
  <p class="photonav">
    <a id="photonext" href="casey.html">Next &gt;</a>
    <a id="photoprev" href="adagio.html">&lt; Previous</a>
  </p>
  <figure id="photo">
    <img id="photoimg" src="gallery/1972-fer-500.jpg" alt="Fer" width="500" height="375">
    <figcaption>Fer, 1972</figcaption>
  </figure>
</aside>
```

#### JavaScript para manejar los clics:
```javascript
function setupHistoryClicks() {
  addClicker(document.getElementById("photonext"));
  addClicker(document.getElementById("photoprev"));
}

function addClicker(link) {
  link.addEventListener("click", function(e) {
    swapPhoto(link.href);
    history.pushState(null, null, link.href);
    e.preventDefault();
  }, false);
}

function swapPhoto(href) {
  var req = new XMLHttpRequest();
  req.open("GET", href, false);
  req.send(null);
  if (req.status == 200) {
    document.getElementById("gallery").innerHTML = req.responseText;
    setupHistoryClicks();
  }
}
```

1. Al hacer clic en un enlace, se carga el nuevo contenido con `XMLHttpRequest`.
2. Se reemplaza el contenido actual usando `innerHTML`.
3. Se actualiza la barra de direcciones con `pushState`.
4. Si el usuario navega hacia atrás, el evento `popstate` actualiza el contenido a la URL anterior.


#### Compatibilidad

La API es compatible con navegadores modernos como Chrome, Firefox, Safari, y Opera. Sin embargo, es importante que las aplicaciones funcionen correctamente en navegadores más antiguos o con JavaScript deshabilitado, implementando técnicas de mejora progresiva.
