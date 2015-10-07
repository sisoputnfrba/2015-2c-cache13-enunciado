# Proceso Administrador de Swap

Será el encargado de administrar la *memoria virtual* de “Cache 13”, utilizando un esquema muy sencillo. Para ello, al iniciarse, creará un archivo de tamaño <u>configurable</u> (en bytes), el cual representará nuestra _partición de swap_, y quedará a la espera de la conexión del **Administrador de Memoria**. El archivo de swap deberá ser rellenado con el caracter `\0`, a fines de inicializar la partición[^16]. El tamaño de las páginas escritas en swap es <u>configurable</u>[^17], así como también el nombre de este archivo.

Para que el manejo del espacio libre y ocupado en esta partición sea sencillo, se utilizará un esquema de asignación contigua. La *partición de swap* será considerada inicialmente como un hueco del total de su tamaño, medido en cantidad de páginas que puede alojar. Ante la llegada de un proceso “mProc”, asignará el tamaño necesario para que este sea guardado, dejando el espacio restante como libre. Esto mismo sucederá con los siguientes procesos “mProc” puestos en ejecución. Al finalizar un proceso “mProc”, el espacio que tenía asignado será marcado como libre. En caso de que esto genere dos huecos contiguos, estos se unirán formando un hueco mayor. Para administrar el espacio utilizado se usará una lista enlazada con el PID, el comienzo del proceso “mProc” en la partición, y la cantidad de páginas que ocupa. Para administrar el espacio libre, se utilizará una lista enlazada con el comienzo del hueco y la cantidad de páginas que representa. <u>La unidad mínima de asignación será una página</u>[^18].

Cuando le sea informada la creación de un nuevo proceso “mProc”, procederá a buscar un hueco donde quepa. En caso de que el espacio total disponible no sea suficiente, deberá rechazar el proceso, siendo su inicialización cancelada. En cambio, cuando la *fragmentación externa*[^19] sea la que no permite crear nuevos procesos, se deberá compactar la partición. Todos los pedidos que lleguen mientras dure este procedimiento deberán esperar a que este finalice. Este procedimiento deberá esperar una cantidad de tiempo <u>configurable</u> (en segundos), simulando el tiempo de compactación.

Ante un pedido de lectura de página realizado por el **Administrador de Memoria**, este módulo devolverá el contenido de esta página. Ante un pedido de escritura de página, sobreescribirá el contenido de esta página. Ambas operaciones tendrán un retardo configurable. Por último, cuando se le informe la finalización de un proceso, deberá borrarlo de la *partición de swap*.

## Archivo de Configuración

| Nombre de Campo        | Valor de Ejemplo |
|:----------------------:|:----------------:|
| `PUERTO_ESCUCHA`       | `6000`           |
| `NOMBRE_SWAP`          | `swap.data`      |
| `CANTIDAD_PAGINAS`     | `512`            |
| `TAMANIO_PAGINA`       | `256`            |
| `RETARDO_SWAP`         | `15`            |
| `RETARDO_COMPACTACION` | `60`[^20]        |

[^16] Se recomienda al alumno investigar sobre la utilización del comando `dd` para crear los archivos.
[^17]  Recuerde que el tamaño de las **páginas** es el mismo que el de los **marcos**.
[^18] Para más información sobre asignación contigua, remitirse al capítulo 11 de “Fundamentos de Sistemas Operativos” de Abraham Silberschatz.
[^19] Es muy importante no confundir la *fragmentación externa* con la falta de espacio disponible. En el primer caso el espacio está, pero no puede ser asignado por estar fragmentado.
[^20] En segundos.