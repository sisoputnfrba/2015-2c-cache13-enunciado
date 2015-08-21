# Anexo I: Especificación del lenguaje mAnsisOp

El lenguaje deberá soportar las siguientes operaciones:

## `leer N`

- Deberá leer la página `N` del proceso en ejecución
- Deberá retornar la expresión `Proceso X - Pagina N leida: ` junto al contenido de esa página concatenado. Por ejemplo: `Proceso 10 - Pagina 2 leida: contenido`.

## `escribir "texto" N`

- Deberá escribir el `texto` en la página `N`, sobreescribiendo <u>todo</u> su contenido. De ser necesario, se rellenará con espacios en blanco. 
- Deberá retornar la expresión `Proceso X - Pagina N escrita: ` junto al nuevo contenido de esa página concatenado. Por ejemplo: `Proceso 1 - Pagina 2 escrita: otro contenido`.

## `entrada-salida T`

- Realizará una _entrada-salida_ de tiempo `T`. La ejecución de esta instrucción simplemente informará al planificador que debe bloquear al proceso en ejecución durante `T` milisegundos.
- Además, esta instrucción libera la **CPU**.

## `finalizar`

- Concluye la ejecución del proceso. Aquí se da aviso al **Administrador de Swap** para que elimine el proceso de la *partición de swap* y al **Administrador de Memoria** para que elimine la tabla de páginas asociada y limpie si es necesario la TLB.
