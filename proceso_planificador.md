# Proceso Planificador

Será el encargado de administrar la ejecución de los procesos “mProc”, permitiendo que estos inicien, ordenándolos para que ejecuten en las distintas **CPUs** y finalizándolos cuando sea necesario. Para ello, utilizará programas “mCod”, que serán puestos en ejecución. 

A partir de que el **Planificador** inicie, deberá mostrar por pantalla una consola, que será capaz de soportar algunos comandos, definidos en el anexo respectivo. Se debe contemplar la posibilidad de ejecutar varios procesos “mProc” concurrentemente (_multiprogramación_), por lo cual la consola deberá estar <u>siempre</u> disponible. Además, el mismo programa “mCod” deberá poder ser ejecutado más de una vez,  generando múltiples procesos “mProc” conviviendo al mismo tiempo en el sistema.

Luego de iniciado, el **Planificador** quedará a la espera de que se conecten distintas **CPUs**, sobre las cuales enviará a ejecutar estos procesos cuando la planificación lo indique y cuando éstas se encuentren libres.

Tras recibir por consola una solicitud de ejecución de un programa “mCod”, se generará su _PCB[^2]_ asociado, incluyendo en él la ruta relativa del archivo; una vez creada esta estructura se lo podrá considerar como listo para ejecutar. Para más detalles sobre el formato de este archivo ver el [Anexo II: Formato de los Archivos](anexo_ii_formato_de_los_archivos.md).

El **Planificador** será también el responsable de decidir qué proceso debe ejecutar en cada momento, basándose en diferentes algoritmos y conociendo la disponibilidad de cada **CPU**. Una vez tomada la decisión, deberá enviar a la **CPU** su _contexto de ejecución_ (en nuestro caso, la ruta al “mCod” y el puntero a la próxima instrucción), y la cantidad de sentencias a ejecutar en caso de que la planificación se realice con _desalojo_. Cuando la **CPU** finalice la ejecución de cada *ráfaga[^3]* o bien cuando interrumpa la ejecución de un proceso, ésta devolverá una serie de mensajes, que deberán ser escritos en el log del proceso **Planificador**. Para simplicidad a la hora de planificar, cualquier **CPU** libre podrá ser otorgada a un proceso que la necesite.

El algoritmo de planificación a utilizar deberá ser especificado por archivo de configuración, así como todos los parámetros adicionales que cada algoritmo en particular requiera.

## Archivo de configuración

| Nombre de Campo           | Valor de ejemplo |
|:-------------------------:|:----------------:|
| `PUERTO_ESCUCHA`          | `4000`           |
| `ALGORITMO_PLANIFICACION` | `FIFO`[^4]       |
| `QUANTUM`                 | `5`              |

El valor de Quantum sólo será utilizado si el algoritmo usado lo requiere.

[^2] El _Process Control Block (PCB)_ será una estructura de datos que tendrá toda aquella información que el grupo considere necesaria para ejecutar los procesos. La misma deberá ser validada y justificada con los ayudantes asignados, en las diferentes instancias de evaluación.
[^3] Se considera una _ráfaga_ a un conjunto de instrucciones que ejecuta una CPU en un determinado período de tiempo hasta que finaliza, se bloquea o es interrumpido.
[^4] Otra alternativa es `RR`.