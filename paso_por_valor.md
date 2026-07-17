 <!-- ========================================================= -->
<!-- ⚡ SISTEMA INTELIGENTE DE GESTIÓN ENERGÉTICA - PASO POR VALOR -->
<!-- ========================================================= -->

<h1 align="center">⚙️ Paso por Valor en C</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Lenguaje-C-00599C?style=for-the-badge&logo=c&logoColor=white">
  <img src="https://img.shields.io/badge/Tema-Paso%20por%20Valor-FF4500?style=for-the-badge">
  <img src="https://img.shields.io/badge/Sistema-Gestión%20Energética-1E90FF?style=for-the-badge">
</p>

<hr>

## 🚀 Introducción

Este programa forma parte del **Sistema Inteligente de Gestión Energética de una Estación Espacial**, y demuestra el **paso de parámetros por valor en C**.

En C, **todos los parámetros se pasan por valor**:  
la función recibe **una copia del dato original**, por lo que cualquier modificación dentro de la función **no afecta** la variable real que vive en `main()`.

> 💡 Si no se usa un puntero, la función solo trabaja con su copia local.

---

## 🧠 Concepto Clave

<table>
  <tr>
    <th>Concepto</th>
    <th>Descripción</th>
  </tr>
  <tr>
    <td><b>Paso por valor</b></td>
    <td>La función recibe una copia del dato original.</td>
  </tr>
  <tr>
    <td><b>Efecto</b></td>
    <td>Las modificaciones internas no afectan la variable real.</td>
  </tr>
  <tr>
    <td><b>Ejemplo</b></td>
    <td><code>simularConsumo(energiaActual, consumo)</code> no altera <code>energiaActual</code>.</td>
  </tr>
  <tr>
    <td><b>Comparación</b></td>
    <td>El paso por referencia usa punteros (<code>&variable</code>).</td>
  </tr>
</table>

---

## 🧩 Código Fuente Completo

```c
/*
 * paso_por_valor.c
 * --------------------------------------------------------------------
 * Sistema Inteligente de Gestión Energética de una Estación Espacial
 * --------------------------------------------------------------------
 * Este programa demuestra el PASO DE PARÁMETROS POR VALOR en C.
 *
 * En C, TODOS los parámetros se pasan por valor: la función recibe una
 * COPIA del dato original. Cuando pasamos un "double" (como la energía
 * disponible en la estación) directamente -sin usar un puntero-, la
 * función solo puede modificar su copia local; el dato original que
 * vive en main() permanece intacto sin importar qué se haga dentro
 * de la función.
 */

#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include "../estilo.h"

#define MAX_HISTORIAL   50
#define TOTAL_MODULOS   4

static const char *MODULOS_DISPONIBLES[TOTAL_MOD
