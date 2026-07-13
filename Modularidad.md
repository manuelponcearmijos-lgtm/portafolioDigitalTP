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

## Explicación del Ejemplo 1 — Sistema Inteligente de Gestión Energética de una Estación Espacial (paso por valor)

### Objetivo

Demostrar que, al pasar un dato numérico (float) como parámetro a una función, cualquier modificación realizada dentro de dicha función **no altera** el valor original almacenado fuera de ella.

### Variables utilizadas

- `energia_actual`: nivel de energía disponible en la estación (float, dato "sensible" que no debe alterarse por accidente).
- `consumo_modulo`: cantidad de energía que un módulo solicita consumir.
- `historial_consumos`: lista que registra cada simulación realizada.
- `opcion`: variable de control del menú.

### Funciones utilizadas

1. `mostrar_menu()`: procedimiento que imprime las opciones disponibles.
2. `leer_opcion()`: función que valida que la opción ingresada sea un número entero dentro del rango del menú.
3. `simular_consumo(energia_disponible, consumo)`: función principal que recibe el nivel de energía **por valor** y calcula cuánto quedaría disponible tras un consumo, sin modificar el original.
4. `registrar_simulacion(historial, resultado)`: agrega un resultado de simulación al historial (aquí se usa una lista como registro interno del propio programa, no como parte del experimento de paso por valor).
5. `mostrar_historial(historial)`: procedimiento que imprime todas las simulaciones registradas.
6. `validar_numero(mensaje)`: función auxiliar que valida que la entrada del usuario sea un número válido y no negativo.
7. `main()`: función principal que orquesta el flujo del programa mediante el menú.

### Flujo del programa

1. Se inicializa la energía actual de la estación con un valor fijo.
2. Se muestra un menú con opciones para simular un consumo energético, ver el historial de simulaciones o salir.
3. Al simular un consumo, el programa solicita la cantidad de energía que un módulo desea consumir.
4. Se invoca `simular_consumo()` pasando la energía actual **por valor**.
5. Al finalizar la simulación, el programa imprime tanto el resultado simulado como el valor original de `energia_actual`, demostrando que este último permanece intacto.

### Explicación paso a paso de la función principal

```python
def main():
    energia_actual = 1500.0          # Energía real de la estación, no debe alterarse por accidente
    historial_consumos = []

    while True:
        mostrar_menu()
        opcion = leer_opcion()

        if opcion == 1:
            consumo = validar_numero("Ingrese el consumo solicitado (kWh): ")
            resultado_simulado = simular_consumo(energia_actual, consumo)
            registrar_simulacion(historial_consumos, resultado_simulado)
            print(f"Energía simulada restante: {resultado_simulado:.2f} kWh")
            print(f"Energía real de la estación (sin cambios): {energia_actual:.2f} kWh")
        elif opcion == 2:
            mostrar_historial(historial_consumos)
        elif opcion == 3:
            print("Cerrando sistema de gestión energética...")
            break
```

- Se declara `energia_actual` como la variable "real" del sistema.
- El ciclo `while True` mantiene el menú activo hasta que el usuario decida salir.
- Cuando se elige la opción de simular consumo, se pide un valor validado y se llama a `simular_consumo()`, que recibe `energia_actual` por valor (al tratarse de un `float`, un tipo inmutable).
- Se imprime el resultado simulado junto con el valor original de `energia_actual`, evidenciando que este no cambió pese a haberse "modificado" dentro de la función.

### Salida esperada
[![Acceder a Unidad 3](https://img.shields.io/badge/ACCEDER%20A%20LA%20UNIDAD_3-CLICK%20AQUÍ-7434eb?style=for-the-badge&logo=github&logoColor=white)](./Unidad_3.md)
</details>
