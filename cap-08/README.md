<center> <h1>Capítulo 7: Vamos a dejar esto de lado</h1></center>

## Introducción
El capítulo 7 llamado "Vamos a dejar esto de lado" explora en detalle cómo funcionan las aplicaciones web sin conexión, desde la configuración del archivo de manifiesto hasta el manejo de eventos y las mejores prácticas para depuración. También incluye ejemplos prácticos para facilitar su implementación. Si alguna vez te has preguntado cómo crear aplicaciones que no dependan totalmente de la conexión en tiempo real, esta guía es el punto de partida ideal.

## Desarrollo

<h3 style="color:lightblue">0. ¿Qué es una aplicación web sin conexión?</h3>

Es una aplicación que utiliza un sistema de almacenamiento en caché para funcionar cuando no hay conexión a Internet. Esto se logra mediante un archivo de manifiesto que lista los recursos necesarios (HTML, CSS, JavaScript, imágenes, etc.) para la aplicación.

- Funcionamiento básico: Cuando estás en línea, el navegador descarga y almacena los recursos listados en el manifiesto. Si pierdes la conexión, el navegador utiliza los recursos almacenados localmente.

<h3 style="color:lightpink">1. El manifiesto de caché</h3>

El archivo de manifiesto define qué recursos se almacenarán para uso sin conexión.

#### Ejemplo básico de archivo de manifiesto:
```
CACHE MANIFEST
/clock.css
/clock.js
/clock-face.jpg
```
- Todos los recursos listados se almacenarán en la caché y estarán disponibles sin conexión.

#### Integración en el HTML:
```html
<!DOCTYPE HTML>
<html manifest="/cache.appcache">
<body>
    ...
</body>
</html>
```
#### Configuración del servidor (en Apache):
```
AddType text/cache-manifest .appcache
```

<h3 style="color:#f5e1ab">2. Secciones de la red y de respaldo</h3>

1. **CACHE**: Recursos que se almacenarán sin conexión.
```
CACHE:
/styles.css
/script.js
```

2. **NETWORK**: Recursos que nunca se almacenan en caché y requieren conexión.
```
NETWORK:
/api/data
```

3. **FALLBACK**: Recursos alternativos para mostrar cuando un recurso solicitado no está disponible.
```
FALLBACK:
/ /offline.html
```

#### Ejemplo completo:
```
CACHE MANIFEST
CACHE:
/styles.css
/script.js

NETWORK:
/live-updates

FALLBACK:
/ /offline.html
```

<h3 style="color:#b0f5ab">3. El flujo de los acontecimientos</h3>

El objeto `window.applicationCache` proporciona eventos para manejar el flujo de la aplicación.

#### Eventos importantes:

- `checking`: El navegador revisa el manifiesto.
- `downloading`: Comienza a descargar recursos.
- `progress`: Indica progreso en las descargas.
- `cached`: Todos los recursos se han almacenado correctamente.
- `error`: Ocurrió un error.

#### Ejemplo en JavaScript:
```javascript
window.applicationCache.addEventListener('cached', function() {
    console.log("Aplicación lista para usarse sin conexión");
});
```

<h3 style="color:#b0f5ab">4. El delicado arte de depurar errores, también conocido como “¡Mátenme! ¡Mátenme ahora!”</h3>

Si falla la descarga de un solo recurso, todo el proceso de almacenamiento en caché fallará.
Configura el servidor para evitar problemas con cachés HTTP:
plaintext
```
ExpiresActive On
ExpiresDefault "access"
```
