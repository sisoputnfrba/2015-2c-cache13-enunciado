# Proceso CPU

Este proceso será el encargado de interpretar y ejecutar las instrucciones enviadas por el planificador. Dado que algunas instrucciones requerirán accesos a memoria, deberá comunicarse con el **Administrador de Memoria** a fin de realizarle diferentes pedidos. Para emular la presencia de múltiples CPUs, será necesario implementar hilos. La cantidad de hilos CPU será <u>configurable</u>.

Cuando el **Planificador** envíe el *contexto de ejecución*, nuestra **CPU** pondrá en ejecución el proceso. Para ello abrirá y leerá el archivo ejecutable completo cuya ruta fue enviada, interpretando cada línea como una instrucción[^2]. Por otro lado, antes de comenzar a ejecutar, transferirá al **Administrador de Swap** el archivo de swap, para que sea cargado. 

Cada instrucción tendrá un valor de retorno, que será enviado al planificador al terminar la *ráfaga*. Las posibles instrucciones a implementar son:

- leer
- escribir
- entrada-salida
- finalizar

Luego de ejecutar cada instrucción, la **CPU** deberá esperar una cantidad de tiempo <u>configurable</u> (en milisegundos), simulando el tiempo de ejecución de la misma, antes de continuar la ejecución. Al ejecutar la instrucción “finalizar”, al haber ejecutado el tiempo indicado por el **Planificador** o bien al terminar una entrada salida, la **CPU** devolverá el resultado de <u>todas</u> las instrucciones ejecutadas durante esa *ráfaga*. Hasta que esto ocurra, la **CPU** no enviará ninguna respuesta relacionada a este proceso.

Al ejecutar una instrucción que requiere acceso a memoria el proceso deberá esperar la respuesta para continuar, aunque esta fuese prolongada. Para simplificar el trabajo práctico, no se contempla el reinicio de una instrucción ante un fallo de página[^3].

[^2] En un Sistema Operativo real, la CPU utilizaría un puntero al código en memoria. A fines de simplificar el trabajo práctico, el proceso **CPU** podrá abrir y cerrar el archivo con el código.
[^2] En un Sistema Operativo real, un fallo de página devolvería una excepción que es tratada de forma especial, generando al menos una operación de entrada salida. Por dicho motivo, es habitual bloquear al proceso hasta que la página solicitada esté disponible, permitiendo que otro proceso utilice la CPU.