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
 #include <stdio.h>

// Función que simula el consumo de energía
// Recibe una COPIA del valor original (paso por valor)
double simularConsumo(double energia, double consumo) {
    energia -= consumo;      // Se modifica únicamente la copia local

    if (energia < 0) {
        energia = 0;         // Evita valores negativos
    }

    return energia;          // Retorna la copia modificada
}

int main() {
    double energiaActual = 500.0;   // Energía REAL del sistema
    double consumo = 120.0;         // Consumo del módulo

    printf("Energia REAL antes de la simulacion: %.2f kWh\n", energiaActual);

    // Se envía una copia de energiaActual
    double energiaSimulada = simularConsumo(energiaActual, consumo);

    printf("Energia simulada restante: %.2f kWh\n", energiaSimulada);
    printf("Energia REAL despues de la simulacion: %.2f kWh\n", energiaActual);

    return 0;
}
 ```
 [![Ejercicio 1](https://img.shields.io/badge/⚡%20Presentación%201%20-%20MODULARIDAD-28a745?style=for-the-badge)](Modularidad.md)

