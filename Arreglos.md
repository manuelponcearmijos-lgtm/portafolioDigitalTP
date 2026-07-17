 # 🌌 Arreglos en C
>
> **Sistema Inteligente de Gestión de una Estación Espacial**

---

<div align="center">

# 🛰️ Arreglos (Arrays)

<img src="https://img.shields.io/badge/Lenguaje-C-blue?style=for-the-badge&logo=c" />
<img src="https://img.shields.io/badge/Unidad-3-success?style=for-the-badge" />
<img src="https://img.shields.io/badge/Tema-Arreglos-orange?style=for-the-badge" />

</div>

---

## 🚀 ¿Qué es un arreglo?

Un **arreglo (array)** es una estructura de datos que permite almacenar **varios elementos del mismo tipo** utilizando una única variable.

Cada elemento ocupa una posición consecutiva en memoria y se identifica mediante un **índice**, que en C siempre comienza desde **0**.

---

<div align="center">

```text
Índice

0        1        2        3        4
┌──────┬──────┬──────┬──────┬──────┐
│ 100  │ 200  │ 300  │ 400  │ 500  │
└──────┴──────┴──────┴──────┴──────┘

nombre[0] nombre[1] nombre[2] ...
```

</div>

---

## 🎯 ¿Por qué utilizar arreglos?

Los arreglos permiten:

- ✅ Almacenar grandes cantidades de datos.
- ✅ Evitar declarar muchas variables.
- ✅ Facilitar búsquedas y recorridos.
- ✅ Procesar información mediante ciclos.
- ✅ Representar tablas, matrices e incluso mapas.

---

# 📚 Tipos de arreglos

---

# 🔹 1. Arreglo Unidimensional (Vector)

Es el tipo de arreglo más sencillo.

Los datos se almacenan en una única fila.

<div align="center">

```text
┌────┬────┬────┬────┬────┐
│120 │135 │110 │140 │128 │
└────┴────┴────┴────┴────┘
  0    1    2    3    4
```

</div>

---

## 🌍 Aplicación

En una estación espacial se registra la energía consumida por cinco módulos durante el día.

---

## 💻 Ejemplo

```c
#include <stdio.h>

int main() {

    int energia[5] = {120,135,110,140,128};

    printf("Consumo de energia:\n\n");

    for(int i=0;i<5;i++){
        printf("Modulo %d: %d kWh\n", i+1, energia[i]);
    }

    return 0;
}
```

---

## ✅ Salida

```text
Modulo 1: 120 kWh
Modulo 2: 135 kWh
Modulo 3: 110 kWh
Modulo 4: 140 kWh
Modulo 5: 128 kWh
```

---

# 🔹 2. Arreglo Bidimensional (Matriz)

Una matriz organiza la información en **filas y columnas**.

<div align="center">

```text
        Columnas

        0     1     2

      ┌────┬────┬────┐
Fila0 │ 12 │ 15 │ 20 │
      ├────┼────┼────┤
Fila1 │ 30 │ 18 │ 25 │
      ├────┼────┼────┤
Fila2 │ 40 │ 22 │ 35 │
      └────┴────┴────┘
```

</div>

---

## 🌍 Aplicación

Cada fila representa un **sector de la estación**, mientras que cada columna representa la energía consumida durante tres turnos del día.

---

## 💻 Ejemplo

```c
#include <stdio.h>

int main(){

    int energia[3][3]={
        {12,15,20},
        {30,18,25},
        {40,22,35}
    };

    printf("Consumo diario\n\n");

    for(int i=0;i<3;i++){

        for(int j=0;j<3;j++){

            printf("%3d ",energia[i][j]);

        }

        printf("\n");

    }

    return 0;

}
```

---

## ✅ Salida

```text
12 15 20
30 18 25
40 22 35
```

---

# 🔹 3. Arreglo Tridimensional

Almacena datos utilizando **tres dimensiones**.

Generalmente representan:

- Tiempo
- Espacio
- Capas
- Pisos
- Sensores
- Días

---

<div align="center">

```text
           Día

        ┌────────────┐
Piso 1  │ Sensor[][] │
        └────────────┘

        ┌────────────┐
Piso 2  │ Sensor[][] │
        └────────────┘
```

</div>

---

## 🌍 Aplicación

Una estación espacial registra la temperatura de varios sensores durante distintos días.

---

## 💻 Ejemplo

```c
#include <stdio.h>

int main(){

    int temperatura[2][2][2]={
        {
            {20,22},
            {21,23}
        },
        {
            {24,26},
            {25,27}
        }
    };

    printf("Temperaturas registradas\n\n");

    for(int i=0;i<2;i++){

        printf("Dia %d\n",i+1);

        for(int j=0;j<2;j++){

            for(int k=0;k<2;k++){

                printf("%d ",temperatura[i][j][k]);

            }

            printf("\n");

        }

        printf("\n");

    }

    return 0;

}
```

---

## ✅ Salida

```text
Dia 1
20 22
21 23

Dia 2
24 26
25 27
```

---

# ⚙️ Comparación

| Característica | Unidimensional | Bidimensional | Tridimensional |
|:--------------|:--------------:|:-------------:|:--------------:|
| Dimensiones | 1 | 2 | 3 |
| Organización | Lista | Filas y columnas | Capas |
| Ejemplo | Notas | Matriz | Sensores |
| Índices | 1 | 2 | 3 |

---

# 🚀 Ejercicio Propuesto
## 🌌 Sistema Inteligente de Monitoreo de Oxígeno

<div align="center">

```text
╔══════════════════════════════════════╗
║      CENTRO DE CONTROL ESPACIAL      ║
╚══════════════════════════════════════╝

Módulos:

🟦 Hábitat
🟩 Laboratorio
🟨 Invernadero
🟥 Ingeniería
🟪 Comunicaciones
```

</div>

---

## 📖 Descripción

La estación espacial cuenta con **cinco módulos**.

Cada uno registra el nivel de oxígeno disponible (%).

El operador debe:

- ingresar el porcentaje de oxígeno de cada módulo;
- mostrar todos los niveles registrados;
- calcular el promedio;
- identificar el módulo con el mayor nivel de oxígeno;
- identificar el módulo con el menor nivel de oxígeno;
- mostrar una alerta si algún módulo tiene menos del **70 %** de oxígeno.

---

## 💻 Código

```c
#include <stdio.h>

#define MODULOS 5

int main() {

    float oxigeno[MODULOS];
    float suma = 0;
    int mayor = 0;
    int menor = 0;

    printf("=====================================\n");
    printf(" SISTEMA DE MONITOREO DE OXIGENO\n");
    printf("=====================================\n\n");

    for (int i = 0; i < MODULOS; i++) {
        printf("Oxigeno del modulo %d (%%): ", i + 1);
        scanf("%f", &oxigeno[i]);

        suma += oxigeno[i];

        if (oxigeno[i] > oxigeno[mayor])
            mayor = i;

        if (oxigeno[i] < oxigeno[menor])
            menor = i;
    }

    printf("\n========== REPORTE ==========\n");

    for (int i = 0; i < MODULOS; i++) {
        printf("Modulo %d -> %.1f%%\n", i + 1, oxigeno[i]);

        if (oxigeno[i] < 70)
            printf("⚠ ALERTA: Oxigeno critico\n");
    }

    printf("\nPromedio: %.2f%%\n", suma / MODULOS);

    printf("Mayor nivel: Modulo %d (%.1f%%)\n",
           mayor + 1,
           oxigeno[mayor]);

    printf("Menor nivel: Modulo %d (%.1f%%)\n",
           menor + 1,
           oxigeno[menor]);

    return 0;
}
```

---

# 🎯 ¿Qué se practica?

- ✅ Declaración de arreglos.
- ✅ Recorrido con `for`.
- ✅ Entrada y salida de datos.
- ✅ Búsqueda del mayor y menor.
- ✅ Acumuladores.
- ✅ Promedio.
- ✅ Condicionales.
- ✅ Uso de índices.
- ✅ Resolución de un problema aplicado a un contexto real.

---

<div align="center">

# ⭐ Conclusión

Los arreglos son una de las estructuras de datos fundamentales del lenguaje C. Permiten almacenar y manipular grandes cantidades de información de forma organizada y eficiente. Comprender el uso de arreglos unidimensionales, bidimensionales y tridimensionales constituye la base para desarrollar estructuras de datos más complejas y aplicaciones de mayor escala.

</div>

---

<div align="center">

**🛰️ Portafolio Digital – Unidad 3: Modularidad y Arreglos**  
**Ingeniería en Computación**

</div>
