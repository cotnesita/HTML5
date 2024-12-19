<center> <h1>Capítulo 10: “Distribuido”, “extensibilidad” y otras palabras elegantes</h1></center>

## Introducción
El capítulo 10 titutlado “'Distribuido', 'extensibilidad' y otras palabras elegantes" presenta los **microdatos**, una forma de añadir significado adicional a los datos visibles en una página web usando atributos específicos en HTML5. Se exploran varios subtemas, con ejemplos prácticos que ilustran cómo implementar microdatos en distintas situaciones.

## Desarrollo

<h3 style="color:#facdcd">1. ¿Qué son los microdatos?</h3>

Los **microdatos** son una forma de enriquecer el contenido de una página web usando vocabularios personalizados que permiten agregar información adicional para los motores de búsqueda y aplicaciones. Un vocabulario define propiedades que puedes agregar a tu HTML.

#### Características principales:

- **itemscope**: Marca el comienzo de un "objeto" en el vocabulario.
- **itemtype**: Define el vocabulario del objeto.
- **itemprop**: Especifica las propiedades del objeto.

#### Ejemplo básico:
```html
<section itemscope itemtype="http://data-vocabulary.org/Person">
  <h1 itemprop="name">Mark Pilgrim</h1>
  <p><img itemprop="photo" src="http://www.example.com/photo.jpg" alt="Foto"></p>
  <a itemprop="url" href="http://example.com">Mi blog</a>
</section>
```
Aquí se usan `itemscope` y `itemtype` para definir el alcance y vocabulario, y `itemprop` para las propiedades.

<h3 style="color:#deeb8a">2. El modelo de datos de microdatos</h3>

El modelo de datos de los microdatos se basa en pares nombre/valor. El valor puede provenir de distintos atributos o el contenido del elemento HTML.

#### Reglas clave para los valores de propiedad:

| Elemento HTML	| Valor extraído |
| --- | --- |
| `<meta>` |	Atributo `content` |
| `<img>` |	Atributo `src` |
| `<a>` |	Atributo `href` |
| Otros elementos | Contenido de texto del elemento|

#### Ejemplo con propiedades específicas:
```html
<section itemscope itemtype="http://data-vocabulary.org/Address">
  <span itemprop="street-address">100 Main Street</span><br>
  <span itemprop="locality">Anytown</span>,
  <span itemprop="region">PA</span>
</section>
```

<h3 style="color:#b0f5ab">3. Marcando personas</h3>

El vocabulario "**Person**" incluye propiedades como `name`, `photo`, `title` y `affiliation`.

#### Ejemplo de una página "Acerca de" con microdatos
```html
<section itemscope itemtype="http://data-vocabulary.org/Person">
  <img itemprop="photo" src="http://example.com/photo.jpg" alt="Foto de perfil">
  <h1 itemprop="name">John Doe</h1>
  <p>Role: <span itemprop="title">Desarrollador</span> en 
     <span itemprop="affiliation">Empresa XYZ</span></p>
  <p>Dirección:
    <span itemprop="address" itemscope itemtype="http://data-vocabulary.org/Address">
      <span itemprop="street-address">Calle 123</span>,
      <span itemprop="locality">Ciudad</span>
    </span>
  </p>
</section>
```

<h3 style="color:#b3b9f5">4. Marcando Organizaciones</h3>

El vocabulario "**Organization**" permite etiquetar información sobre empresas, como:

- `name`: Nombre de la organización.
- `url`: Página web.
- `address`: Dirección física.
- `tel`: Número de teléfono.

```html
<article itemscope itemtype="http://data-vocabulary.org/Organization">
  <h1 itemprop="name">Google, Inc.</h1>
  <p itemprop="address" itemscope itemtype="http://data-vocabulary.org/Address">
    <span itemprop="street-address">1600 Amphitheatre Parkway</span><br>
    <span itemprop="locality">Mountain View</span>,
    <span itemprop="region">CA</span>
  </p>
  <p itemprop="tel">650-253-0000</p>
  <a itemprop="url" href="http://www.google.com/">Google.com</a>
</article>
```

#### Nota
- Si la organización tiene varias ubicaciones, puedes agregar múltiples `address`.

<h3 style="color:#db9e9e">5. Marcar eventos</h3>

El vocabulario "**Event**" incluye:

- `summary`: Nombre del evento.
- `location`: Lugar.
- `startDate` y `endDate`: Fechas.
- `description`: Descripción.

#### Ejemplo:
```html
<article itemscope itemtype="http://data-vocabulary.org/Event">
  <h1 itemprop="summary">Google Developer Day</h1>
  <p><time itemprop="startDate" datetime="2024-07-01T08:00">1 de julio</time></p>
  <p>Ubicación:
    <span itemprop="location" itemscope itemtype="http://data-vocabulary.org/Address">
      <span itemprop="street-address">Calle 456</span>, 
      <span itemprop="locality">Ciudad A</span>
    </span>
  </p>
</article>
```

<h3 style="color:#db9e9e">6. Marcar reseñas</h3>

Los **microdatos** permiten que los motores de búsqueda, como Google, muestren **fragmentos enriquecidos** con información adicional, como nombres, direcciones o imágenes.

#### Ejemplo de resultado de búsqueda enriquecido:
```makefile
Nombre: Mark Pilgrim
Rol: Desarrollador
Empresa: Google, Inc.
Dirección: 100 Main Street, Anytown, PA

```
