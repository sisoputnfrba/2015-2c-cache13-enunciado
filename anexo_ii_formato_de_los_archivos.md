# Anexo II: Formato de los archivos

Los archivos ejecutables tendrán el siguiente formato:

- N cantidad de instrucciones
- Terminan con la instrucción `finalizar`
- Se coloca una instrucción por línea

Ejemplo de programa:

```
escribir "Hola" 1
leer 1
entrada-salida 5000
finalizar
```

Los archivos de swap tendrán el siguiente formato:

- Pag: Contenido
- Las páginas estarán ordenadas y comenzarán en 0
- No habrá huecos
- El contenido podrá ser interpretado como texto, sin tildes, caracteres especiales ni eñes
- La última página de este archivo será la última página válida: no se contempla que el _espacio de direccione de un proceso_ crezca en tiempo de ejecución
- Se coloca una página por línea

Ejemplo de `programa.swp`:

```
0: primera pagina
1: segunda pagina
2: tercera pagina con numeros 123
```