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

double simularConsumo(double energia, double consumo)
{
    // Se resta el consumo únicamente a la copia local
    energia = energia - consumo;

    // Si la energía resulta negativa,
    // se establece en cero.
    if (energia < 0)
    {
        energia = 0;
    }

    // Se devuelve la copia modificada
    return energia;
}

int main()
{
    // Variables del programa
    double energiaActual;
    double consumo;
    double energiaSimulada;

    // Título del programa
    printf("===========================================\n");
    printf(" SISTEMA INTELIGENTE DE GESTION ENERGETICA\n");
    printf("      Paso de Parametros por Valor\n");
    printf("===========================================\n\n");

    // El usuario ingresa la energía disponible
    printf("Ingrese la energia actual (kWh): ");
    scanf("%lf", &energiaActual);

    // El usuario ingresa el consumo del módulo
    printf("Ingrese el consumo del modulo (kWh): ");
    scanf("%lf", &consumo);

    // Se muestra la energía original antes de llamar la función
    printf("\n--------- ANTES DE LA SIMULACION ---------\n");
    printf("Energia REAL: %.2f kWh\n", energiaActual);

    // Se envía una COPIA de energiaActual a la función.
    // La variable original NO cambia.
    energiaSimulada = simularConsumo(energiaActual, consumo);

    // Se muestran los resultados obtenidos
    printf("\n--------- DESPUES DE LA SIMULACION ---------\n");
    printf("Energia simulada: %.2f kWh\n", energiaSimulada);

    // Esta variable conserva su valor inicial,
    // demostrando el paso por valor.
    printf("Energia REAL: %.2f kWh\n", energiaActual);

    // Explicación final del resultado
    printf("\nObservacion:\n");
    printf("La energia REAL no cambio porque la funcion\n");
    printf("recibio una COPIA del dato (paso por valor).\n");

    return 0;
}
 ```
 [![Ejercicio 1](https://img.shields.io/badge/⚡%20Regresar%201%20-%20MODULARIDAD-28a745?style=for-the-badge)](Modularidad.md)

