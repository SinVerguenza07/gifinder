Preguntas de cierre - EC1 F1 A1
1. ¿Qué función cumple Node.js en el entorno de desarrollo?
Node.js actúa como el entorno de ejecución (runtime) fuera del navegador. Aunque el producto final corre dentro del navegador web, Node.js es indispensable en la etapa de desarrollo para ejecutar herramientas de automatización, gestionar librerías mediante gestores de paquetes y servir como motor para la compilación y empaquetado del proyecto.

2. ¿Qué es PNPM y qué responsabilidad tiene?
PNPM es un gestor de paquetes de Node.js rápido y eficiente en el uso de espacio en disco. Su responsabilidad en el proyecto es descargar, instalar, actualizar y gestionar las dependencias (librerías externas) necesarias para el desarrollo, utilizando un almacén global con enlaces simbólicos (symlinks) para evitar duplicar archivos.

3. ¿Qué problema resuelve Vite durante el desarrollo?
Vite resuelve los tiempos de espera prolongados y la lentitud al recargar cambios. Aprovecha los módulos ES nativos del navegador (ESM) para ofrecer un servidor de desarrollo con arranque instantáneo y Hot Module Replacement (HMR), permitiendo que los cambios visuales y de lógica se reflejen en tiempo real sin reempaquetar todo el proyecto.

4. ¿Por qué se seleccionó la plantilla Vanilla con TypeScript?
Se seleccionó para construir una base ligera y sin la sobrecarga (overhead) de un framework pesado (como React o Angular), manteniendo el control total sobre la manipulación del DOM. El uso de TypeScript añade un sistema de tipado estático que ayuda a prevenir errores en tiempo de desarrollo, mejora el autocompletado y facilita la mantenibilidad del código.

5. ¿Cuál es la diferencia entre pnpm install, pnpm dev y pnpm build?
pnpm install: Lee el archivo package.json (y pnpm-lock.yaml) para descargar e instalar todas las dependencias necesarias en la carpeta node_modules.

pnpm dev: Inicia el servidor de desarrollo local de Vite para probar la aplicación en tiempo real mientras se programa.

pnpm build: Compila, transpila el código TypeScript a JavaScript puro y empaqueta la aplicación optimizada y minificada dentro de la carpeta dist, lista para producción.

6. ¿Qué información contiene package.json?
Contiene el manifiesto del proyecto: metadatos básicos (nombre, versión, descripción), scripts de ejecución (dev, build, etc.), la lista de dependencias del proyecto (dependencies y devDependencies), y configuraciones generales del entorno de desarrollo.

7. ¿Por qué debe conservarse pnpm-lock.yaml en el repositorio?
Garantiza la reproducibilidad del entorno. Guarda la estructura exacta del árbol de dependencias y las versiones específicas instaladas. Al mantenerlo en el repositorio, se asegura que cualquier desarrollador o servidor de despliegue instale exactamente las mismas versiones, evitando el problema de "funciona en mi máquina".

8. ¿Por qué node_modules no debe subirse a GitHub?
Porque es una carpeta sumamente pesada que contiene miles de archivos generados localmente. Subirla ralentizaría el repositorio y generaría conflictos entre distintos sistemas operativos. Como las dependencias se pueden reinstalar en cualquier momento con pnpm install leyendo package.json y pnpm-lock.yaml, resulta innecesario e ineficiente subirla.

9. ¿Cuál es la función de main.ts?
Es el archivo de entrada principal (entry point) de la aplicación TypeScript. Se encarga de inicializar la lógica global, importar los estilos principales, instanciar componentes y conectar la lógica con el elemento raíz HTML del DOM (generalmente #app).

10. ¿Qué ventaja ofrece separar el código en components, models, services, styles y utils?
Aporta una arquitectura limpia, modular y escalable.

components: Aísla la interfaz de usuario y la lógica de presentación.

models: Define las interfaces y tipos de datos (contratos TypeScript).

services: Maneja las peticiones HTTP y la comunicación con APIs externas (por ejemplo, Giphy).

styles: Mantiene centralizados los archivos CSS/Tailwind.

utils: Reutiliza funciones auxiliares o auxiliares puras.

Esta separación facilita el trabajo en equipo, la depuración y la reutilización de código.

11. ¿Qué diferencia existe entre el código fuente almacenado en src y los archivos generados en dist?
src: Contiene el código fuente legible para el desarrollador, escrito en TypeScript, modularizado y sin optimizar para producción.

dist: Contiene el resultado del proceso de build: código JavaScript transpilado, CSS minificado y archivos estáticos listos para ser servidos de manera óptima por cualquier servidor web de producción.

12. ¿Qué error o dificultad encontraste durante la configuración y cómo lo resolviste?

Un reto común fue la resolución de tipos en TypeScript al importar módulos locales y la configuración inicial de scripts en PNPM. Se resolvió ajustando la configuración del archivo tsconfig.json y verificando la compatibilidad de versiones de las dependencias.

13. ¿Cómo comprobaste que el repositorio puede ejecutarse en otro equipo?
Se realizó una prueba de clonado desde cero (git clone) en un directorio independiente / equipo distinto, verificando la ejecución exitosa de pnpm install seguido de pnpm dev para comprobar que el proyecto levantó sin dependencias faltantes ni errores de compilación.

14. ¿Qué aprendizaje de esta actividad será necesario para continuar desarrollando GIFinder?
Comprender el flujo completo de un proyecto frontend moderno: desde la gestión rigurosa de dependencias con PNPM y el tipado fuerte con TypeScript, hasta la estructura modular en services para consumir la API de Giphy y la optimización final con Vite. Esta estructura será la base para implementar la búsqueda, filtrado y despliegue de GIFs en las siguientes fases.