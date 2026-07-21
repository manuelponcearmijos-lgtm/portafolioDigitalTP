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

#define TOTAL_SECTORES 3
#define ESCUDO_MAXIMO 100
#define ESCUDO_MINIMO 0

typedef struct {
    char nombre[20];
    int nivel;
} Sector;

// Inicializa los nombres y el nivel de los escudos
void estadoInicialEscudos(Sector escudos[])
{
    strcpy(escudos[0].nombre, "Frontal");
    strcpy(escudos[1].nombre, "Trasero");
    strcpy(escudos[2].nombre, "Lateral");

    // El usuario ingresa el nivel inicial de cada escudo
    printf("=== CONFIGURACION INICIAL DE ESCUDOS ===\n");

    for (int i = 0; i < TOTAL_SECTORES; i++)
    {
        printf("Ingrese el nivel inicial del escudo %s (0 - 100): ",
               escudos[i].nombre);
        scanf("%d", &escudos[i].nivel);

        if (escudos[i].nivel > ESCUDO_MAXIMO)
            escudos[i].nivel = ESCUDO_MAXIMO;

        if (escudos[i].nivel < ESCUDO_MINIMO)
            escudos[i].nivel = ESCUDO_MINIMO;
    }
}

// Muestra el estado de los escudos
void mostrarEscudos(Sector escudos[])
{
    printf("\n------ ESTADO DE LOS ESCUDOS ------\n");

    for (int i = 0; i < TOTAL_SECTORES; i++)
    {
        printf("%d. %-10s : %d%%\n",
               i + 1,
               escudos[i].nombre,
               escudos[i].nivel);
    }
}

// Paso por referencia mediante punteros
void aplicarImpacto(Sector *escudo, int danio)
{
    escudo->nivel -= danio;

    if (escudo->nivel < ESCUDO_MINIMO)
        escudo->nivel = ESCUDO_MINIMO;
}

int main()
{
    Sector escudos[TOTAL_SECTORES];

    int opcion;
    int sector;
    int danio;

    estadoInicialEscudos(escudos);

    do
    {
        printf("\n===============================\n");
        printf(" SISTEMA DE ESCUDOS ESPACIAL\n");
        printf("===============================\n");
        printf("1. Simular impacto\n");
        printf("2. Ver estado de escudos\n");
        printf("3. Salir\n");
        printf("Seleccione una opcion: ");
        scanf("%d", &opcion);

        switch(opcion)
        {
            case 1:

                mostrarEscudos(escudos);

                printf("\nSeleccione el sector (1-3): ");
                scanf("%d", &sector);

                if(sector >= 1 && sector <= TOTAL_SECTORES)
                {
                    printf("Ingrese el dano del impacto: ");
                    scanf("%d", &danio);

                    // Se envia la direccion del sector seleccionado
                    aplicarImpacto(&escudos[sector - 1], danio);

                    printf("\nImpacto aplicado correctamente.\n");
                }
                else
                {
                    printf("\nSector invalido.\n");
                }

                break;

            case 2:

                mostrarEscudos(escudos);
                break;

            case 3:

                printf("\nSaliendo del sistema...\n");
                break;

            default:

                printf("\nOpcion invalida.\n");
        }

    } while(opcion != 3);

    return 0;
}
```

[![Ejercicio 1](https://img.shields.io/badge/⚡%20Regresar%201%20-%20MODULARIDAD-28a745?style=for-the-badge)](Modularidad.md)
