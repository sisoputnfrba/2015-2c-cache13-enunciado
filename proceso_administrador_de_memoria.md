# Proceso Administrador de Memoria

Será el encargado de administrar la memoria del sistema. Soportará *paginación por demanda*, utilizando una *TLB* y una partición de *swap*. Además limitará la cantidad de *marcos* otorgados a cada proceso, siendo esta cantidad <u>configurable</u>, con *asignación fija* y *reemplazo local[^9]*. La asignación de frames a un determinado proceso será efectiva sólo cuando este lo necesite, pudiendo nunca llegar al límite mencionado. Al iniciar, se conectará al **Administrador de Swap** y quedará a la espera de conexiones de hilos **CPU**.

El **Administrador de Memoria** utilizará una estructura en memoria que emulará una <u>única</u> cache *TLB*, con las columnas que sean necesarias para su buen funcionamiento. Su cantidad de entradas será <u>configurable</u>, y no variará durante la ejecución de este proceso. También se deberá poder deshabilitar el uso de esta cache, con una opción en el <u>archivo de configuración</u>.

Además, el **Administrador de Memoria** manejará una *tabla de páginas* para cada proceso, con las columnas que sean necesarias para cada instancia del Trabajo Práctico. Por último, reservará una cantidad de *memoria principal para procesos* <u>configurable</u>, para ser dividida en marcos de tamaño <u>configurable</u>. A fines prácticos, ante cualquier acceso a la *tabla de páginas o a memoria principal[^10]*, se deberá esperar una cantidad de tiempo <u>configurable</u> -en segundos, e igual para ambos tipos de acceso-, simulando el tiempo de acceso a memoria.

Cuando un **CPU** informe el inicio de un nuevo proceso “mProc”, deberá crear las estructuras necesarias para administrarlo correctamente. Además, deberá informar tal situación al **Administrador de Swap**, junto con la cantidad de páginas de datos a utilizar, para que este asigne el espacio necesario en su partición.

Ante un pedido de lectura de página de alguno de los procesadores, el **Administrador de Memoria** realizará la traducción a *marco (frame)* y se devolverá el contenido correspondiente[^11]. En caso de que la página no se encuentre en *memoria principal*, será solicitada al proceso **Administrador de Swap**, corriendo luego el algoritmo correspondiente para cargarla en *memoria principal*. A fines de simplificar el desarrollo, se asumirá que cualquier página solicitada por un proceso es válida.

Ante un pedido de escritura de página de alguno de los procesadores, se realizará la traducción a marco (frame), y se actualizará su contenido. Queda a criterio del grupo devolver o no el contenido, puesto que el proceso **CPU** ya lo conoce. En caso de que la página no se encuentre en *memoria principal*, será solicitada al proceso **Administrador de Swap**, corriendo luego el algoritmo correspondiente para cargarla en *memoria principal*. Es importante recordar que las escrituras a *Swap* se hacen <u>únicamente</u> cuando se reemplaza una página que fue modificada previamente. Si fuese necesario asignar un marco y no hubiese ninguno disponible, se finalizará el proceso “mProc”.

Cuando un **CPU** informe el fin de un nuevo proceso “mProc”, el **Administrador de Memoria** deberá eliminar las estructuras usadas para administrarlo. Además, deberá informar tal situación al **Administrador de Swap**, para que este libere el espacio utilizado en su partición.

Por último, el **Administrador de Memoria**, deberá ser capaz de recibir e interpretar tres *señales* diferentes[^12]. La primera de ellas deberá limpiar completamente la TLB (*TLB flush*), utilizando un hilo correctamente sincronizado para esto, evitando problemas de concurrencia. La segunda señal deberá limpiar completamente la *memoria principal*, actualizando los bits que sean necesarios en las tablas de páginas de los diferentes procesos. Para evitar problemas de concurrencia, aquí también se deberá utilizar un hilo correctamente sincronizado. Por último, la tercera señal deberá realizar un volcado (dump) del contenido de la *memoria principal*, en el archivo log de **Administrador de Memoria**, creando para tal fin un proceso nuevo[^13]. El volcado deberá indicar el número de *marco* y su contenido, utilizando una fila por cada *marco*.

<br/>
## Archivo de Configuración

| Nombre de Campo             | Valor de Ejemplo |
|:---------------------------:|:----------------:|
| `PUERTO_ESCUCHA`            | `5000`           |
| `IP_SWAP`                   | `192.168.101.12` |
| `PUERTO_SWAP`               | `6000`           |
| `MAXIMO_MARCOS_POR_PROCESO` | `3`              |
| `CANTIDAD_MARCOS`           | `128`            |
| `TAMANIO_MARCO`             | `256`            |
| `ENTRADAS_TLB`              | `4`              |
| `TLB_HABILITADA`            | `SI`             |
| `RETARDO_MEMORIA`           | `8`[^14]         |

[^9] Para más información, referirse al capítulo 9 de “Fundamentos de Sistemas Operativos”, de Abraham Silberschatz.
[^10] Si bien el Trabajo Práctico simplifica este aspecto, recuerde que las tablas de páginas se almacenan en Memoria Principal.
[^11] Recuerde los pasos del proceso de traducción: búsqueda en TLB, luego (de ser necesario) búsqueda en la tabla de páginas y por último búsqueda del frame correspondiente.
[^12] Se deberán usar las señales `SIGUSR1`, `SIGUSR2` y `SIGPOLL` para estos tres escenarios.
[^13] Recomendamos investigar el uso de `fork` y el concepto de “Copy on write”.
[^14] En segundos