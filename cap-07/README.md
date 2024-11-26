
<center> <h1>Capítulo 7: El pasado, el presente y el futuro del almacenamiento local para aplicaciones web</h1></center>

## Introducción
El capítulo 7 titutlado "El pasado, el presente y el futuro del almacenamiento local para aplicaciones web" explica que el almacenamiento local en HTML5 ha cambiado cómo las páginas web guardan información en el navegador del usuario, haciéndolo más fácil, rápido y práctico. Este documento explica su historia, desde los primeros intentos con cookies y otros trucos, hasta cómo funciona hoy con herramientas como localStorage y opciones más avanzadas. Además, incluye ejemplos claros que muestran cómo usar estas herramientas en proyectos web.

## Desarrollo

<h3 style="color:#facdcd">1. Breve historia de los trucos de almacenamiento local antes de HTML5</h3>

- **Problemas de las cookies**: Antes de HTML5, las cookies eran la solución estándar para almacenamiento local, pero tenían limitaciones:
  - Se transmiten en cada solicitud HTTP, ralentizando la aplicación.
  - Limitadas a 4 KB.
  - Inseguras a menos que se use SSL.
- **Primeros intentos**:
  - `userData` (Internet Explorer): Permitía almacenar hasta 64 KB por dominio usando XML.
  - Flash (Local Shared Objects): Permitía 100 KB de almacenamiento por dominio y requería permisos para cantidades mayores.
  - Gears (Google): Proporcionaba bases de datos SQL integradas basadas en SQLite con almacenamiento ilimitado tras un permiso inicial.

<h3 style="color:#deeb8a">2. Presentación del almacenamiento HTML5</h3>

El almacenamiento en HTML5 resuelve los problemas previos al proporcionar una API estandarizada y nativa para manejar datos de manera persistente en navegadores modernos.

#### Características principales
- **Estructura de pares clave-valor**:
  - Los datos se almacenan como cadenas.
  - Uso accesible mediante el objeto `localStorage`.
#### Compatibilidad
Todos los navegadores modernos lo soportan, incluidos Chrome, Firefox, Safari, Opera, Android e incluso Internet Explorer 8+.

#### Comprobando compatibilidad

```javascript
function supports_html5_storage() {
    try {
        return 'localStorage' in window && window['localStorage'] !== null;
    } catch (e) {
        return false;
    }
}
```

<h3 style="color:#b0f5ab">3. Uso del almacenamiento HTML5</h3>

#### Guardar y recuperar datos
```javascript
// Guardar un dato
localStorage.setItem('clave', 'valor');

// Recuperar un dato
let valor = localStorage.getItem('clave');

// Eliminar un dato
localStorage.removeItem('clave');

// Limpiar todo el almacenamiento
localStorage.clear();
```

#### Uso alternativo con sintaxis de corchetes
```javascript
localStorage['clave'] = 'valor';
let valor = localStorage['clave'];
```

<h3 style="color:#b3b9f5">4. Seguimiento de cambios en el área de almacenamiento HTML5</h3>

El evento `storage` permite monitorear modificaciones en el almacenamiento local:
```javascript
window.addEventListener("storage", (event) => {
    console.log(`Cambio en la clave: ${event.key}`);
    console.log(`Valor antiguo: ${event.oldValue}`);
    console.log(`Valor nuevo: ${event.newValue}`);
});
```

<h3 style="color:#db9e9e">5. Limitaciones de los navegadores actuales</h3>

- Capacidad limitada a 5 MB por dominio.
- Los datos se almacenan como cadenas, lo que puede requerir conversiones manuales al recuperar datos numéricos o booleanos.


<h3 style="color:#db9e9e">6. Almacenamiento HTML5 en acción</h3>
Esta sección muestra cómo usar el almacenamiento local de HTML5 en aplicaciones reales. Se ilustra con un ejemplo práctico de un juego llamado Halma, donde el estado del juego se guarda en el almacenamiento local para que los usuarios puedan continuar desde donde lo dejaron, incluso si cierran el navegador:

#### Guardando el estado del juego
Cada vez que ocurre un cambio en el juego, se guarda el estado con esta función:
```javascript
function saveGameState() {
    if (!supportsLocalStorage()) { return false; }

    localStorage["halma.game.in.progress"] = gGameInProgress;

    for (let i = 0; i < kNumPieces; i++) {
        localStorage["halma.piece." + i + ".row"] = gPieces[i].row;
        localStorage["halma.piece." + i + ".column"] = gPieces[i].column;
    }

    localStorage["halma.selectedpiece"] = gSelectedPieceIndex;
    localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;
    localStorage["halma.movecount"] = gMoveCount;

    return true;
}
```
- `gGameInProgress`: Booleano que indica si hay un juego en progreso.
- `gPieces`: Array que contiene la posición de cada pieza.
- Otros valores como el número de movimientos y el índice de la pieza seleccionada también se guardan.

#### Restaurando el estado del juego
Cuando el usuario vuelve al juego, se restaura el estado con la siguiente función:

```javascript
function resumeGame() {
    if (!supportsLocalStorage()) { return false; }

    gGameInProgress = (localStorage["halma.game.in.progress"] === "true");
    if (!gGameInProgress) { return false; }

    gPieces = new Array(kNumPieces);
    for (let i = 0; i < kNumPieces; i++) {
        let row = parseInt(localStorage["halma.piece." + i + ".row"]);
        let column = parseInt(localStorage["halma.piece." + i + ".column"]);
        gPieces[i] = new Cell(row, column);
    }

    gSelectedPieceIndex = parseInt(localStorage["halma.selectedpiece"]);
    gSelectedPieceHasMoved = (localStorage["halma.selectedpiecehasmoved"] === "true");
    gMoveCount = parseInt(localStorage["halma.movecount"]);

    drawBoard();
    return true;
}
```
#### Puntos importantes
- Los datos se almacenan como cadenas. Es necesario convertirlos manualmente al tipo de datos adecuado al recuperarlos:
  - **Booleanos**: Comparar explícitamente con `"true"`.
  - **Números**: Usar `parseInt()` o `parseFloat()`.

<h3 style="color:#db9e9e">7. Más allá de los pares clave-valor con nombre: visiones en competencia</h3>

1. **Web SQL Database**: Permite usar SQLite directamente desde JavaScript, aunque su estándar está descontinuado.
```javascript
let db = openDatabase('miDB', '1.0', 'Base de datos local', 2 * 1024 * 1024);
db.transaction((tx) => {
    tx.executeSql('CREATE TABLE IF NOT EXISTS items (id unique, text)');
    tx.executeSql('INSERT INTO items (id, text) VALUES (1, "Hola Mundo")');
});
```
2. **IndexedDB**: Más potente y flexible que `localStorage`, pero más complejo. Permite almacenar objetos completos y transacciones.
