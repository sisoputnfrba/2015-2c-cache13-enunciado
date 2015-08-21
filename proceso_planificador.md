# Proceso Planificador

Será el encargado de administrar la ejecución de los procesos, permitiendo que estos inicien, ordenándolos para que ejecuten y finalizándolos cuando sea necesario.

A partir de que este proceso inicie, deberá mostrar por pantalla una consola, que será capaz de soportar el comando `run PATH`, donde `PATH` es la ruta al archivo mAnsisOp a ejecutar (por ejemplo `run programa`, correrá el archivo `programa`). Se debe contemplar la posibilidad de estar ejecutando varios procesos concurrentemente (*multiprogramación*), por lo que la consola deberá estar <u>siempre</u> disponible.

Al poner en ejecución un proceso, se generará su _PCB_[^1] asociado, incluyendo en él la ruta del archivo. Cada archivo ejecutable estará asociado a un archivo de igual nombre, pero con la extensión `.swp` (por ejemplo, `programa` estará asociado a `programa.swp`). En este segundo archivo, denominado _de swap_, estarán cargadas las páginas iniciales del proceso.

El **Planificador** será también el responsable de decidir qué proceso debe ejecutar en cada momento, basándose en diferentes algoritmos y conociendo la disponibilidad de cada **CPU**. Una vez tomada la decisión, deberá enviar a la **CPU** la información del *PCB* (es decir, su *contexto de ejecución*), y la cantidad de sentencias a ejecutar, en caso de que la planificación se realice *con desalojo*. Cuando la **CPU** finalice la ejecución, devolverá una serie de mensajes, que deberán ser escritos en el log del proceso. Para simplicidad a la hora de planificar, cualquier **CPU** libre podrá ser otorgada a un proceso que la necesite.

[^1] El _PCB_ tendrá toda aquella información que el grupo considere necesaria para ejecutar los procesos. Esta estructura será validada y justificada con los ayudantes asignados, en las diferentes instancias de evaluación.