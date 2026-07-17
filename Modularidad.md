# Modularidad

## ¿Qué es la modularidad?

La modularidad es la práctica de descomponer un programa en unidades independientes —llamadas comúnmente **funciones**, **procedimientos** o **módulos**— cada una encargada de resolver una tarea concreta y acotada. En lugar de escribir todo el comportamiento de un sistema en un único bloque de instrucciones, el programador separa la lógica en piezas que pueden diseñarse, probarse y corregirse de manera aislada.

Pensar de forma modular es, en esencia, aplicar la misma estrategia que usamos para resolver cualquier problema grande de la vida real: dividirlo en partes más pequeñas y abordables. Un sistema de gestión de una estación espacial, por ejemplo, no se programa como un solo script gigante; se separa en módulos de energía, de escudos, de comunicaciones, de soporte vital, etc., y cada uno se conecta con los demás mediante interfaces bien definidas (funciones con parámetros y valores de retorno).

## Objetivos de la modularidad

- Reducir la complejidad de un sistema dividiéndolo en partes comprensibles.
- Permitir que distintas personas trabajen sobre distintos módulos sin interferir entre sí.
- Facilitar la localización y corrección de errores, ya que cada módulo tiene una responsabilidad concreta.
- Favorecer la reutilización de código en distintos contextos del mismo proyecto o incluso en otros proyectos.

## Características

- **Cohesión interna**: cada módulo agrupa instrucciones relacionadas entre sí y orientadas a un mismo propósito.
- **Bajo acoplamiento**: los módulos se comunican mediante interfaces claras (parámetros, retornos) y no dependen de los detalles internos de otros módulos.
- **Independencia funcional**: un módulo puede modificarse internamente sin afectar a los demás, siempre que su interfaz externa se mantenga.
- **Reutilización**: una función bien diseñada puede invocarse desde distintas partes de un programa sin duplicar código.

## Ventajas

- Código más legible y organizado.
- Depuración más sencilla, al poder aislar el módulo donde ocurre un error.
- Facilita las pruebas unitarias, ya que cada función puede probarse por separado.
- Permite el trabajo colaborativo en equipos grandes, dividiendo responsabilidades por módulo.
- Escalabilidad: agregar nuevas funcionalidades implica, en general, agregar nuevos módulos sin reescribir los existentes.

## Desventajas

- Un diseño modular mal planificado puede generar dependencias ocultas entre módulos, dificultando su mantenimiento.
- Introduce una sobrecarga inicial de diseño: definir correctamente qué hace cada módulo y cómo se comunican requiere tiempo de análisis previo.
- Un exceso de fragmentación (funciones demasiado pequeñas o innecesarias) puede terminar dificultando, en lugar de facilitar, la lectura del flujo general del programa.

## Importancia en el desarrollo de software

En proyectos reales, el software rara vez lo mantiene una sola persona ni se termina en una sola versión. La modularidad permite que un sistema evolucione con el tiempo: se agregan funcionalidades, se corrigen errores y se reemplazan partes internas sin que el resto del sistema se vea afectado. Sin modularidad, cualquier cambio pequeño podría romper partes no relacionadas del programa, lo cual vuelve inviable el mantenimiento a largo plazo.

## Diferencia entre funciones y procedimientos

Aunque en el lenguaje cotidiano se usan como sinónimos, existe una diferencia conceptual:

- Una **función** recibe datos de entrada (parámetros) y **retorna un valor** como resultado de su ejecución. Se puede usar directamente dentro de una expresión (por ejemplo, `total = calcular_costo(consumo)`).
- Un **procedimiento** ejecuta una serie de acciones, pero **no necesariamente retorna un valor** útil para el programa; su propósito principal es producir un efecto (mostrar información, modificar una estructura de datos, etc.).

En Python, ambos conceptos se implementan con la palabra reservada `def`. La diferencia es de diseño: si la función termina con `return valor`, actúa como función en el sentido estricto; si no retorna nada relevante (o retorna `None` implícitamente), actúa como procedimiento.

## Parámetros

Los parámetros son los mecanismos mediante los cuales una función recibe información desde quien la invoca. Existen dos formas principales de "pasar" esa información:

### Parámetros por valor

Cuando se pasa un parámetro **por valor**, la función recibe una **copia** del dato original. Cualquier modificación realizada dentro de la función sobre ese parámetro **no afecta** a la variable original que existe fuera de la función. En Python, esto ocurre de forma natural con los tipos de datos **inmutables**: números (`int`, `float`), cadenas (`str`), tuplas (`tuple`) y booleanos (`bool`). Como estos tipos no pueden modificarse en el lugar donde residen en memoria, cualquier "modificación" en realidad crea un nuevo objeto dentro del ámbito local de la función.

### Parámetros por referencia

Cuando se pasa un parámetro **por referencia**, la función recibe una referencia al **mismo objeto** en memoria que la variable original. Si dentro de la función se modifica el contenido de ese objeto (no se reemplaza por uno nuevo, sino que se altera su contenido interno), el cambio **sí se refleja** en la variable original, porque ambas apuntan al mismo espacio de memoria. En Python esto ocurre con los tipos de datos **mutables**: listas (`list`), diccionarios (`dict`) y conjuntos (`set`).

Es importante aclarar que Python, técnicamente, siempre pasa "una referencia al objeto" (a esto se le llama *pass by object reference* o *pass by assignment*). La diferencia de comportamiento que percibimos como "por valor" o "por referencia" depende, en realidad, de si el tipo de dato es inmutable o mutable, y de si dentro de la función se reasigna la variable (lo cual no afecta al original) o se modifica el objeto en el lugar (lo cual sí afecta al original).

## Casos de uso reales

- **Paso por valor**: se usa cuando queremos garantizar que una función no altere accidentalmente un dato sensible, por ejemplo, al realizar un cálculo de simulación o proyección sobre una lectura de sensor sin alterar la lectura original.
- **Paso por referencia**: se usa cuando el propósito explícito de la función es modificar una estructura de datos compartida por el resto del sistema, por ejemplo, actualizar el estado de un inventario, el nivel de un escudo o el contenido de una base de datos en memoria.

---

[![Presentación - Paso por Valor](https://img.shields.io/badge/🧪%20Presentación%20-%20Paso%20por%20Valor-8A2BE2?style=for-the-badge)](paso_por_valor.md)

[![Presentación - Paso por Referencia](https://img.shields.io/badge/🛠️%20Presentación%20-%20Paso%20por%20Referencia-8A2BE2?style=for-the-badge)](paso_por_referencia.md)

--- 
[![Acceder a Unidad 3](https://img.shields.io/badge/ACCEDER%20A%20LA%20UNIDAD_3-CLICK%20AQUÍ-7434eb?style=for-the-badge&logo=github&logoColor=white)](./Unidad_3.md)
</details>
