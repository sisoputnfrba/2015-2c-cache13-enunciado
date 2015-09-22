# Descripción de las entregas

Para permitir una mejor distribución de las tareas y orientar al alumno en el proceso de desarrollo de su trabajo, se definieron una serie de puntos de control y fechas que el alumno podrá utilizar para comparar su grado de avance respecto del esperado. En cada una de estas entregas se otorgará feedback al grupo, para que sepan fehacientemente si su presentación cumple o no con el mínimo estipulado.

En cada checkpoint se explicita una serie de requisitos mínimos que debe tener cada entrega. Dado que la descripción de los componentes del TP enuncia generalidades, es importante que cada grupo esté atento a estos requisitos, que detallan algoritmos y funcionalidades a tener en cuenta, entre otras cosas..

## Checkpoint 1 - Obligatorio

**Fecha:** 12 de septiembre

**Objetivos:**
- Familiarizarse con Linux y su consola, el entorno de desarrollo y el repositorio
- Aplicar las Commons Libraries, principalmente las funciones para listas, archivos de conf y logs
- Dar los primeros pasos en el Trabajo Práctico, creando la base de los procesos y su esquema de comunicación

**Requisitos mínimos:**
- Entorno instalado y funcionando. <u>Todos los integrantes</u> deben haber subido commits a GitHub.
- Tener los 4 procesos del sistema creados, conectándose entre sí.
- Poder enviar el comando `correr programa` al **Planificador**, y que este mensaje sea enviado a la **CPU**, luego de la **CPU** al **Administrador de Memoria** y luego del **Administrador de Memoria** al **Administrador de Swap**. Será suficiente con que cada proceso imprima el mensaje recibido por pantalla.

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
- Construir incrementalmente un **Planificador** de procesos "mProc" básico
- Comunicar procesos del sistema correctamente
- Sincronizar correctamente la ejecución de los procesos del sistema
- Modelar la primera versión de las estructuras necesarias para el desarrollo
- Implementar la primera versión del **Administrador de Memoria** y del **Administrador de Swap**

**Requisitos mínimos:**
- El **Planificador** debe poder correr N procesos "mProc", eligiéndolos mediante un algoritmo FIFO
- La **CPU** debe ser capaz de correr 1 *hilo*. Este *hilo* debe poder interpretar los comandos iniciar, leer y finalizar. Debe poder comunicarse con el Administrador de Memoria tanto para iniciar y finalizar procesos "mProc" como para realizar las lecturas necesarias.
- El **Administrador de Memoria** debe ser capaz de recibir pedidos de lecturas, y directamente reenviarlos **Administrador de Swap**. También debe interpretar los pedidos para iniciar y finalizar procesos "mProc".
- El **Administrador de Swap** debe ser capaz de recibir nuevos procesos “mProc”. También debe poder eliminar estos procesos. Ante un pedido de lectura, debe poder buscar en su partición, para devolver el contenido de página adecuado.

**Distribución recomendada:** 
1 persona: **Planificador**. 1 persona: **CPU**. 0.5 persona: **Adm de Memoria**. 1.5 personas **Adm de Swap** 

**Lectura recomendada**:
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 5: Planificación de la CPU
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 6: Sincronización de Procesos


## Checkpoint 3 - Obligatorio - Laboratorio

**Fecha:** 7 de noviembre - Laboratorio Azul de Medrano (3er piso)

**Objetivos:**
- Construir un **Planificador** de procesos de mayor complejidad, que sea capaz de soportar una variedad de algoritmos.
- Crear procesos del sistema, con múltiples hilos, correctamente sincronizados para soportar concurrencia.
- Desarrollar un **Administrador de memoria** capaz de manejar correctamente el flujo que ocurre ante cada acceso a memoria.
- Desarrollar una partición de file system de fácil manejo.

**Requisitos mínimos:**
- El **Planificador** debe poder correr N procesos “mProc”, eligiendolos mediante un algoritmo Round Robin (con quantum <u>configurable</u>) o FIFO. El algoritmo a ejecutar será <u>configurable</u>, y no cambiará mientras se ejecuta el **Planificador**.
- La **CPU** debe ser capaz de correr como N hilos. Estos hilos deberán poder interpretar todos los comandos previamente creados, además de permitir la escritura de páginas y entrada-salidas.
- El **Administrador de Memoria** debe ser capaz de recibir pedidos de inicio, fin, lecturas y escrituras e interpretarlos correctamente, buscando en TLB, tabla de páginas o bien en swap, según corresponda. La TLB utilizará el algoritmo FIFO para sus reemplazos. Los procesos “mProc” tendrán una asignación a demanda de marcos con un máximo <u>configurable</u>, igual para todos. La sustitución será local. El algoritmo de reemplazo de marcos será FIFO. Por último, deberá implementar las tres señales previamente mencionadas.
- El **Administrador de Swap** debe ser capaz de recibir pedidos de inicio, fin, lecturas y escrituras.

**Distribución recomendada:**
1 persona: **Planificador**. 1 persona: **CPU**. 1.5 personas: **Adm de Memoria**. 0.5 persona **Adm de Swap**.

**Lectura recomendada:**
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 8: Memoria Principal
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 10: Interfaz del sistema de archivos

## Entrega Final

**Fecha:** 28 de noviembre

**Objetivos:**
- Implementar una mayor variedad de algoritmos de reemplazo de marcos.
- Fomentar la investigación de los alumnos, acerca de diferentes métricas y criterios.
- Investigar el uso de señales.
- Finalizar el desarrollo del Trabajo Práctico.
- Empaquetar el desarrollo para un fácil deployment.
- Subir y taggear en GIT la última versión estable.
- Validar los tests provistos por la cátedra.
- Evaluar el Trabajo Práctico en el laboratorio.
- Obtener conclusiones en base a la ejecución de diferentes lotes de procesos “mProc”.


**Requisitos mínimos:**
- El **Planificador** debe escribir en su log las siguientes métricas, cuando un proceso finaliza: tiempo de respuesta del proceso (desde el punto de vista del usuario), tiempo de ejecución, tiempo de espera.
- Cada **CPU** debe calcular y mostrar su porcentaje de uso.
- El **Administrador de Memoria** debe incluir los algoritmos de reemplazo de marcos FIFO, LRU y Clock Modificado. Cuando finaliza un proceso “mProc”, debe mostrar la cantidad de fallos de página vs la cantidad total de páginas accedidas para este. Cada un minuto debe mostrar la tasa de aciertos de la TLB histórica (es decir, incluyendo todos los valores generados desde que el **Administrador** entró en funcionamiento). 
- El **Administrador de Swap** debe, cada vez que un proceso “mProc” finalice, indicar la cantidad de páginas leídas y escritas por él. Además, debe ser capaz de compactar la partición cuando corresponda.

**Distribución recomendada:**
1 persona: **Planificador**. 0.5 persona: **CPU**. 2 personas: **Adm de Memoria**. 0.5 persona **Adm de Swap**

**Lectura recomendada:**
- Fundamentos de los Sistemas Operativos - Silberschatz, Galvin - Capítulo 9: Memoria Virtual

### Recuperatorios
- Primer recuperatorio: 5 de diciembre
- Segundo recuperatorio: 19 de diciembre

# Normas del Trabajo Práctico
El trabajo práctico se rige por las reglas detalladas en el documento [Normas del Trabajo Práctico](http://faq.utn.so/ntp).