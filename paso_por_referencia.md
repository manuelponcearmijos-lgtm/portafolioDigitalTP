<!-- ========================================================= -->
<!-- 🛡️ PASO POR REFERENCIA EN C - SISTEMA DE ESCUDOS -->
<!-- ========================================================= -->

<h1 align="center">🛡️ Paso por Referencia en C</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Lenguaje-C-00599C?style=for-the-badge&logo=c&logoColor=white">
  <img src="https://img.shields.io/badge/Tema-Punteros-8A2BE2?style=for-the-badge">
  <img src="https://img.shields.io/badge/Sistema-Escudos%20Espaciales-FF4500?style=for-the-badge">
</p>

<hr>

## 🚀 Introducción

Este programa forma parte del Sistema de Escudos de una Estación Espacial y demuestra cómo simular el paso por referencia en C mediante punteros.

En C no existe un paso por referencia nativo como en otros lenguajes; en su lugar, se simula enviando la dirección de memoria de una variable mediante un puntero.

La función recibe una copia del puntero, pero esa copia sigue apuntando a la misma dirección de memoria que la variable original. Por ello, cualquier modificación realizada a través del puntero se refleja directamente en la variable original.

💡 **Aunque en C todos los parámetros se pasan por valor, al pasar un puntero se obtiene el mismo efecto que un paso por referencia.**

---

## 🧠 Concepto Clave

<table>
  <tr>
    <th>Concepto</th>
    <th>Descripción</th>
  </tr>
  <tr>
    <td><b>Puntero</b></td>
    <td>Variable que almacena una dirección de memoria.</td>
  </tr>
  <tr>
    <td><b>Paso por referencia</b></td>
    <td>Se envía la dirección de la variable original (<code>&variable</code>).</td>
  </tr>
  <tr>
    <td><b>Efecto</b></td>
    <td>Las funciones pueden modificar directamente la variable real.</td>
  </tr>
  <tr>
    <td><b>Ejemplo</b></td>
    <td><code>aplicarImpacto(&escudos[indice], danio)</code></td>
  </tr>
</table>

---

## 🧩 Código Fuente Completo

```c
#include <stdio.h>
#include <string.h>
#include "../estilo.h"

#define TOTAL_SECTORES  3
#define ESCUDO_MAXIMO   100
#define ESCUDO_MINIMO   0

typedef struct {
    char nombre[20];
    int  nivel;
} Sector;

// Crea el estado inicial de los tres sectores de escudos. 
static void estadoInicialEscudos(Sector escudos[]) {
    strcpy(escudos[0].nombre, "frontal");
    strcpy(escudos[1].nombre, "trasero");
    strcpy(escudos[2].nombre, "lateral");
    for (int i = 0; i < TOTAL_SECTORES; i++) {
        escudos[i].nivel = ESCUDO_MAXIMO;
    }
}

static void mostrarMenu(void) {
    printf("\n");
    titulo(AZUL_B, "SISTEMA DE ESCUDOS - ESTACION ORBITAL");
    printf(AZUL "  1." RESET " Simular impacto en un sector\n");
    printf(AZUL "  2." RESET " Ver
```

[![Ejercicio 1](https://img.shields.io/badge/⚡%20Regresar%201%20-%20MODULARIDAD-28a745?style=for-the-badge)](Modularidad.md)
