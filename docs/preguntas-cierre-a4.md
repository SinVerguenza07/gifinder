# Preguntas de cierre - EC1 F3 A4

## 1. ¿Qué diferencia existe entre una operación síncrona y una asíncrona?

R= Una operación síncrona se ejecuta de manera secuencial y espera a que termine una tarea antes de continuar. En cambio, una operación asíncrona permite realizar otras tareas mientras espera una respuesta, como sucede al consultar la API de Giphy en GIFinder.

## 2. ¿Cuáles son los estados de una promesa y qué relación tienen con async/await?

R= Una promesa tiene tres estados: pendiente (pending), cumplida (fulfilled) y rechazada (rejected). async/await permite trabajar con promesas de una manera más sencilla, esperando su resultado y manejando posibles errore

## 3. ¿Qué devuelve fetch y qué devuelve response.json()?

R= fetch devuelve una promesa que se resuelve en un objeto Response. Por otro lado, response.json() devuelve una promesa que convierte el contenido de la respuesta en datos JavaScript, normalmente un objeto o arreglo.

## 4. ¿Por qué es necesario comprobar response.ok?

R= Porque permite verificar si la respuesta HTTP fue exitosa. Si ocurre un error como un código 404 o 500, response.ok será false, lo que permite lanzar un error y evitar procesar una respuesta incorrecta.

## 5. ¿Cómo se utilizan try, catch y unknown para manejar errores en GIFinder?

R= try contiene el código que puede generar un error, mientras que catch permite capturarlo. El tipo unknown se utiliza para manejar errores de forma segura en TypeScript, comprobando el tipo del error antes de acceder a sus propiedades.

## 6. ¿Qué diferencia existe entre GiphyGif y Gif, y qué responsabilidad tiene mapGiphyGif?

R= GiphyGif representa la estructura de datos que devuelve la API de Giphy, mientras que Gif representa el formato utilizado dentro de la aplicación. mapGiphyGif se encarga de transformar los datos de Giphy al formato que necesita GIFinder.

## 7. ¿Por qué se utiliza URLSearchParams al construir la solicitud?

R= Se utiliza para construir los parámetros de la URL de manera segura y organizada. Permite agregar datos como la búsqueda, el límite de resultados y la clave de la API, codificando correctamente los valores.

## 8. ¿Qué significa Promise<Gif[]> en el tipo de retorno?

R= Significa que la función devuelve una promesa que, cuando se resuelve, contiene un arreglo de objetos de tipo Gif. Esto indica que los GIF se obtienen de manera asíncrona.

## 9. ¿Qué diferencia existe entre .env.local y .env.example, y por qué una variable VITE\_ no debe considerarse secreta?

R= .env.local contiene las variables de entorno utilizadas localmente, mientras que .env.example sirve como plantilla para indicar qué variables necesita el proyecto. Las variables que comienzan con VITE\_ se exponen al código del cliente durante la construcción, por lo que no deben contener información secreta, como contraseñas o claves privadas.

## 10. ¿Cómo comprobaste que .env.local no está versionado?

R= Lo comprobé revisando el archivo .gitignore para verificar que .env.local estuviera incluido. También se puede utilizar el comando git status para comprobar que el archivo no aparezca como un cambio pendiente de agregar al repositorio.

## 11. ¿Por qué Loading puede observarse con mayor claridad al consultar una API?

R= Porque la consulta a una API depende de la conexión y del tiempo de respuesta del servidor. Durante ese periodo, la aplicación muestra un estado de carga para informar al usuario que los datos todavía se están obteniendo.

## 12. ¿Qué dificultad se presentó durante la integración y cómo comprobaste que quedó resuelta?

R= Una dificultad fue integrar la consulta a la API de Giphy y transformar correctamente los datos recibidos para mostrarlos en la aplicación. Comprobé que quedó resuelta realizando búsquedas de GIF, verificando que los resultados se mostraran correctamente y revisando que los errores de la API fueran manejados adecuadamente.
