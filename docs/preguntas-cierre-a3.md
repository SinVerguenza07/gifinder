# Preguntas de cierre - EC1 F2 A3

**Nombre: Jonathan Ariel Lagarda Durazo**
**Grupo: 001**

## 1. ¿Qué significa refactorizar una aplicación?

Mejorar la organización interna del código sin cambiar su funcionamiento.

## 2. ¿Por qué el proyecto se dividió en módulos?

Para separar responsabilidades y facilitar el mantenimiento y reutilización del código.

## 3. ¿Cuál es la responsabilidad de main.ts?

Inicializar la interfaz, coordinar los módulos y manejar los eventos principales.

## 4. ¿Qué diferencias existen entre una interfaz, un tipo unión y una enumeración?

La interfaz define la estructura de un objeto, el tipo unión limita valores posibles y la enumeración agrupa valores relacionados.

## 5. ¿Para qué se utiliza import type?

Para importar elementos que solo se necesitan durante la comprobación de tipos de TypeScript.

## 6. ¿Dónde se aplicaron la desestructuración, spread y rest?

En gallery.ts se usa desestructuración, en gif.service.ts spread y en gif-detail.ts rest.

## 7. ¿Por qué searchGifs recibe la colección como parámetro?

Para que pueda trabajar con diferentes colecciones sin depender de una específica.

## 8. ¿Por qué findGifById puede devolver undefined?

Porque el GIF buscado podría no existir en la colección.

## 9. ¿Qué función cumple data-gif-id?

Guarda el identificador del GIF seleccionado para poder localizarlo posteriormente.

## 10. ¿Qué es la delegación de eventos?

Es manejar eventos desde un elemento padre en lugar de agregar eventos individualmente a cada elemento hijo.

## 11. ¿Por qué el estado Loading podría no observarse?

Porque la búsqueda local es muy rápida y termina antes de que el navegador muestre visualmente ese estado.

## 12. ¿Qué dificultad se presentó durante la refactorización y cómo se resolvió?

Una dificultad fue organizar las funciones en diferentes módulos; se resolvió separándolas según su responsabilidad e importándolas desde main.ts.
