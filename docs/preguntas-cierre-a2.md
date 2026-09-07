# Preguntas de cierre - EC1 F1 A2

**Nombre: Jonathan Ariel Lagarda Durazo**
**Grupo: 001**

## 1. Modelo Gif

La interfaz `Gif` resuelve el problema de darle **forma y estructura fija** a los datos que representan un GIF dentro del proyecto. En lugar de trabajar con objetos "sueltos" cuyas propiedades podrían escribirse mal, omitirse o tener tipos incorrectos, `Gif` obliga a que cada objeto que se use como GIF tenga siempre las mismas propiedades (por ejemplo `id`, `title`, `url`, y opcionalmente `username`, `description`). Esto permite que TypeScript detecte errores en tiempo de compilación (como acceder a una propiedad que no existe, o pasar un `number` donde se espera un `string`) antes de que el código se ejecute, y además hace que el editor pueda ofrecer autocompletado.

## 2. Interfaz y objeto literal

Una **interfaz** es una declaración de tipo: define un contrato sobre qué propiedades debe tener un objeto y de qué tipo son, pero **no crea ningún valor en tiempo de ejecución** (no existe en el JavaScript compilado). Un **objeto literal**, en cambio, es un valor concreto: la instancia real de datos creada con llaves `{ }` que sí existe en memoria cuando el programa corre. La interfaz describe *cómo debe lucir* el objeto; el objeto literal *es* ese objeto. Se puede decir que la interfaz es el molde y el objeto literal es la pieza construida con ese molde.

## 3. Gif[] y el arreglo local

`Gif[]` significa "un arreglo cuyos elementos son todos de tipo `Gif`". Al declarar el arreglo local con ese tipo, TypeScript evita el error de **insertar elementos que no cumplan la estructura de `Gif`** (por ejemplo, un objeto al que le falte `title`, o que tenga `url` como número en vez de string). También evita errores al recorrer el arreglo, porque cada elemento que se extrae ya se sabe que tiene las propiedades de `Gif`, sin necesidad de verificarlo manualmente ni de usar `any`.

## 4. username y description como opcionales

`username` y `description` se declaran como propiedades opcionales (con `?`) porque **no todos los GIFs del arreglo necesariamente tienen esos datos disponibles**. Por ejemplo, un GIF podría no tener descripción, o podría no conocerse el usuario que lo subió. Marcarlas como opcionales permite crear objetos `Gif` válidos aunque esas propiedades falten, sin que TypeScript marque error por "propiedad faltante", reflejando así la realidad de los datos (más adelante, al conectar con la API de Giphy, algunos campos también pueden venir vacíos o ausentes).

## 5. Uso de let en lugar de const

Se usaría `let` en lugar de `const` en los casos donde una variable **necesita cambiar de valor después de su declaración inicial**. Por ejemplo: una variable que acumula o filtra resultados de búsqueda y se reasigna cada vez que el usuario escribe un nuevo término, un contador dentro de un bucle, o una variable booleana que indica si hubo coincidencias y se actualiza según el resultado del filtro. Si la variable solo se asigna una vez y nunca se reemplaza (como una referencia a un elemento del DOM o el arreglo original de GIFs), se usa `const`.

## 6. normalizeText, searchGifs y createGifCard

- **normalizeText**: recibe un `string` (por ejemplo el texto escrito por el usuario o el título de un GIF) y devuelve un `string` normalizado —generalmente en minúsculas y sin espacios extra o acentos— para poder comparar textos de forma uniforme sin importar cómo los haya escrito el usuario.
- **searchGifs**: recibe un término de búsqueda (`string`) y el arreglo de GIFs (`Gif[]`), y devuelve un nuevo arreglo (`Gif[]`) con los elementos cuyo `title` (u otra propiedad de texto) coincide con el término buscado, normalmente usando `filter` junto con `normalizeText`.
- **createGifCard**: recibe un objeto `Gif` y devuelve un `string` (HTML en forma de template string) o un elemento del DOM, que representa visualmente la tarjeta de ese GIF para poder insertarla en la página.

## 7. Diferencia entre forEach, filter, map y find

- **forEach**: recorre cada elemento del arreglo y ejecuta una función para cada uno, pero **no devuelve nada nuevo** (devuelve `undefined`); se usa para efectos secundarios, como imprimir o insertar elementos en el DOM.
- **filter**: recorre el arreglo y devuelve un **nuevo arreglo** solo con los elementos que cumplen una condición (la función callback devuelve `true`/`false`).
- **map**: recorre el arreglo y devuelve un **nuevo arreglo de la misma longitud**, transformando cada elemento según lo que retorne el callback.
- **find**: recorre el arreglo y devuelve el **primer elemento** que cumple una condición, o `undefined` si ninguno la cumple; a diferencia de `filter`, no devuelve un arreglo sino un solo elemento (o `undefined`).

## 8. find y undefined

`find` puede devolver `undefined` porque es posible que **ningún elemento del arreglo cumpla la condición** buscada (por ejemplo, buscar un GIF con un `id` que no existe). Ese resultado se controló validando explícitamente si el valor devuelto es `undefined` antes de usarlo (por ejemplo con un `if (gif)` o `if (gif !== undefined)`), mostrando un mensaje o comportamiento alternativo (como "no se encontraron resultados") en lugar de intentar acceder a propiedades de un valor inexistente, lo que provocaría un error en tiempo de ejecución.

## 9. Callbacks

Un **callback** es una función que se pasa como argumento a otra función, para que esta la ejecute en un momento determinado (por ejemplo, una vez por cada elemento de un arreglo, o cuando ocurre un evento). En la solución, dos ejemplos de callbacks son:
1. La función anónima o flecha que se pasa a `filter` dentro de `searchGifs`, que decide si cada GIF cumple la condición de búsqueda.
2. La función que se pasa como manejador del evento `submit` del formulario (`form.addEventListener('submit', callback)`), que se ejecuta cada vez que el usuario envía la búsqueda.

## 10. Ventaja de las template strings

Las template strings (delimitadas con comillas invertidas `` ` ``) permiten **insertar variables y expresiones directamente dentro del texto** usando `${...}`, sin necesidad de concatenar cadenas con `+`. Esto hace que construir el HTML de cada tarjeta de GIF sea mucho más legible y menos propenso a errores, además de permitir escribir el HTML en varias líneas de forma natural, respetando saltos de línea e indentación.

## 11. Destructuración y valor predeterminado de username

La destructuración se utilizó para **extraer directamente las propiedades necesarias de un objeto `Gif`** (por ejemplo `const { title, url, username } = gif;`) en lugar de acceder a cada una con `gif.title`, `gif.url`, etc., haciendo el código más corto y claro. El valor predeterminado para `username` (por ejemplo `const { username = "Anónimo" } = gif;`) se usó para **evitar mostrar `undefined` en la tarjeta** cuando esa propiedad opcional no viene definida, mostrando en su lugar un texto por defecto adecuado.

## 12. querySelector y validación de elementos

`querySelector` puede devolver `null` cuando **no encuentra ningún elemento en el DOM que coincida con el selector indicado**, por ejemplo si hay un error de tipeo en el id/clase, o si el elemento aún no existe en el momento en que se ejecuta el script. Para controlar esto, los elementos obtenidos se validaron comprobando que no fueran `null` antes de usarlos (con un `if` o el operador `!` cuando se tenía certeza de su existencia), evitando así errores como "no se puede leer una propiedad de null" al intentar manipular un elemento inexistente.

## 13. preventDefault en el formulario

`preventDefault()` evita el **comportamiento por defecto del navegador al enviar un formulario**, que normalmente recarga la página. Al llamarlo dentro del manejador del evento `submit`, se permite controlar manualmente qué ocurre con los datos ingresados (como capturar el texto de búsqueda y ejecutar `searchGifs`) sin que la página se refresque y se pierda el estado de la aplicación.

## 14. Búsqueda sin coincidencias

Cuando la búsqueda no encuentra coincidencias, la aplicación responde mostrando un **mensaje al usuario indicando que no se encontraron resultados** (en lugar de dejar el contenedor vacío sin explicación), evitando así una pantalla en blanco confusa y confirmando que la búsqueda sí se ejecutó correctamente.

## 15. Cambios al sustituir el arreglo local por la API de Giphy

Al reemplazar el arreglo local por datos reales de la API de Giphy, cambiaría lo siguiente:
- Los datos ya no estarían disponibles de inmediato en memoria, sino que habría que **esperar una respuesta asíncrona** (usando `fetch`, `async/await` o promesas).
- Sería necesario **manejar posibles errores de red** o respuestas fallidas (por ejemplo, sin conexión o límite de peticiones excedido).
- La estructura de los datos que devuelve la API podría no coincidir exactamente con la interfaz `Gif`, por lo que habría que **transformar o mapear la respuesta** de la API hacia el tipo `Gif` definido en el proyecto.
- La búsqueda podría delegarse directamente a los parámetros de la API en lugar de filtrar un arreglo local con `filter`.

## 16. Errores o dificultades encontradas
El error 'status' is possibly 'null' pasaba porque TypeScript no recuerda que ya validaste status en un if cuando lo usas después dentro de otra función (renderGifs). Cada función se analiza por separado.

La solución fue mover la validación dentro del tipo de retorno de una función
Como esta función declara que retorna T (no T | null), TypeScript confía en esa firma en cualquier lugar donde la uses — ya no depende de que "recuerde" un if anterior. El null queda descartado adentro de la función, antes de salir.