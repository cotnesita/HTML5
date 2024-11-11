<center> <h1>Capítulo 5: Video on the Web</h1></center>

## Introducción
El capítulo 5 titutlado "Video on the Web" plantea cómo HTML5 ha revolucionado la forma de incorporar videos en páginas web, explicando que antes de esta tecnología, el video en línea dependía en gran medida de complementos externos como Flash. HTML5 introdujo una solución estándar mediante la etiqueta `<video>`, permitiendo una integración más directa y optimizada para reproducir videos en navegadores sin necesidad de complementos.

## Desarrollo

<h3 style="color:lightblue">0. Elementos de Video en HTML5</h3>

Antes de HTML5, los videos requerían plugins de terceros como Flash. HTML5 introdujo el elemento `<video>`, que permite incorporar video directamente en una página web de forma estandarizada.

#### Ejemplo
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogv" type="video/ogg">
    <source src="video.webm" type="video/webm">
    Tu navegador no soporta el elemento de video.
</video>
```
Este código muestra un video en diferentes formatos (`mp4, ogv, webm`) para asegurar compatibilidad con varios navegadores.

<h3 style="color:#facdcd">1. Contenedores de video</h3>

Un contenedor de video define cómo se almacenan pistas de video y audio en un archivo. Los formatos populares incluyen:

- **MP4**: Basado en QuickTime de Apple, usado comúnmente para videos de alta calidad.

- **Ogg**: Un formato abierto compatible con Firefox y Chrome.

- **WebM**: Un formato optimizado para la web que utiliza el códec VP8 para video y Vorbis para audio.

<h3 style="color:#deeb8a">2. Códecs de vídeo</h3>
Los códecs son algoritmos que comprimen y descomprimen datos de video y audio. En HTML5, los navegadores soportan diferentes combinaciones de códecs:

- **H.264**: Usado en MP4, con alta calidad y compresión eficiente.

- **VP8 y VP9**: Usados en WebM, son libres de regalías y optimizados para web.

- **Theora**: Otro códec libre usado comúnmente con el contenedor Ogg.

<h3 style="color:#b0f5ab">3. Qué funciona en la Web</h3>
No existe una combinación única de formatos y códecs que funcione en todos los navegadores. Se recomienda codificar el video en varios formatos (MP4, WebM y Ogg) para una compatibilidad completa.

#### Ejemplo avanzado:
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <source src="video.ogv" type="video/ogg">
    Tu navegador no soporta este formato de video.
</video>
```

<h3 style="color:#b3b9f5">4. Codificación de vídeo con Miro Video Converter</h3>
Existen herramientas como Miro Video Converter y HandBrake para convertir videos a los formatos necesarios para HTML5. Se explica el uso de Miro para convertir videos en tres formatos compatibles: WebM, Ogg y MP4, donde cada conversión se guarda con un nombre específico para cada tipo de archivo.

<h3 style="color:#db9e9e">5. Problemas de licencia con el vídeo H.264</h3>
El códec H.264, ampliamente usado para videos en alta definición, está sujeto a licencias y tarifas por patentes. Aunque es compatible con muchos navegadores, su uso puede implicar costos de licencia para la distribución de contenido, a diferencia de códecs libres como VP8 y Theora. Para evitar estos costos, muchas personas prefieren los códecs de código abierto, especialmente si el video está destinado a ser reproducido en una amplia variedad de plataformas y dispositivos.
