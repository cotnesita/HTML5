<center> <h1>Capítulo 4: Llamémoslo superficie de dibujo</h1></center>

## Introducción
El capítulo 4 llamado "Llamémoslo superficie de dibujo" describe en profundidad el uso del elemento `<canvas>` en HTML5, que funciona como un "lienzo" para gráficos, imágenes y otros elementos visuales generados a través de JavaScript. Este lienzo permite crear y manipular gráficos de forma dinámica, ideal para juegos, diagramas y visualizaciones interactivas. Canvas, en esencia, es una superficie de dibujo en la que los desarrolladores pueden plasmar gráficos y modificar la presentación del contenido visual en tiempo real.

## Desarrollo

<h3 style="color:lightblue">0. Canvas</h3>

`<canva>` crea un área rectangular donde se puede dibujar utilizando JavaScript. No tiene contenido visible hasta que se le agregan gráficos.

**Ejemplo básico para definir un canvas:**
```html
<canvas id="miCanvas" width="300" height="225"></canvas>
```

JavaScript permite seleccionar el elemento y obtener el contexto de dibujo:

```javascript
var canvas = document.getElementById("miCanvas");
var contexto = canvas.getContext("2d");
```

<h3 style="color:lightpink">1. Formas simples</h3>

Para dibujar rectángulos, se usa `fillRect(x, y, width, height)` para dibujar rectángulos rellenos o `strokeRect(x, y, width, height)`  para solo trazar el borde.

**Un ejemplo básico sería:**

```javascript
var canvas = document.getElementById("myCanvas");
var context = canvas.getContext("2d");
context.fillRect(50, 25, 150, 100); // Dibuja un rectángulo relleno
```

<h3 style="color:#f5e1ab">2. Coordenadas del lienzo</h3>

El sistema de coordenadas inicia en la esquina superior izquierda `(0,0)`. A medida que los valores aumentan en X, se mueven hacia la derecha, y en Y, hacia abajo. Esto permite especificar la ubicación exacta de cada figura y personalizar su diseño según se necesite.

<h3 style="color:#b0f5ab">3. Caminos</h3>

Las líneas se crean usando `moveTo` (mover el "lápiz" sin dibujar) y `lineTo` (dibujar hasta el punto indicado). Estas trayectorias no se muestran hasta llamar a `stroke()`, lo que "entinta" el trazo.

**Por ejemplo:**

```javascript
contexto.beginPath();
contexto.moveTo(0, 0);
contexto.lineTo(300, 150);
contexto.stroke(); // Dibuja la línea
```

<h3 style="color:#b0f5ab">4. Texto</h3>

El elemento `<canvas>` también soporta texto, permitiendo agregar texto en distintas posiciones y con diferentes estilos, aunque sin el modelo de caja de CSS. Esto se logra ajustando propiedades como `font`, `textAlign`, y `textBaseline`. Se puede dibujar texto con `fillText` o `strokeText`.

**Ejemplo:**

```javascript
contexto.font = "20px Arial";
contexto.fillText("Hola, Canvas!", 50, 50);
```

<h3 style="color:#b0f5ab">5. Gradientes</h3>

Los gradientes permiten transiciones de color suaves. Se crean con `createLinearGradient` o `createRadialGradient`.

**Ejemplo:**

```javascript
var gradiente = contexto.createLinearGradient(0, 0, 300, 0);
gradiente.addColorStop(0, "black");
gradiente.addColorStop(1, "white");
contexto.fillStyle = gradiente;
contexto.fillRect(0, 0, 300, 150);
```

<h3 style="color:#dfceed">6. Imágenes</h3>

El método `drawImage()` permite insertar imágenes dentro del lienzo, pudiendo también escalarlas y recortarlas. Esto resulta útil para crear efectos visuales y trabajar con iconos o sprites en aplicaciones gráficas.  La imagen puede ser un elemento `<img>` o un objeto `Image`.

**Ejemplo:**

```javascript
<img id="miImagen" src="imagen.png" />
<canvas id="canvas" width="500" height="500"></canvas>
<script>
  var img = document.getElementById("miImagen");
  var canvas = document.getElementById("canvas");
  var contexto = canvas.getContext("2d");
  img.onload = function() {
    contexto.drawImage(img, 0, 0, 200, 100); // Dibuja imagen escalada
  };
</script>
```

<h3 style="color:#caff91">7. ¿Qué pasa con IE?</h3>


