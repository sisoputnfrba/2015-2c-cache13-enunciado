# Eventos de Logueo Obligatorio

Existen eventos que ocurren en cada proceso desarrollado que son relevantes para la verificación de su correcto funcionamiento. Es por eso que, más abajo, se definen una serie de eventos de logueo obligatorios.

## Planificador

- Comienzo y fin de ejecución de procesos, indicando al menos: PID asignado y nombre del archivo “mCod”.
- Conexión y desconexión de **CPUs**.
- Ejecución del algoritmo de planificación, indicando el proceso “mProc” seleccionado para ejecutar y el contenido ordenado de todas las colas de planificación.
- Ráfaga de **CPU** completada, indicando el proceso mProc y todos los mensajes de la CPU.

## CPU

Todos los hilos compartirán el mismo archivo log, prefijando en cada evento el número de cpu que está realizando el logueo

- Instancia de **CPU** creada/conectada al **Administrador de Memoria**, indicando el identificador de hilo **CPU** (id)
- *Contexto de ejecución* recibido, indicando todos sus datos, y el quantum de ejecución.
- Instrucción ejecutada, indicando PID, el valor de sus parámetros (si hubiese) y el resultado de la instrucción.
- Ejecución de ráfaga concluída, indicando PID.

## Administrador de Memoria

- Proceso mProc creado, indicando PID y cantidad de páginas asignadas
- Solicitud de escritura/lectura recibida, indicando PID y N° de página
TLB hit/miss, indicando N° de página ingresado, N° de marco resultante, y en caso de miss resultado del algoritmo de reemplazo (si aplica)
- Acceso a memoria realizado, indicando PID, N° de página y N° de marco
- Acceso a swap (fallo de página), indicando PID, resultado del algoritmo de sustitución de páginas, estado inicial y final de las colas y punteros correspondientes (si aplica)
- Señal recibida/tratamiento de señal terminado, indicando tipo y acción a ejecutar.

## Administrador de Swap

- Proceso mProc asignado, indicando PID, N° de byte inicial, y tamaño en bytes
- Proceso mProc liberado, indicando PID, N° de byte inicial, y tamaño en bytes liberado
- Proceso mProc rechazado por falta de espacio
- Compactación iniciada/finalizada por fragmentación externa
- Escritura/lectura solicitada, indicando PID, N° de byte inicial, tamaño y contenido

En general, no se debería imprimir por pantalla ninguno de estos eventos, sino que para ello debe usarse el archivo de log. Se reservará la impresión por pantalla para indicar terminaciones anormales, escribiendo los detalles en el archivo de log. 
Para poder seguir las entradas que va logueando un proceso del Sistema Operativo, se recomienda usar el comando: `tail -f <archivo de log>`, que va imprimiendo nuevas líneas conforme va creciendo dicho archivo. Por ejemplo:

```
> tail -f cpu_instancia_01.log
```

Cada vez que un proceso del Sistema Operativo inicie su ejecución, deberá imprimir en el log una línea especial indicando que comenzó la ejecución del mismo. Además, es posible ampliar la cantidad de eventos a loguear por encima de los mínimos especificados arriba, siempre que contribuya a entender el funcionamiento del programa y el mismo siga siendo legible y fácil de seguir. Se recomienda utilizar la funcionalidad de Logging de la [Commons Library](https://github.com/sisoputnfrba/so-commons-library) que facilita la generación y escritura de archivos de log.