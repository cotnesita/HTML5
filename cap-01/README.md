<center> <h1>Capítulo 1: ¿Cómo llegamos aquí?</h1></center>

## Introducción
El capítulo 1 titutlado "¿Cómo llegamos aquí?" ofrece un resumen sobre cómo ha evolucionado HTML, señalando la importancia de los tipos MIME, la creación de estándares y el desarrollo de XHTML. También menciona la colaboración entre distintos grupos para crear HTML5. A través de esta historia, se muestra cómo HTML ha permanecido útil y relevante, adaptándose a las necesidades de los desarrolladores y usuarios a lo largo del tiempo.

## Desarrollo

<h3 style="color:lightblue">1.Tipos MIME</h3>
Cada vez que accedes a una página web, el navegador recibe instrucciones invisibles del servidor que le indican cómo mostrarla. Estas instrucciones se llaman "tipos MIME" y ayudan a que los archivos (imágenes, textos, videos) se vean correctamente. Estos tipos han evolucionado para mejorar la manera en que las páginas web son interpretadas por los navegadores.
Por ejemplo, cuando visitas una página web, el navegador recibe algo como:

`Content-Type: text/html`

Esto le dice al navegador que lo que sigue es una página HTML. Otros tipos MIME pueden ser para imágenes `(image/jpeg, image/png)`, JavaScript `(application/javascript)`, o CSS `(text/css)`. Sin estos tipos, el navegador no sabría cómo manejar los archivos.

<h3 style="color:#facdcd">2. Cómo se crean los estándares</h3>

Las funciones que usamos en HTML, como la etiqueta `<img>` para imágenes, no aparecieron de la nada. Fueron propuestas por desarrolladores pioneros y discutidas en correos y foros abiertos. A través de esta colaboración, se crearon muchas de las etiquetas que hoy usamos, adaptándose con el tiempo a las necesidades de los usuarios.

 `<IMG SRC="file://foobar.com/foo/bar/blargh.xbm">`

Este código fue propuesto en 1993 como una manera para que los navegadores descargaran y mostraran imágenes. No se requería un cierre, y permitía integrar imágenes en el texto, lo que resultó en el `<img>` que conocemos hoy

<h3 style="color:#deeb8a">3. Una línea ininterrumpida</h3>
HTML ha evolucionado con los años, pero ha mantenido su esencia desde los primeros días de la web. Aunque se ha intentado mejorar o reemplazarlo con otros lenguajes, sigue siendo el estándar para la construcción de sitios web gracias a su flexibilidad y capacidad de adaptarse. Las páginas creadas en 1990 aún funcionan en navegadores modernos. HTML ha tenido versiones como 2.0, 3.2 y 4.0, manteniendo siempre la compatibilidad, lo que permite que las páginas antiguas sigan viéndose bien sin ser reescritas.

`<a href="http://example.com">Visitar ejemplo</a>`

Este tipo de enlaces se ha mantenido a lo largo de las versiones de HTML.

<h3 style="color:#b0f5ab">4. Cronología del desarrollo de HTML desde 1997 hasta 2004</h3>
Después de la publicación de HTML 4.0 en 1997, el W3C decidió hacer la transición hacia XHTML. XHTML 1.0 y 1.1 surgieron en ese contexto, y los desarrolladores se enfrentaron a problemas de compatibilidad entre HTML y XML.

A diferencia de HTML, XHTML es mucho más estricto. En HTML puedes tener errores como olvidar cerrar una etiqueta, y el navegador lo mostrará sin problemas. Pero en XHTML, un error provocará que el navegador muestre un mensaje de error y no cargue la página. Muchas páginas que afirman ser XHTML en realidad siguen usando HTML, algo que puede verificarse observando el tipo MIME con el que se sirven.

XHTML fue diseñado para manejar los errores de manera más rigurosa. Sin embargo, esta "rigidez" no fue bien recibida por muchos desarrolladores, quienes continuaron usando la versión tradicional de HTML, más flexible y tolerante con los errores.

<h3 style="color:#b3b9f5">5. Todo lo que sabes sobre XHTML es erróneo</h3>
Como se mencionó anteriormente, a diferencia de HTML, donde los navegadores son indulgentes con los errores, XHTML requiere que los documentos sean "bien formados". Si hay un error, como olvidar cerrar una etiqueta, el navegador no mostrará la página. Un ejemplo de XHTML sería:

`<!DOCTYPE html>` <br>
`<html xmlns="http://www.w3.org/1999/xhtml">` <br>
`<head>` <br>
    `<title>Ejemplo de XHTML</title>` <br>
`</head>` <br>
`<body>` <br>
    `<h1>Hola, mundo!</h1>` <br>
`</body>` <br>
`</html>`

Si este documento se sirve con el tipo MIME `application/xhtml+xml`, un error en la estructura provocará que el navegador muestre un mensaje de error en lugar de intentar mostrar el contenido.

<h3 style="color:#db9e9e">6. Una visión competitiva</h3>
Una visión competidora: En 2004, hubo un debate sobre cómo debía evolucionar la web. Por un lado, el W3C (World Wide Web Consortium) proponía hacer una transición a XHTML, que era más estricto. Por otro lado, un grupo de desarrolladores, incluyendo Mozilla y Opera, propusieron mejorar HTML existente con nuevas características para las aplicaciones web sin romper la compatibilidad con versiones anteriores. Esto llevó a la creación de la WHATWG (Web Hypertext Applications Technology Working Group), un grupo que desarrolló lo que luego sería HTML5.

<h3 style="color:#f5e1ab">7. WHAT Working Group?</h3>
El WHATWG nació para desarrollar especificaciones que facilitaran la implementación de aplicaciones web interoperables. Se enfocaron en documentar cómo los navegadores manejan errores en HTML, con el objetivo de crear una base sólida para nuevas funciones. 

Por ejemplo, una especificación inicial llamada Web Forms 2.0 introdujo nuevos tipos de controles para formularios en HTML.

Otro ejemplo es: si el código tiene errores como etiquetas no cerradas, los navegadores simplemente lo corregirán y seguirán mostrando la página. WHATWG decidió escribir estas reglas para asegurarse de que todos los navegadores manejaran los errores de la misma manera.

<h3 style="color:#81d492">8. De vuelta al W3C</h3>
Después de varios años de trabajo paralelo entre el W3C y el WHAT Working Group, se unieron para evolucionar HTML y crear HTML5. Esta colaboración buscó realizar mejoras incrementales en HTML sin perder la compatibilidad con versiones anteriores. Así, las nuevas características se integraron en HTML5, lo que permitió a los desarrolladores seguir utilizando el contenido existente sin problemas.
