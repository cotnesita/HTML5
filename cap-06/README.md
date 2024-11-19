<center> <h1>Capítulo 6: Estás aquí (y todos los demás también)</h1>h1></center>

## Introducción
El capítulo 6 llamado "Estás aquí (y todos los demás tambián)" explica cómo usar la API de geolocalización en HTML5, que permite a las aplicaciones web saber dónde está el usuario, siempre y cuando este acepte compartir su ubicación. A través de ejemplos y pasos sencillos, se muestra cómo hacer que una página web detecte la ubicación, cómo manejar posibles errores y cómo hacer que funcione en dispositivos y navegadores más antiguos.

## Desarrollo

<h3 style="color:lightblue">0.¿Qué es la geolocalización?</h3>

La geolocalización es la capacidad de determinar dónde estás físicamente en el mundo y compartir esa ubicación con otros. Se basa en tecnologías como GPS, torres de telefonía móvil, conexiones Wi-Fi y direcciones IP.

<h3 style="color:lightpink">1. La API de Geolocalización</h3>

La API de geolocalización permite a las páginas web acceder a la ubicación física de los usuarios (latitud y longitud) mediante JavaScript. Se utiliza para mostrar mapas, encontrar negocios cercanos, entre otros.

<h3 style="color:#f5e1ab">2. Muéstrame el código</h3>

Para acceder a la ubicación, se utiliza la propiedad `navigator.geolocation`. 

#### Un ejemplo básico sería:

```javascript
function get_location() {
  navigator.geolocation.getCurrentPosition(show_map);
}
function show_map(position) {
  var latitude = position.coords.latitude;
  var longitude = position.coords.longitude;
  console.log(`Latitud: ${latitude}, Longitud: ${longitude}`);
}
```
Este código solicita la ubicación y la muestra en consola.

#### Si se quiere verificar si el navegador soporta la API se utiliza:

```javascript
if ('geolocation' in navigator) {
  console.log('Geolocalización soportada');
} else {
  console.log('No soportada');
}
```

<h3 style="color:#b0f5ab">3. Manejo de errores</h3>
Cuando algo falla al obtener la ubicación, puedes manejar errores con una función de devolución. 

#### Ejemplo:

```javascript
navigator.geolocation.getCurrentPosition(
  show_map,
  handle_error
);
```

<h3 style="color:#b0f5ab">4. ¡Opciones! ¡Exijo opciones!</h3>

Puedes configurar opciones adicionales con `PositionOptions`:

- **enableHighAccuracy**: mejora la precisión, pero puede ser más lento.
- **timeout**: tiempo máximo para esperar la ubicación.
- **maximumAge**: permite usar ubicaciones recientes almacenadas.

#### Ejermplo:

```javascript
navigator.geolocation.getCurrentPosition(
  show_map,
  handle_error,
  {
    enableHighAccuracy: true,
    timeout: 10000,
    maximumAge: 60000
  }
);
```

<h3 style="color:#b0f5ab">5. ¿Qué hay de IE?</h3>

Antes de IE9, no se soportaba la API de geolocalización. Google Gears era una solución alternativa para estos casos. Además, plataformas antiguas como BlackBerry o Nokia tenían sus propias APIs específicas.

<h3 style="color:#dfceed">6. Geo.js al Rescate</h3>

La librería `geo.js` simplifica el manejo de geolocalización, asegurando compatibilidad entre diferentes navegadores y dispositivos. 

#### Configuración básica:

```javascript
<script src="gears_init.js"></script>
<script src="geo.js"></script>
<script>
if (geo_position_js.init()) {
  geo_position_js.getCurrentPosition(
    function(p) {
      alert(`Latitud: ${p.coords.latitude}, Longitud: ${p.coords.longitude}`);
    },
    function() {
      alert('No se pudo obtener la ubicación');
    }
  );
}
</script>
```

<h3 style="color:#caff91">7. Un ejemplo completo y en vivo</h3>

El documento proporciona un ejemplo para mostrar un mapa con Google Maps.

#### Aquí una versión simplificada:

```javascript
function show_map(loc) {
  const lat = loc.coords.latitude;
  const lon = loc.coords.longitude;
  console.log(`Mapa en Latitud: ${lat}, Longitud: ${lon}`);
  // Aquí usarías una API de mapas como Google Maps para visualizar.
}
function show_map_error() {
  console.log('No se pudo determinar la ubicación.');
}
```
Este ejemplo utiliza la API para obtener la ubicación y mostrar un mapa interactivo.
