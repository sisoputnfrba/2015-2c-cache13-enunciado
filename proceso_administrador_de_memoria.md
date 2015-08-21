# Proceso Administrador de Memoria

Será el encargado de administrar la memoria del sistema. Soportará *paginación por demanda*, utilizando una *TLB* y una partición de *swap*. Además limitará la cantidad de frames otorgados a cada proceso, siendo esto <u>configurable</u>.

Este proceso utilizará una estructura en memoria que emulará una cache TLB, con columnas para el identificador del proceso, la página y el marco, y su cantidad de entradas será <u>configurable</u>. Además manejará una *tabla de páginas* para cada proceso, con las columnas que sean necesarias para cada instancia del Trabajo Práctico. Por último, reservará una cantidad de *memoria principal para procesos* <u>configurable</u>, para ser dividida en marcos de tamaño <u>configurable</u>. A fines del trabajo práctico, ante cualquier acceso a la *tabla de páginas o a memoria principal*[^4], se deberá esperar una cantidad de tiempo <u>configurable</u> (en milisegundos), simulando el tiempo de búsqueda de la misma.

Ante un pedido de *página* de alguno de los procesadores, se realizará la traducción a *marco* (*frame*) y se devolverá el contenido correspondiente[^5]. En caso de que la página no se encuentre en *memoria principal*, será solicitada al proceso **Administrador de Swap**. A fines de simplificar el desarrollo, se asumirá que cualquier página solicitada por un proceso es válida.

Una vez que este proceso inicie, deberá siempre mostrar por pantalla una consola, que será capaz de soportar el comando `dump`. Cuando este comando se ejecute, se deberá escribir en el log del proceso el contenido de las tablas de páginas.

[^4] Si bien el Trabajo Práctico simplifica este aspecto, recuerde que las tablas de páginas se almacenan en Memoria Principal.
[^5] Recuerde los pasos del proceso de traducción: búsqueda en TLB, luego (de ser necesario) búsqueda en la tabla de páginas y por último búsqueda del frame correspondiente.