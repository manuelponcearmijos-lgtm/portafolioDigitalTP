 <div align="center">

# 🚀 Unidad 3: Modularidad y Arreglos
### Edición en Lenguaje C

![Lenguaje](https://img.shields.io/badge/Lenguaje-C11-00599C?style=for-the-badge&logo=c&logoColor=white)
![Licencia](https://img.shields.io/badge/Licencia-MIT-green?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Terminado-brightgreen?style=for-the-badge)
![Compilador](https://img.shields.io/badge/Compilador-GCC-orange?style=for-the-badge)
![Colores](https://img.shields.io/badge/Consola-ANSI%20Colors-ff69b4?style=for-the-badge)

Repositorio académico en **C** sobre modularidad (paso por valor vs. punteros) y arreglos (1D, 2D, 3D), con programas de consola a color y escenarios tecnológicos: estaciones espaciales, drones autónomos y bases científicas. 🛰️🤖🌡️

</div>

---

<details open>
<summary><b>📌 Introducción</b></summary>
<br>

C es el lenguaje ideal para comprender a fondo la modularidad y los arreglos, precisamente porque **no oculta nada**: no hay recolector de basura, no hay listas dinámicas automáticas, no hay paso "por referencia" mágico. Todo se hace explícito mediante **punteros** y **arreglos de tamaño fijo**, lo que obliga a entender exactamente qué ocurre en memoria en cada operación.

Este repositorio combina ambos conceptos en programas ejecutables, documentados y comentados, con teoría redactada desde cero, salida en consola a color mediante secuencias ANSI, y un análisis crítico sobre las dificultades más comunes al programar en C con funciones y arreglos.

</details>

<details>
<summary><b>🎯 Objetivos</b></summary>
<br>

- Comprender la modularidad en C y la construcción de funciones con responsabilidades claras.
- Diferenciar el paso de parámetros **por valor** del paso **mediante punteros** (la forma que tiene C de simular "paso por referencia").
- Comprender la estructura, el uso y las limitaciones de los arreglos unidimensionales, bidimensionales y tridimensionales en C.
- Aplicar buenas prácticas de programación en C (nombres descriptivos, validación de límites, funciones pequeñas, cabeceras reutilizables).
- Reflexionar críticamente sobre los errores más comunes al trabajar con punteros y arreglos en un lenguaje de bajo nivel como C.

</details>

<details>
<summary><b>🧠 Competencias desarrolladas</b></summary>
<br>

| # | Competencia |
|:-:|---|
| 1 | Diseño modular de soluciones de software en un lenguaje de bajo nivel |
| 2 | Manejo de punteros y de estructuras de datos multidimensionales en memoria contigua |
| 3 | Pensamiento algorítmico y validación defensiva de índices y entradas |
| 4 | Redacción de documentación técnica siguiendo estándares profesionales |
| 5 | Depuración de errores de memoria y de límites de arreglos |
| 6 | Organización de proyectos en C para control de versiones (Git/GitHub) |

</details>

<details>
<summary><b>🛠️ Tecnologías utilizadas</b></summary>
<br>

| Tecnología | Uso |
|---|---|
| 🔵 C (estándar C11) | Lenguaje principal de desarrollo |
| ⚙️ GCC / Clang | Compilación de los programas |
| 🎨 Códigos ANSI | Colores y estilos en la salida de consola |
| 📝 Markdown + HTML | Documentación técnica |
| 🔧 Git / GitHub | Control de versiones y publicación |

> No se requieren librerías externas: todos los programas funcionan únicamente con la biblioteca estándar de C (`stdio.h`, `string.h`).

</details>


 <details>
<summary><b>📁 Ver explicación de cada carpeta</b></summary>

<br>

| 📂 Carpeta / Archivo | 📖 Contenido |
|:---------------------|:-------------|
| 🧩 `modularidad/` | Contiene la teoría sobre la modularidad en C, explicaciones del paso por valor y del paso por referencia mediante punteros, junto con ejemplos prácticos ambientados en una estación espacial. |
| 🌱 `arreglos/` | Incluye la teoría de los arreglos en C, sus características, ventajas, representación en memoria y ejemplos de arreglos unidimensionales, bidimensionales y tridimensionales, además de un ejercicio integrador aplicado a un invernadero espacial. |
| 💭 `analisis/` | Presenta una reflexión crítica sobre el aprendizaje de la unidad, las principales dificultades encontradas durante la aplicación de la modularidad y los arreglos, y los conocimientos adquiridos. |
 
</details>

---

 ## ⚙️ Cómo compilar y ejecutar los programas  ▶️ 

Para compilar los ejemplos de este portafolio se requiere un compilador compatible con el estándar **C11**, como **GCC**.

Todos los programas incluyen el archivo `estilo.h` mediante una ruta relativa (`../estilo.h`), por lo que deben compilarse desde la **raíz del repositorio**.

| Programa | Comando |
|:---------|:--------|
| ⚡ **Paso por valor** | `gcc -std=c11 modularidad/paso_por_valor.c -o paso_por_valor && ./paso_por_valor` |
| 🛡️ **Paso por referencia (punteros)** | `gcc -std=c11 modularidad/paso_por_referencia.c -o paso_por_referencia && ./paso_por_referencia` |
| 🌱 **Arreglo unidimensional (Invernadero Inteligente)** | `gcc -std=c11 arreglos/unidimensional.c -o unidimensional && ./unidimensional` |
| 🛰️ **Arreglo bidimensional (Centro de Control de Satélites)** | `gcc -std=c11 arreglos/bidimensional.c -o bidimensional && ./bidimensional` |
| 🧬 **Arreglo tridimensional (Laboratorio Genético Espacial)** | `gcc -std=c11 arreglos/tridimensional.c -o tridimensional && ./tridimensional` |
| 🚀 **Ejercicio Integrador (Invernadero Espacial)** | `gcc -std=c11 arreglos/ejercicio_integrador.c -o ejercicio_integrador && ./ejercicio_integrador` |

> 💡 **Nota:** Los colores ANSI se visualizan correctamente en terminales de **Linux**, **macOS**, **WSL** y **Windows Terminal**. En el símbolo del sistema clásico (`cmd.exe`) algunos colores podrían no mostrarse correctamente.

---

## ▶️ Ejecución de los programas

Cada programa está diseñado para ejecutarse de forma **independiente** y representa un ejemplo práctico de los contenidos estudiados durante la **Unidad 3: Modularidad y Arreglos**.

Una vez compilado el programa correspondiente, solo es necesario ejecutarlo y seguir las instrucciones que aparecen en la consola. Los ejemplos permiten ingresar datos cuando es necesario y muestran los resultados obtenidos para facilitar la comprensión de los conceptos desarrollados.
  
---

<details>
<summary><b>✅ Ver conclusiones generales</b></summary>
<br>

1. C obliga a hacer explícito lo que otros lenguajes esconden: el paso "por referencia" no existe como tal, sino que se logra pasando punteros.
2. Los arreglos en C son bloques de memoria contigua de tamaño fijo, lo que exige planificar su capacidad máxima y validar siempre los índices.
3. La modularidad en C se apoya en funciones pequeñas y cabeceras reutilizables (`estilo.h`).
4. Enriquecer la salida de consola con colores ANSI mejora la experiencia y comunica información más rápido (ej. un escudo bajo en rojo).
5. Comprender modularidad y arreglos en C sienta una base sólida para entender por qué otros lenguajes implementan estos conceptos de forma más "cómoda" pero menos transparente.

</details>

<div align="center">

---

**👤 Autoría**
Trabajo académico elaborado para la **Unidad 3: Modularidad y Arreglos**, con fines educativos, bajo licencia MIT (ver [`LICENSE`](./LICENSE)).

</div>
