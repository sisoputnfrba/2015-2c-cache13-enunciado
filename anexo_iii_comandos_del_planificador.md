# Anexo III: Comandos del Planificador

El proceso **Planificador** deberá ser capaz de soportar los siguientes comandos:

## `correr PATH`
- PATH es la ruta relativa al programa “mCod” a ejecutar.
- Este comando deberá ejecutar el programa en cuestión.
- Ejemplo: `correr prueba.cod` ejecutará el programa “mCod” llamado `prueba.cod`.

## `finalizar PID`
- PID es el ID del proceso “mProc” en ejecución.
- Este comando deberá mover el *puntero de instrucciones* haciéndolo apuntar a la última del programa “mCod”. De esta forma, cuando este proceso ejecute nuevamente, finalizará.
- Ejemplo: `finalizar 13`, colocará el puntero en la última línea del proceso “mProc” de PID 13.

## `ps`
- Este comando deberá escribir en la pantalla del **Planificador** el PID, el nombre del programa y el estado de cada proceso “mProc”.
- El formato deberá ser: `mProc PID: nombre -> estado`, escribiendo en una línea diferente cada proceso “mProc”. Por ejemplo:

```
mProc 1: prueba.cod -> Listo
mProc 2: otro.cod -> Ejecutando
mProc 3: entrada.cod -> Bloqueado
```

## `cpu`

- Este comando deberá escribir en la pantalla del **Planificador** un listado de las CPUs actuales del sistema, indicando para cada una el porcentaje de uso del último minuto. Por ejemplo:

```
cpu 1: 50%
cpu 2: 80%
cpu 3:  0%
```
