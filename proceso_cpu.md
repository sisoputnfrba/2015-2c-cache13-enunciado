# Proceso CPU

Este proceso será el encargado de interpretar y ejecutar las instrucciones enviadas por el planificador. Dado que algunas instrucciones requerirán accesos a memoria, deberá comunicarse con el **Administrador de Memoria** a fin de realizarle diferentes pedidos. Para simular la presencia de múltiples CPUs, será necesario implementar *hilos[^5]*. La cantidad de hilos **CPU** será <u>configurable</u> y no variará durante la ejecución del sistema. Cada uno de los hilos **CPU** deberá tener un número que lo distinga (id), y este valor será utilizado para identificar todos los eventos que ocurrieron en esta **CPU**, en los logs de todos los procesos que lo necesiten.

Al iniciar, intentará conectarse al proceso **Planificador** y se quedará a la espera de solicitudes de ejecución de programas “mCod” por parte del mismo. También, intentará conectarse al proceso **Administrador de Memoria**, que es a quien solicitará las operaciones de lectura o escritura de memoria. En caso de que no pueda conectarse con alguno de ellos, la **CPU** finalizará su ejecución informando en el archivo de log del proceso.

Cuando el **Planificador** envíe el *contexto de ejecución* a alguna **CPU**, ésta pondrá en ejecución el proceso “mProc”. Para ello abrirá y leerá el archivo ejecutable completo cuya ruta relativa fue enviada, interpretando cada línea como una instrucción[^6].

Cada instrucción tendrá un valor de retorno, que será enviado al planificador al terminar la *ráfaga*. Las posibles instrucciones a implementar son:

- `iniciar`
- `leer`
- `escribir`
- `entrada-salida`
- `finalizar`

Luego de ejecutar cada instrucción, la **CPU** deberá esperar una cantidad de tiempo <u>configurable</u> (en segundos), simulando el tiempo de ejecución de la misma, antes de continuar con la siguiente instrucción. Tanto al ejecutar la instrucción “finalizar”, como al haber ejecutado el tiempo indicado por el **Planificador**, o bien al ejecutar una instrucción de entrada salida, la **CPU** devolverá el resultado de <u>todas</u> las instrucciones ejecutadas durante esa *ráfaga*. Hasta que esto ocurra, la **CPU** no enviará ninguna respuesta relacionada a este proceso.

Al ejecutar una instrucción que requiera acceso a memoria, se llamará al **Administrador de Memoria** para satisfacerla y la ejecución del proceso “mProc” deberá esperar la respuesta para continuar, aunque esta fuese prolongada. Para simplificar el trabajo práctico, no se contempla el reinicio de una instrucción ante un *fallo de página[^7]*.

Una vez enviada la información mencionada anteriormente al **Planificador**, volverá a quedar a la espera de solicitudes de ejecución.

## Archivo de Configuración

| Nombre de Campo       | Valor de Ejemplo |
|:---------------------:|:----------------:|
| `IP_PLANIFICADOR`     | `192.168.101.10` |
| `PUERTO_PLANIFICADOR` | `4000`           |
| `IP_MEMORIA`          | `192.168.101.11` |
| `PUERTO_MEMORIA`      | `5000`           |
| `CANTIDAD_HILOS`      | `4`              |
| `RETARDO`             | `2000`[^8]       |

[^5] _Hilo_ o _Thread_: traza de ejecución perteneciente a un proceso, susceptible de ser planificada por el sistema operativo. Para más información referirse a la clase teórica asociada.
[^6] En un Sistema Operativo real, la CPU utilizaría un puntero al código en memoria. A fines de simplificar el trabajo práctico, el proceso **CPU** podrá abrir y cerrar el archivo con el código, dejando en memoria únicamente la sección de datos.
[^7] En un Sistema Operativo real, un fallo de página devolvería una excepción que es tratada de forma especial, generando al menos una operación de entrada salida. Por dicho motivo, es habitual bloquear al proceso hasta que la página solicitada esté disponible, permitiendo que otro proceso utilice la CPU.
[^8] Especificado en milisegundos