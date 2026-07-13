# Unidad 3: Modularidad y Arreglos

Repositorio académico desarrollado en **Python**, orientado a estudiantes universitarios de programación, que aborda dos pilares fundamentales de la construcción de software: la **modularidad** (con sus dos formas de paso de parámetros) y los **arreglos** en sus tres dimensiones más comunes (unidimensional, bidimensional y tridimensional).

Todos los ejemplos están ambientados en escenarios tecnológicos (estaciones espaciales, drones autónomos, bases científicas) para evitar los ejercicios clásicos de aula y fomentar un aprendizaje más significativo.

---

## 📌 Introducción

Cuando un programa crece en tamaño y complejidad, escribirlo como un único bloque de instrucciones se vuelve insostenible: es difícil de leer, de depurar y de mantener. La **modularidad** resuelve este problema dividiendo el software en piezas más pequeñas y manejables (funciones, procedimientos, módulos), mientras que los **arreglos** permiten organizar y manipular grandes volúmenes de datos relacionados bajo una sola estructura, en lugar de declarar decenas de variables sueltas.

Este repositorio combina ambos conceptos en ejemplos ejecutables, documentados y comentados, acompañados de teoría redactada desde cero y de un análisis crítico sobre las dificultades más comunes que enfrenta un programador al trabajar con ellos.

---

## 🎯 Objetivos

- Comprender qué es la modularidad y por qué es una práctica esencial en la ingeniería de software.
- Diferenciar de forma práctica el paso de parámetros **por valor** y **por referencia** en Python.
- Comprender la estructura, el uso y las limitaciones de los arreglos unidimensionales, bidimensionales y tridimensionales.
- Aplicar buenas prácticas de programación (PEP 8, Clean Code) en proyectos reales.
- Reflexionar críticamente sobre los errores más comunes al trabajar con funciones y arreglos, y sobre su relevancia en áreas como la inteligencia artificial, los videojuegos y la ciencia de datos.

---

## 🧠 Competencias desarrolladas

- Diseño modular de soluciones de software.
- Manejo de estructuras de datos multidimensionales.
- Pensamiento algorítmico y lógico.
- Redacción de documentación técnica siguiendo estándares profesionales.
- Depuración y análisis crítico de código.
- Buenas prácticas de organización de proyectos para control de versiones (Git/GitHub).

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| Python 3.10+ | Lenguaje principal de desarrollo |
| Markdown | Documentación técnica |
| Git / GitHub | Control de versiones y publicación |
| PEP 8 | Estándar de estilo de código |

No se requieren librerías externas: todos los programas funcionan únicamente con la biblioteca estándar de Python.

---

## 📂 Estructura del proyecto

---

## 📁 Explicación de cada carpeta

- **`modularidad/`**: contiene la teoría sobre modularidad y dos programas ejecutables que demuestran, respectivamente, el paso de parámetros por valor y por referencia, ambos aplicados a la gestión de una estación espacial.
  
 [![Modularidad Tema 1](https://img.shields.io/badge/Modularidad%20A%20LA%20Tema_1-CLICK%20AQUÍ-7434eb?style=for-the-badge&logo=github&logoColor=white)](./Modularidad.md)
</details>

- **`arreglos/`**: contiene la teoría sobre arreglos y tres programas ejecutables que demuestran el uso de arreglos unidimensionales, bidimensionales y tridimensionales en escenarios de inventario, exploración con drones y sensores atmosféricos.
- **`analisis/`**: contiene la reflexión crítica del trabajo, con un análisis profundo de las dificultades más comunes al programar con funciones y arreglos, así como su relación con áreas avanzadas de la computación.
- **`imagenes/`**: contiene una lista de diagramas sugeridos para acompañar visualmente la documentación (no se incluyen las imágenes, solo su descripción y propósito).

---

## ▶️ Cómo ejecutar cada programa

Se requiere tener instalado **Python 3.10 o superior**. Para ejecutar cualquiera de los programas, ubíquese en la raíz del repositorio y utilice el intérprete de Python:

```bash
# Módulo: paso por valor
python modularidad/paso_por_valor.py

# Módulo: paso por referencia
python modularidad/paso_por_referencia.py

# Arreglo unidimensional
python arreglos/unidimensional.py

# Arreglo bidimensional
python arreglos/bidimensional.py

# Arreglo tridimensional
python arreglos/tridimensional.py
```

Cada programa despliega un menú interactivo en consola. Basta con seguir las instrucciones que se muestran en pantalla e ingresar las opciones solicitadas.

---

## ✅ Conclusiones generales
 
1. La modularidad no es solo una técnica de organización de código: es una forma de pensar la solución de un problema en partes verificables de manera independiente.
2. Comprender la diferencia entre paso por valor y paso por referencia evita errores silenciosos que son difíciles de detectar en etapas avanzadas de un proyecto.
3. Los arreglos son la base estructural sobre la que se construyen estructuras de datos más complejas (matrices, tensores, grafos), por lo que dominarlos es indispensable antes de avanzar a temas como IA o ciencia de datos.
4. La combinación de buenas prácticas de documentación y de código limpio facilita enormemente el trabajo colaborativo, especialmente en repositorios públicos como los de GitHub.
5. La reflexión crítica sobre los propios errores de programación (índices fuera de rango, referencias no deseadas, etc.) es tan formativa como la escritura del código correcto.

---

## 👤 Autoría

Trabajo académico elaborado para la **Unidad 3: Modularidad y Arreglos**, con fines educativos, bajo licencia MIT (ver archivo `LICENSE`).
