<center> <h1>Capítulo 9: Una forma de locura</h1></center>

## Introducción
El capítulo 9 llamado "Una forma de locura" explora las novedades de HTML5 para formularios web, destacando su compatibilidad con navegadores y la implementación de varios tipos de entrada y características. Los formularios web han evolucionado significativamente gracias a las innovaciones de HTML5, que han hecho que sean más funcionales y accesibles para todo tipo de usuarios. Este estándar introduce herramientas que permiten crear campos más específicos, como aquellos para ingresar correos electrónicos, números o fechas, así como características que facilitan la personalización y mejoran la experiencia de uso.

## Desarrollo

<h3 style="color:lightblue">1.Texto de marcador de posición</h3>

HTML5 introduce el atributo `placeholder` para mostrar un texto temporal en los campos de entrada, el cual desaparece al enfocarlos.

#### Ejemplo
```html
<form>
  <input name="q" placeholder="Buscar en marcadores e historial">
  <input type="submit" value="Buscar">
</form>
```
- Es ignorado por navegadores que no lo soportan.
- No admite HTML ni imágenes dentro del placeholder.

<h3 style="color:lightpink">2. Campos de enfoque automático</h3>

El atributo `autofocus` permite enfocar automáticamente un campo de entrada al cargar la página.

#### Ejemplo básico:
```html
<form>
  <input name="q" autofocus>
  <input type="submit" value="Buscar">
</form>
```
**Ejemplo con respaldo**: Si el navegador no soporta `autofocus`, se puede usar JavaScript:

```javascript
<form>
  <input id="q" autofocus>
  <script>
    if (!("autofocus" in document.createElement("input"))) {
      document.getElementById("q").focus();
    }
  </script>
  <input type="submit" value="Enviar">
</form>
```

<h3 style="color:#f5e1ab">3. Nuevos Tipos de Entrada</h3>
(Direcciones de correo electrónico, Direcciones web, Números como casillas de verificación, Números como controles deslizantes, Selectores de fecha, Selectores de color)

1. Email (`type="email"`)

- Campo diseñado para direcciones de correo.
- Validación automática en navegadores modernos.

#### Ejemplo:
```html
<form>
  <input type="email" placeholder="tuemail@dominio.com">
  <input type="submit" value="Enviar">
</form>
```

2. URL (`type="url"`)

- Campo para direcciones web, optimizado en dispositivos como iPhone.

#### Ejemplo:
```html
<form>
  <input type="url" placeholder="https://www.ejemplo.com">
  <input type="submit" value="Ir">
</form>
```

3. Números (`type="number"`)

- Permite establecer valores mínimos, máximos y pasos.

#### Ejemplo:
```html
<input type="number" min="0" max="10" step="2" value="4">
```

4. Rango (`type="range"`)

- Control deslizante para seleccionar un valor.

#### Ejemplo:
```html
<input type="range" min="0" max="100" step="5" value="50">
```

5. Fecha (`type="date"`)

- Selector de fecha nativo, aunque su soporte aún es limitado.

#### Ejemplo:
```html
<input type="date">
```

5. Color (`type="color"`)

- Permite elegir un color mediante un selector.

#### Ejemplo:
```html
<input type="color" value="#ff0000">
```

<h3 style="color:#b0f5ab">4. Validación de formulario y Campos obligatorios</h3>

HTML5 simplifica la validación del lado del cliente con atributos como `required` (obligatorio).

#### Ejemplo:
```html
<form>
  <input type="email" required>
  <input type="submit" value="Suscribirse">
</form>
```

#### Desactivar validación:
```html
<form novalidate>
  <input type="email">
  <input type="submit" value="Enviar">
</form>
```
