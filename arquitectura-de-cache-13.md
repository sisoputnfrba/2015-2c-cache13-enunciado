El sistema “Cache 13” constará de los siguientes Procesos[^1]:

![Arquitectura de Cache 13](arquitectura-cache-13.png)

Los mismos deberán ser capaces de correr en tres PCs diferentes, como muestra el esquema. Al iniciarse, deberán conectarse teniendo en cuenta que los diferentes <u>pedidos</u> se realizarán en el sentido que muestran las flechas.

Para que la evaluación del trabajo práctico sea la adecuada, es muy importante que todos los parámetros que se mencionan como configurables estén en archivos de configuración correspondientes a cada proceso. Esta práctica se debe realizar también para parámetros de entorno tales como IPs, puertos, rutas, etc. Algunos procesos retardan la ejecución de ciertas funcionalidades, a fin de que la simulación se acerque más a un caso real, por lo cual se recomienda investigar el uso de las funciones para “dormir” procesos, conocidas como la familia de funciones `sleep()`. Este es el <u>único</u> caso donde estará permitido su uso.

Dado que el Trabajo Práctico se realizará de forma incremental, se recomienda prestar especial atención al diseño de las interfaces entre los diferentes procesos. De esta forma, cuando una funcionalidad crezca, la interfaz será la misma. Esto es especialmente útil cuando se requiera implementar diferentes algoritmos que realicen la misma tarea de forma distinta.

[^1] _Proceso_: un programa en ejecución. Para más información referirse a la clase teórica asociada.