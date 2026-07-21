 <div align="center">

# 🌌 Unidad 3 - Arreglos en C

### 🚀 Sistema Inteligente de Gestión de una Estación Espacial

<img src="https://img.shields.io/badge/Lenguaje-C-00599C?style=for-the-badge&logo=c&logoColor=white">
<img src="https://img.shields.io/badge/Unidad-3-4CAF50?style=for-the-badge">
<img src="https://img.shields.io/badge/Tema-Arreglos-FF9800?style=for-the-badge">
<img src="https://img.shields.io/badge/Estado-Completado-success?style=for-the-badge">

*"Los arreglos permiten organizar y manipular grandes cantidades de información de forma eficiente, siendo una de las estructuras de datos fundamentales en la programación."*

</div>

---

# 📑 Contenido

- 🚀 Introducción
- 📖 ¿Qué es un arreglo?
- ⭐ Características
- ✅ Ventajas y desventajas
- 🧠 Representación en memoria
- 🌱 Arreglo Unidimensional
- 💻 Ejemplo práctico
- 📊 Análisis del programa

---

# 🚀 Introducción

Los **arreglos (arrays)** son estructuras de datos fundamentales en el lenguaje **C**, utilizadas para almacenar múltiples elementos del mismo tipo de dato bajo un único nombre de variable.

Cada elemento ocupa una posición consecutiva en memoria y puede accederse mediante un **índice**, el cual comienza desde **0**.

Gracias a esta organización, los arreglos facilitan el procesamiento de grandes cantidades de información utilizando estructuras repetitivas como `for` y `while`, haciendo que los programas sean más organizados, eficientes y fáciles de mantener.

---

# 📖 ¿Qué es un arreglo?

Un **arreglo** es una colección de elementos del mismo tipo almacenados en posiciones contiguas de memoria.

Cada elemento posee un índice que permite acceder directamente a él.

### Ejemplo

```c
int numeros[5] = {10,20,30,40,50};
```

En este caso se almacenan cinco números enteros.

---

# 🧠 Representación en memoria

```text
              ARREGLO "numeros"

Índice

   0       1       2       3       4

┌──────┬──────┬──────┬──────┬──────┐
│  10  │  20  │  30  │  40  │  50  │
└──────┴──────┴──────┴──────┴──────┘

numeros[0]
numeros[1]
numeros[2]
...
```

Cada posición almacena un dato y puede accederse mediante su índice correspondiente.

---

# ⭐ Características

- Todos los elementos son del **mismo tipo de dato**.
- Los elementos se almacenan de forma **contigua en memoria**.
- El primer elemento siempre tiene índice **0**.
- El tamaño del arreglo se define al momento de declararlo.
- Permiten recorrer la información mediante ciclos.

---

# ✅ Ventajas

- ✔️ Organizan grandes cantidades de información.
- ✔️ Reducen la cantidad de variables necesarias.
- ✔️ Facilitan búsquedas y recorridos.
- ✔️ Mejoran la legibilidad del código.
- ✔️ Permiten trabajar con estructuras de datos más complejas.

---

# ⚠️ Desventajas

- ❌ Todos los elementos deben ser del mismo tipo.
- ❌ El tamaño normalmente es fijo.
- ❌ Acceder a un índice inexistente produce un comportamiento indefinido.
- ❌ No pueden crecer dinámicamente sin utilizar memoria dinámica.

---

<div align="center">

# 🌱 Arreglo Unidimensional

## Invernadero Inteligente de la Estación Espacial

</div>

---

## 🌍 Contexto

La estación espacial cuenta con un **invernadero inteligente** donde se cultivan alimentos para la tripulación.

Cada cultivo posee un sensor que registra el **porcentaje de humedad** del suelo.

El sistema almacenará la humedad de cinco cultivos utilizando un **arreglo unidimensional**, permitiendo mostrar posteriormente toda la información registrada.

---

## 🧠 ¿Qué es un arreglo unidimensional?

Un arreglo unidimensional, también conocido como **vector**, almacena los datos en una única dimensión, es decir, en una sola fila.

Cada elemento se identifica mediante un único índice.

---

## 📊 Representación

```text
Cultivos

                 Humedad (%)

            68    75    82    60    91

Índice

             0     1     2     3     4

        ┌────┬────┬────┬────┬────┐
        │68% │75% │82% │60% │91% │
        └────┴────┴────┴────┴────┘
```

---

## 💻 Código Fuente

```c
 #include <stdio.h>

#define CULTIVOS 5

int main() {

    float humedad[CULTIVOS];

    printf("=====================================\n");
    printf("      INVERNADERO INTELIGENTE\n");
    printf("=====================================\n\n");

    // Ingreso de datos con validación
    for (int i = 0; i < CULTIVOS; i++) {

        do {
            printf("Ingrese la humedad del cultivo %d (0 - 100%%): ", i + 1);
            scanf("%f", &humedad[i]);

            if (humedad[i] < 0 || humedad[i] > 100) {
                printf("Error: La humedad debe estar entre 0 y 100%%.\n\n");
            }

        } while (humedad[i] < 0 || humedad[i] > 100);
    }

    printf("\n========== REPORTE ==========\n\n");

    // Encabezado
    printf("Cultivos : ");
    for (int i = 0; i < CULTIVOS; i++) {
        printf("C%-2d\t", i + 1);
    }

    printf("\n");

    // Valores de humedad
    printf("Humedad : ");
    for (int i = 0; i < CULTIVOS; i++) {
        printf("%.1f%%\t", humedad[i]);
    }

    printf("\n");

    return 0;
}
```

---

## 📊 Análisis del programa

En este ejemplo se declara un arreglo llamado `humedad` con capacidad para almacenar los datos de cinco cultivos.

Mediante un ciclo `for`, el usuario ingresa el porcentaje de humedad de cada cultivo. Posteriormente, otro ciclo recorre el arreglo para mostrar toda la información registrada.

Este tipo de arreglo resulta ideal cuando se necesita almacenar una lista de elementos relacionados, como temperaturas, calificaciones, edades, ventas o, en este caso, la humedad de los cultivos de un invernadero inteligente.

---

> 💡 **Dato importante:** En un arreglo unidimensional solo se necesita **un índice** para acceder a cada elemento. Por ejemplo, `humedad[2]` representa el tercer cultivo almacenado, ya que los índices comienzan en **0**.

---

<div align="center">

# 🛰️ Arreglo Bidimensional

## Centro de Control de Satélites

</div>

---

## 🌍 Contexto

La estación espacial administra una red de **cuatro satélites de comunicación**. Cada satélite transmite la intensidad de su señal durante **tres turnos del día**:

- 🌅 Mañana
- ☀️ Tarde
- 🌙 Noche

La información se almacena en un **arreglo bidimensional (matriz)**, donde cada fila representa un satélite y cada columna un turno.

---

## 🧠 ¿Qué es un arreglo bidimensional?

Un arreglo bidimensional, también conocido como **matriz**, organiza los datos en **filas y columnas**.

Para acceder a un elemento se utilizan **dos índices**:

```c
matriz[fila][columna]
```

---

## 📊 Representación

```text
              Turnos

             M     T     N

           ┌────┬────┬────┐
SAT-1      │ 95 │ 93 │ 90 │
           ├────┼────┼────┤
SAT-2      │ 88 │ 91 │ 86 │
           ├────┼────┼────┤
SAT-3      │ 97 │ 96 │ 94 │
           ├────┼────┼────┤
SAT-4      │ 82 │ 84 │ 81 │
           └────┴────┴────┘

          Filas = Satélites
          Columnas = Turnos
```

---

## 💻 Código Fuente

```c
#include <stdio.h>

#define SATELITES 4
#define TURNOS 3

int main() {

    int senal[SATELITES][TURNOS];

    printf("=====================================\n");
    printf(" CENTRO DE CONTROL DE SATELITES\n");
    printf("=====================================\n\n");

    for(int i=0;i<SATELITES;i++){

        printf("\nSatelite %d\n",i+1);

        for(int j=0;j<TURNOS;j++){

            printf("Turno %d: ",j+1);
            scanf("%d",&senal[i][j]);

        }

    }

    printf("\n=========== REPORTE ===========\n\n");

    for(int i=0;i<SATELITES;i++){

        printf("SAT-%d -> ",i+1);

        for(int j=0;j<TURNOS;j++){

            printf("%3d ",senal[i][j]);

        }

        printf("\n");

    }

    return 0;

}
```

---


## 📊 Análisis

Este programa almacena la intensidad de la señal de cuatro satélites durante tres turnos del día.

El primer índice identifica el satélite y el segundo el turno correspondiente, permitiendo organizar la información de forma tabular y acceder rápidamente a cualquier dato mediante dos índices.

---

<div align="center">

# 🧬 Arreglo Tridimensional

## Laboratorio Genético Espacial

</div>

---

## 🌍 Contexto

El laboratorio científico analiza muestras biológicas recolectadas en distintos planetas.

Los datos registrados corresponden a:

- 📅 Día del análisis
- 🧪 Laboratorio
- 🔬 Muestra

Debido a estas tres variables, la información se almacena mediante un **arreglo tridimensional**.

---

## 🧠 ¿Qué es un arreglo tridimensional?

Un arreglo tridimensional almacena información utilizando **tres índices**.

Su sintaxis general es:

```c
datos[dia][laboratorio][muestra]
```

---

## 📊 Representación

```text
analisis[dia][laboratorio][muestra]

                Día

          ┌────────────┐
          │Laboratorio │
          │            │
          │ M1   M2    │
          └────────────┘

Cada dato necesita tres índices para ser localizado.
```

---

## 💻 Código Fuente

```c
 #include <stdio.h>

#define CAPAS 2
#define FILAS 3
#define COLUMNAS 2

int main() {

    int analisis[CAPAS][FILAS][COLUMNAS];

    printf("=========================================\n");
    printf("   SISTEMA DE ANALISIS DE LABORATORIO\n");
    printf("=========================================\n\n");

    // Ingreso de datos
    for (int c = 0; c < CAPAS; c++) {

        printf("\n========== CAPA %d ==========\n", c + 1);

        for (int f = 0; f < FILAS; f++) {

            for (int col = 0; col < COLUMNAS; col++) {

                do {

                    printf("Ingrese el dato [%d][%d][%d]: ",
                           c, f, col);

                    scanf("%d", &analisis[c][f][col]);

                    if (analisis[c][f][col] < 0) {
                        printf("Error: no se permiten numeros negativos.\n");
                    }

                } while (analisis[c][f][col] < 0);

            }

        }

    }

    printf("\n=========== RESULTADOS ===========\n");

    // Mostrar la matriz tridimensional
    for (int c = 0; c < CAPAS; c++) {

        printf("\nCAPA %d\n", c + 1);

        for (int f = 0; f < FILAS; f++) {

            for (int col = 0; col < COLUMNAS; col++) {

                printf("%4d", analisis[c][f][col]);

            }

            printf("\n");
        }

    }

    return 0;
}
```

---

## 📊 Análisis

El arreglo tridimensional organiza la información utilizando tres dimensiones: día, laboratorio y muestra.

Este tipo de estructura resulta útil cuando se requiere almacenar información compleja relacionada con tiempo, ubicación o diferentes categorías.

---

<div align="center">

 
---

# 📊 Comparación de los tipos de arreglos

| Tipo | Dimensiones | Índices | Ejemplo |
|:-----|:-----------:|:-------:|:--------|
| 🌱 Unidimensional | 1 | 1 | Humedad de cultivos |
| 🛰️ Bidimensional | 2 | 2 | Señal de satélites |
| 🧬 Tridimensional | 3 | 3 | Muestras genéticas |

---

# 💡 Aplicaciones en la vida real

| Tipo | Aplicaciones |
|------|--------------|
| 🌱 Vector | Calificaciones, edades, temperaturas, ventas, inventarios. |
| 🛰️ Matriz | Imágenes, mapas, tableros, horarios, videojuegos. |
| 🧬 Tridimensional | Simulaciones, medicina, inteligencia artificial, videojuegos 3D, investigación científica. |

---

# ✅ Conclusión

Los arreglos constituyen una de las estructuras de datos más importantes del lenguaje C, ya que permiten almacenar y organizar múltiples elementos de manera eficiente. Los arreglos unidimensionales facilitan el manejo de listas, los bidimensionales permiten representar información en forma de tablas o matrices y los tridimensionales hacen posible organizar datos más complejos mediante tres índices. Su dominio es fundamental para desarrollar algoritmos más estructurados y constituye la base para comprender estructuras de datos de mayor complejidad utilizadas en la programación moderna.

[![Acceder a Unidad 3](https://img.shields.io/badge/ACCEDER%20A%20LA%20UNIDAD_3-CLICK%20AQUÍ-7434eb?style=for-the-badge&logo=github&logoColor=white)](./Unidad_3.md)

---

<div align="center">

## ⭐ Fin del Tema: Arreglos en C

**Unidad 3 – Modularidad y Arreglos**

🛰️ *Portafolio Digital de Programación en C*

</div>
