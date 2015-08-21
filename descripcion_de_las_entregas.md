# Descripción de las entregas

Para permitir una mejor distribución de las tareas y orientar al alumno en el proceso de desarrollo de su trabajo, se definieron una serie de puntos de control y fechas que el alumno podrá utilizar para comparar su grado de avance respecto del esperado. En cada una de estas entregas se otorgará feedback al grupo, para que sepan fehacientemente si su presentación cumple o no con el mínimo estipulado.

## Checkpoint 1 - Obligatorio

**Fecha:** 12 de septiembre

**Objetivos:**
- Familiarizarse con Linux y su consola, el entorno de desarrollo y el repositorio
- Aplicar las Commons Libraries, principalmente las funciones para listas, archivos de conf y logs
- Dar los primeros pasos en el Trabajo Práctico, creando la base de los procesos y su esquema de comunicación

**Requisitos mínimos:**
- Entorno instalado y funcionando; todos los integrantes deben haber subido commits a GitHub
- Tener los 4 procesos del sistema creados, conectándose entre sí
- Poder enviar el comando `RUN programa` al Planificador, y que este mensaje sea enviado a la CPU, luego de la CPU al Administrador de Memoria y luego del Administrador de Memoria al Administrador de Swap; debe ser impreso por pantalla

**Distribución recomendada:** Todos los miembros trabajando juntos para crear los procesos y poder subir el código a GitHub.

**Lectura recomendada:**
- http://faq.utn.so/arrancar
- [Beej Guide to Network Programming](http://beej.us/guide/bgnet/output/html/multipage/index.html)
- [Linux POSIX Threads](http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html)
- [SisOpUTNFRBA Commons Libraries](https://github.com/sisoputnfrba/so-commons-library)
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 3: Procesos
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 4: Hilos

## Checkpoint 2 - Obligatorio

**Fecha:** 3 de octubre

**Objetivos:**
- Construir incrementalmente un planificador de procesos básico
- Comunicar procesos correctamente
- Sincronizar correctamente la ejecución de sus procesos
- Modelar la primera versión de las estructuras necesarias para el desarrollo

**Requisitos mínimos:**
- El Planificador debe poder correr N procesos, eligiendolos mediante un algoritmo FIFO
- La CPU debe ser capaz de correr 1 hilo. Este hilo debe poder interpretar los comandos leer y finalizar. Debe poder comunicarse con el Administrador de Swap al iniciar y finalizar procesos. Debe solicitar las lecturas al Administrador de Memoria.
- El Administrador de Memoria debe ser capaz de recibir pedidos de lecturas, y delegarlos en el Administrador de Swap
- El Administrador de Swap debe ser capaz de recibir archivos de swap y guardarlos en su partición respectiva. También debe poder eliminar procesos. Ante un pedido de lectura, debe poder buscar en su partición, para devolver el contenido de página adecuado.

**Distribución recomendada:** 
1 persona para el Planificador, 1 persona para la CPU, 0.5 personas para el Administrador de Memoria, 1.5 personas para el Admistrador de Swap

**Lectura recomendada**:
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 5: Planificación de la CPU
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 6: Sincronización de Procesos


## Checkpoint 3 - Obligatorio y presencial

**Fecha:** 7 de noviembre - Laboratorio de Medrano

**Objetivos:**
- Construir un planificador de procesos de mayor complejidad, que sea capaz de soportar una variedad de algoritmos
- Crear procesos con múltiples hilos, correctamente sincronizados, soportando concurrencia
- Desarrollar un administrador de memoria sencillo, manejando correctamente el flujo que ocurre ante cada acceso a memoria
- Desarrollar una partición de file system de fácil manejo

**Requisitos mínimos:**
- El Planificador debe poder correr N procesos, eligiendolos mediante un algoritmo Round Robin o SJF sin desalojo. El algoritmo a ejecutar será configurable, y no cambiará mientras se ejecuta el proceso.
- La CPU debe ser capaz de correr N hilos. Estos hilo debe poder interpretar los comandos previamente creados y además de permitir la escritura de páginas
- El Administrador de Memoria debe ser capaz de recibir pedidos de lecturas y escrituras e interpretarlos correctamente, buscando en TLB, tabla de páginas o bien en swap, según corresponda. La TLB utilizará el algoritmo FIFO. Los proceso tendrán una asignación fija de marcos configurable, igual para todos. La sustitución será local. El algoritmo de reemplazo de marcos sera FIFO.
- El Administrador de Swap debe ser capaz de recibir pedidos de lectura y escritura.

**Distribución recomendada:**
1 persona para el Planificador, 1 persona para la CPU, 1.5 personas para el Administrador de Memoria, 0.5 personas para el Administrador de Swap

**Lectura recomendada:**
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 8: Memoria Principal
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 10: Interfaz del sistema de archivos

## Entrega Final

**Fecha:** 28 de noviembre

**Objetivos:**
- Implementar una mayor variedad de algoritmos de reemplazo de marcos
- Fomentar la investigación de los alumnos, acerca de diferentes métricas y criterios
- Finalizar el desarrollo del Trabajo Práctico
- Empaquetar el desarrollo para un fácil deployment
- Subir a GIT la última versión estable
- Validar los tests provistos por la cátedra
- Evaluar el Trabajo Práctico en el laboratorio
- Obtener conclusiones en base a la ejecución de diferentes lotes de procesos

**Requisitos mínimos:**
- El Planificador debe mostrar las siguientes métricas, cuando un proceso finaliza: tiempo de respuesta del proceso, tiempo de ejecución
- La CPU debe mostrar el % de utilización de CPU cada un minuto
- El Administrador de Memoria debe incluir los algoritmos de reemplazo de marcos LRU y Clock Modificado. Cuando finaliza un proceso, debe mostrar la cantidad de fallos de página vs la cantidad de páginas accedidas. Cada un minuto debe mostrar la tasa de aciertos de la TLB, incluyendo todos los valores generados desde que el Administrador entró en funcionamiento.
- El Administrador de Swap debe, cada vez que un proceso finalice, indicar la cantidad de páginas leídas y escritas por él. Además, debe ser capaz de compactar la partición.

**Distribución recomendada:**
1 persona para el Planificador, 0.5 personas para la CPU, 2 personas para el Admistrador de Memoria, 0.5 personas para el Administrador de Swap

**Lectura recomendada:**
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 9: Memoria Virtual

### Recuperatorios
- Primer recuperatorio: 12 de diciembre
- Segundo recuperatorio: 19 de diciembre

# Normas del Trabajo Práctico
El trabajo práctico se rige por las reglas detalladas en el documento [Normas del Trabajo Práctico](http://faq.utn.so/ntp).