# Arreglos

## ¿Qué es un arreglo?

Un arreglo es una estructura de datos que permite almacenar una colección de elementos del mismo tipo (o de tipos compatibles) bajo un único nombre, organizados de forma secuencial y accesibles mediante un **índice numérico**. En lugar de crear una variable independiente por cada dato relacionado (por ejemplo, `sensor1`, `sensor2`, `sensor3`...), un arreglo agrupa todos esos valores en una sola estructura recorrible.

En Python no existe un tipo de dato "arreglo" nativo tan rígido como en otros lenguajes (C, Java); en su lugar, la **lista** (`list`) cumple ese rol de forma flexible, permitiendo además crear arreglos de más de una dimensión mediante listas anidadas (listas de listas, listas de listas de listas, etc.).

## Características

- Cada elemento del arreglo ocupa una posición identificada por un índice, que en Python comienza en 0.
- Los arreglos pueden ser de una, dos, tres o más dimensiones, según la cantidad de índices necesarios para ubicar un elemento.
- El tamaño de una lista en Python es dinámico: puede crecer o reducirse durante la ejecución del programa.
- Se puede recorrer un arreglo de forma secuencial mediante bucles (`for`, `while`) o mediante comprensión de listas.

## Ventajas

- Permiten almacenar y procesar grandes volúmenes de datos relacionados de forma organizada.
- Facilitan operaciones repetitivas sobre conjuntos de datos (recorridos, búsquedas, ordenamientos).
- Reducen drásticamente la cantidad de variables individuales que un programa necesitaría declarar.
- Son la base para representar estructuras del mundo real: mapas, imágenes, volúmenes, tableros, matrices de datos.

## Desventajas

- Acceder a un índice que no existe genera un error en tiempo de ejecución (`IndexError`), lo cual exige validar los límites cuidadosamente.
- Cuando el arreglo es multidimensional, el código puede volverse difícil de leer si no se documentan bien los ejes o dimensiones que representa cada índice.
- En listas de Python, insertar o eliminar elementos en posiciones intermedias puede ser costoso en términos de rendimiento para arreglos muy grandes.

## Tipos de arreglos

- **Unidimensional (vector)**: una secuencia simple de elementos, accesible con un solo índice. Ejemplo: `inventario[3]`.
- **Bidimensional (matriz)**: una tabla de filas y columnas, accesible con dos índices. Ejemplo: `mapa[fila][columna]`.
- **Tridimensional (volumen)**: una estructura de capas, filas y columnas, accesible con tres índices. Ejemplo: `sensores[capa][fila][columna]`.

## Índices

El índice es la "dirección" que utilizamos para ubicar un elemento dentro del arreglo. En Python, el primer elemento de una lista está en el índice `0`, el segundo en el índice `1`, y así sucesivamente hasta `n - 1`, donde `n` es la cantidad de elementos. Intentar acceder a un índice igual o mayor que `n` (o menor que el índice negativo válido más bajo) produce un `IndexError`.

## Memoria

Internamente, una lista de Python almacena referencias a los objetos que contiene, no los valores "puros" en bloques contiguos como ocurriría en un arreglo de C. Esto le da flexibilidad (una lista puede mezclar tipos de datos) a costa de un poco más de uso de memoria por cada elemento. En arreglos multidimensionales implementados como listas de listas, cada "fila" es en realidad una lista independiente referenciada desde la lista contenedora, lo cual es importante tener en cuenta al copiar estructuras (una copia superficial puede compartir las filas internas entre dos variables distintas).

## Casos de uso

- **Unidimensional**: inventarios, listas de tareas, historial de eventos, colas de procesos.
- **Bidimensional**: mapas de videojuegos, hojas de cálculo, imágenes en escala de grises (píxeles), tableros de juegos.
- **Tridimensional**: volúmenes médicos (tomografías), simulaciones atmosféricas o climáticas, voxeles en gráficos 3D, tensores de datos en aprendizaje automático.

---

## Explicación del ejemplo — Inventario Inteligente de una Mochila Tecnológica (arreglo unidimensional)

### Objetivo

Demostrar el uso de un arreglo unidimensional (lista) para gestionar el inventario de una mochila tecnológica, permitiendo agregar, mostrar, buscar y contar objetos.

### Variables utilizadas

- `inventario`: lista que almacena diccionarios, cada uno representando un objeto (nombre, categoría, peso).
- `opcion`: variable de control del menú.

### Funciones utilizadas

- `mostrar_menu()`, `leer_opcion()`: manejo del menú.
- `agregar_objeto(inventario, objeto)`: agrega un nuevo elemento al final del arreglo mediante `append()`.
- `mostrar_inventario(inventario)`: recorre el arreglo con un `for` e imprime cada objeto junto a su índice.
- `buscar_objeto(inventario, nombre)`: recorre el arreglo comparando el nombre buscado con el de cada elemento, y retorna su posición o `-1` si no existe.
- `contar_objetos(inventario)`: retorna la longitud del arreglo mediante `len()`.

### Flujo del programa

1. Se inicializa `inventario` como una lista vacía.
2. El menú permite agregar un objeto (solicitando nombre, categoría y peso), mostrar todo el inventario, buscar un objeto por nombre o contar cuántos objetos existen actualmente.
3. Cada operación se implementa recorriendo o modificando el arreglo unidimensional.

### Entrada / Proceso / Salida

- **Entrada**: nombre, categoría y peso de cada objeto tecnológico a registrar; nombre del objeto a buscar.
- **Proceso**: inserción al final del arreglo (`append`), recorrido secuencial (`for` con `enumerate`), comparación de cadenas para la búsqueda.
- **Salida**: listado del inventario con su índice, resultado de la búsqueda (posición encontrada o mensaje de "no encontrado"), y el total de objetos almacenados.

### Resultado esperado

Un menú funcional que permite construir progresivamente un inventario, consultarlo por completo o buscar un objeto específico por nombre, mostrando siempre información consistente con lo almacenado en la lista.

---

## Explicación del ejemplo — Mapa de Exploración de un Dron Autónomo (arreglo bidimensional)

### Objetivo

Representar una cuadrícula de exploración (matriz) que un dron recorre, permitiendo ingresar hallazgos en celdas específicas, recorrer la matriz completa, localizar posiciones concretas e imprimir el mapa de forma ordenada.

### Variables utilizadas

- `mapa`: lista de listas (matriz) de tamaño `FILAS x COLUMNAS`, donde cada celda almacena un carácter o etiqueta que representa lo que el dron detectó (vacío, obstáculo, recurso).
- `fila`, `columna`: índices que ubican una celda específica dentro de la matriz.

### Funciones utilizadas

- `crear_mapa(filas, columnas)`: genera la matriz inicial llena de un valor "vacío" (`"."`), usando comprensión de listas para evitar filas compartidas por referencia.
- `mostrar_mapa(mapa)`: recorre la matriz con dos bucles anidados (uno por fila, otro por columna) e imprime el contenido de forma alineada.
- `registrar_hallazgo(mapa, fila, columna, simbolo)`: valida que los índices estén dentro de los límites y actualiza la celda correspondiente.
- `localizar_simbolo(mapa, simbolo)`: recorre toda la matriz devolviendo la lista de coordenadas `(fila, columna)` donde aparece un símbolo determinado.
- `indices_validos(mapa, fila, columna)`: función auxiliar que valida los límites de la matriz antes de acceder a una celda, evitando un `IndexError`.

### Flujo del programa

1. Se crea el mapa con dimensiones fijas, inicializado con celdas vacías.
2. El menú permite registrar un hallazgo en una celda (validando que la posición exista dentro de la matriz), mostrar el mapa completo o localizar todas las coordenadas donde aparece un símbolo determinado.

### Entrada / Proceso / Salida

- **Entrada**: dimensiones del mapa (fijas en este ejemplo), coordenadas de fila y columna, símbolo a registrar o buscar.
- **Proceso**: doble iteración anidada para recorrer la matriz, validación de índices antes de acceder a una celda, búsqueda lineal de coincidencias.
- **Salida**: representación visual del mapa alineado en filas y columnas, y listado de coordenadas donde se encontró un símbolo específico.

### Resultado esperado

Una cuadrícula que refleja fielmente las actualizaciones realizadas por el usuario, con una impresión ordenada que simula la vista aérea de la zona explorada por el dron.

---

## Explicación del ejemplo — Sistema de Sensores Atmosféricos de una Base Científica (arreglo tridimensional)

### Objetivo

Representar un volumen tridimensional de sensores de temperatura (capas de altitud, filas y columnas de una cuadrícula geográfica), permitiendo almacenar, recorrer y consultar temperaturas por coordenada exacta.

### Variables utilizadas

- `sensores`: lista de listas de listas (`CAPAS x FILAS x COLUMNAS`), donde cada posición almacena una temperatura simulada.
- `capa`, `fila`, `columna`: los tres índices necesarios para ubicar un sensor específico dentro del volumen.

### Funciones utilizadas

- `crear_volumen(capas, filas, columnas)`: construye la estructura tridimensional inicializada con un valor por defecto, evitando referencias compartidas entre sublistas.
- `asignar_temperatura(sensores, capa, fila, columna, temperatura)`: valida los tres índices y actualiza el valor correspondiente.
- `recorrer_volumen(sensores)`: utiliza tres bucles anidados para recorrer cada capa, fila y columna, mostrando la coordenada y la temperatura registrada.
- `temperatura_promedio_capa(sensores, capa)`: recorre una única capa (matriz bidimensional) y calcula el promedio de sus temperaturas.
- `indices_validos(sensores, capa, fila, columna)`: función auxiliar de validación de límites en las tres dimensiones.

### Flujo del programa

1. Se crea el volumen de sensores con dimensiones fijas (por ejemplo, 2 capas de altitud, cada una con una cuadrícula de 3x3).
2. El menú permite asignar una temperatura a una coordenada específica, recorrer todo el volumen mostrando cada coordenada y su valor, o calcular el promedio de temperatura de una capa completa.

### Entrada / Proceso / Salida

- **Entrada**: coordenadas de capa, fila y columna; valor de temperatura a asignar.
- **Proceso**: triple iteración anidada para recorrer el volumen completo, validación de los tres índices antes de acceder a una posición, cálculo de promedios por capa.
- **Salida**: listado de todas las coordenadas del volumen junto a su temperatura, y el promedio de temperatura de una capa específica.

### Resultado esperado

Una estructura tridimensional consistente que permite ubicar y consultar la temperatura exacta de cualquier punto del volumen definido, simulando el comportamiento de una red de sensores distribuidos en altitud y en una cuadrícula geográfica.
