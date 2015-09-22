# Introducción

**Cache 13** es un pequeño sistema que emulará el funcionamiento de algunos módulos del Sistema Operativo. El mismo permitirá ejecutar algunos programas a los que llamaremos “mCod”, compuestos de sentencias sencillas. Estos programas en ejecución serán denominados procesos “mProc”. El orden en el cual se ejecutarán estará determinado por un planificador de corto plazo que, basándose en diferentes algoritmos, seleccionará el siguiente proceso a ejecutar.

La ejecución de estas sentencias requerirá diferentes accesos a memoria, tales como lecturas, escrituras, inicialización y finalización. Estos accesos serán realizados utilizando un administrador de memoria, y requerirán la utilización de todos los conceptos aprendidos durante las clases. 

Esta simulación tiene por objetivo profundizar en conceptos relacionados a la planificación de procesos y a la utilización de memoria virtual en un Sistema Operativo tradicional, implementado con paginación por demanda. Por ende, algunos de los accesos a memoria, requerirán también accesos a una partición de swap.

Para que el desarrollo del Trabajo Práctico coincida con el orden en que se dictan los temas de la materia, las diferentes entregas (de aquí en más, checkpoints) fueron cuidadosamente confeccionadas, evitando así retrabajo. Recomendamos fuertemente respetar este orden. Los requisitos indicados son los **mínimos** para considerar el checkpoint aprobado, pero es una excelente práctica continuar avanzando en caso de cumplirlos antes de la fecha límite.

Para mejor comprensión de la terminología utilizada, se colocarán en **negrita** las referencias a los diferentes procesos del TP. Los términos en _itálica_ harán referencia a conceptos que fueron o serán vistos durante las clases teóricas. Por último, se enfatizarán ciertos aspectos que no deben ser pasados por alto utilizando <u>texto subrayado</u>.
