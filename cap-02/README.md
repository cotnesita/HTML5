<center><h1>Capítulo 2: Detectando catracterísticas HTML5</h1></center>

## Introducción
El capítulo 2 titutlado "Detectando características HTML5" explica cómo asegurarse de que las páginas web funcionen correctamente en diferentes navegadores, ya que no todos admiten las nuevas características de HTML5. Es decir, en lugar de preguntar si un navegador es "compatible con HTML5", lo ideal es revisar si soporta funciones específicas, como reproducción de videos, dibujo en canvas o almacenamiento local. El contenido se enfoca en varias funcionalidades que HTML5 presenta y cómo verificar si están disponibles en el navegador.

## Deasarrollo

<h3 style="color:lightblue">1. Técnicas de Detección de Características</h3>
El documento presenta cuatro técnicas básicas para detectar si un navegador admite una función en particular. Estas técnicas van desde la más simple a la más compleja:

#### Técnica 1: Verificar Propiedades Globales 
Consiste en comprobar si una propiedad existe en un objeto global, como window o navigator.
**Ejemplo para detectar la API de geolocalización:**
```
if ('geolocation' in navigator) {
  *// La geolocalización es compatible*
}
```
#### Técnica 2: Crear un Elemento y Verificar una Propiedad 
Se crea un elemento y se verifica si tiene una propiedad específica. Esto se utiliza, por ejemplo, para verificar la compatibilidad con la API de Canvas.
**Ejemplo para Canvas:**
```
function supports_canvas() {
  return !!document.createElement('canvas').getContext;
}
```
#### Técnica 3: Crear un Elemento, Llamar a un Método y Comprobar el Valor Devuelto 
Se utiliza para verificar formatos de vídeo soportados.
**Ejemplo para H.264:**
```
function supports_h264_baseline_video() {
  var v = document.createElement('video');
  return v.canPlayType('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
}
```
#### Técnica 4: Crear un Elemento, Establecer una Propiedad y Verificar si Conserva el Valor
Se utiliza para detectar nuevos tipos de <input>.
**Ejemplo para el tipo color:**
```
var i = document.createElement('input');
i.setAttribute('type', 'color');
return i.type !== 'text';
```
<h3 style="color:lightpink">2. Uso de Modernizr</h3>
Modernizr es una herramienta que permite verificar automáticamente si las funciones de HTML5 están disponibles. Esta biblioteca simplifica mucho el trabajo del desarrollador, ya que evita tener que escribir código manual para cada prueba.

**Ejemplo de uso de Modernizr para Canvas:**
```
if (Modernizr.canvas) {
  // El navegador soporta Canvas
} else {
  // El navegador no soporta Canvas
}
```
Modernizr crea un objeto global llamado `Modernizr` que contiene propiedades booleanas que indican si una función es compatible o no.

<h3 style="color:lightpink">3. Detección de Soporte de Video</h3>
Para detectar qué formatos de vídeo soporta un navegador, se usa la técnica 3 con el método canPlayType.

**Ejemplo para detectar soporte de Ogg Theora:**
```
function supports_ogg_theora_video() {
  var v = document.createElement('video');
  return v.canPlayType('video/ogg; codecs="theora, vorbis"');
  }
```
<h3 style="color:#abf5bf">4. Tipos de Input HTML5</h3>

HTML5 introduce nuevos tipos de `<input>` como `color`, `email`, `url`, entre otros. Para verificar la compatibilidad de estos nuevos tipos, se utiliza la técnica 4.

**Ejemplo para comprobar el soporte de** `<input type="date">`:
```
if (!Modernizr.inputtypes.date) {
  // El navegador no soporta nativamente <input type="date">
}
```
<h3 style="color:#aeabf5">5. Texto Placeholder</h3>

HTML5 permite definir texto de marcador de posición en los campos de formulario. Para detectar si un navegador admite esta funcionalidad, se verifica la existencia de la propiedad `placeholder` en un elemento `<input>`.

**Ejemplo para detectar soporte de** `placeholder`:
```
function supports_input_placeholder() {
  var i = document.createElement('input');
  return 'placeholder' in i;
}
