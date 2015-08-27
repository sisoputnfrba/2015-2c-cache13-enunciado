# Anexo I: Especificación del lenguaje mAnsisOp

El lenguaje deberá soportar las siguientes operaciones:

## `iniciar N`

- Deberá informar al **Administrador de Memoria** que se ha iniciado un proceso “mProc” de N páginas de datos.
- Deberá retornar la expresión `mProc X - Iniciado` o bien `mProc X - Fallo`, dependiendo de su correcta iniciación.

## `leer N`

- Deberá leer la página N del proceso “mProc” en ejecución.
- Deberá retornar la expresión `mProc X - Pagina N leida:` junto al contenido de esa página concatenado. Ejemplo: `mProc 10 - Pagina 2 leida: contenido`

## `escribir N “texto”`
Deberá escribir el texto en la página N del proceso “mProc” en ejecución, sobreescribiendo todo su contenido. De ser necesario, se rellenará con el caracter ‘\0’. 
Deberá retornar la expresión “mProc X - Pagina N escrita:” junto al nuevo contenido de esa página concatenado. Ejemplo: “mProc 1 - Pagina 2 escrita: otro contenido”.

entrada-salida T
Realizará una entrada-salida de tiempo T. La ejecución de esta instrucción provocará que la CPU informe al Planificador que debe bloquear al proceso “mProc” en ejecución durante T segundos.
Deberá retornar la expresión “mProc X en entrada-salida de tiempo T”.
Además, esta instrucción libera la CPU.

finalizar
Concluye la ejecución del proceso “mProc”. Aquí se da aviso al Administrador de Memoria para que elimine la tabla de páginas asociada, limpie si es necesario la TLB y dé aviso al Administrador de Swap.
Deberá retornar la expresión “mProc X finalizado”.
