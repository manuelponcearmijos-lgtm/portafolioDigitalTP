###  Paso Por Valor

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

static const char *MODULOS_DISPONIBLES[TOTAL_MODULOS] = {
    "navegacion", "soporte vital", "comunicaciones", "laboratorio"
};

/* Imprime en pantalla las opciones del sistema. */
static void mostrarMenu(void) {
    printf("\n");
    titulo(CIAN_B, "SISTEMA DE GESTION ENERGETICA - ESTACION ORBITAL");
    printf(CIAN "  1." RESET " Simular consumo de un modulo\n");
    printf(CIAN "  2." RESET " Ver historial de simulaciones\n");
    printf(CIAN "  3." RESET " Salir\n");
    linea(CIAN_B);
}

/* Valida que la opcion ingresada sea un entero entre 1 y 3. */
static int leerOpcion(void) {
    int opcion;
    char basura[100];

    while (1) {
        printf(AMARILLO_B "Seleccione una opcion: " RESET);
        if (scanf("%d", &opcion) == 1 && opcion >= 1 && opcion <= 3) {
            fgets(basura, sizeof(basura), stdin); /* limpia el buffer */
            return opcion;
        }
        fgets(basura, sizeof(basura), stdin);
        printf(ROJO_B "Opcion invalida. Intente nuevamente.\n" RESET);
    }
}

/* Solicita un numero y valida que sea positivo. */
static double validarNumero(const char *mensaje) {
    double valor;
    char basura[100];

    while (1) {
        printf("%s", mensaje);
        if (scanf("%lf", &valor) == 1 && valor >= 0) {
            fgets(basura, sizeof(basura), stdin);
            return valor;
        }
        fgets(basura, sizeof(basura), stdin);
        printf(ROJO_B "Debe ingresar un numero valido y no negativo.\n" RESET);
    }
}

/* Permite elegir un modulo valido de la estacion. */
static int elegirModulo(void) {
    int i;
    char entrada[50];

    printf(MAGENTA_B "Modulos disponibles: " RESET);
    for (i = 0; i < TOTAL_MODULOS; i++) {
        printf("%s%s", MODULOS_DISPONIBLES[i], (i < TOTAL_MODULOS - 1) ? ", " : "\n");
    }

    while (1) {
        printf("Ingrese el modulo que consumira energia: ");
        scanf("%49s", entrada);
        getchar();
        for (i = 0; i < TOTAL_MODULOS; i++) {
            if (strcmp(entrada, MODULOS_DISPONIBLES[i]) == 0) {
                return i;
            }
        }
        printf(ROJO_B "Modulo no reconocido. Intente nuevamente.\n" RESET);
    }
}

/*
 * Calcula la energia restante tras un consumo SIN alterar el valor
 * original recibido. "energiaDisponible" es una COPIA local del
 * double que existe en main() (paso por valor puro de C).
 */
static double simularConsumo(double energiaDisponible, double consumo) {
    energiaDisponible -= consumo; /* Esta resta solo afecta la copia local */
    if (energiaDisponible < 0) {
        energiaDisponible = 0;
    }
    return energiaDisponible;
}

/* Agrega el resultado de una simulacion al historial del programa. */
static void registrarSimulacion(double historial[], int *totalRegistros, double resultado) {
    if (*totalRegistros < MAX_HISTORIAL) {
        historial[*totalRegistros] = resultado;
        (*totalRegistros)++;
    }
}

/* Imprime todas las simulaciones registradas durante la sesion. */
static void mostrarHistorial(const double historial[], int totalRegistros) {
    int i;

    if (totalRegistros == 0) {
        printf(AMARILLO "Aun no se ha realizado ninguna simulacion.\n" RESET);
        return;
    }
    titulo(VERDE_B, "HISTORIAL DE SIMULACIONES (kWh RESTANTES)");
    for (i = 0; i < totalRegistros; i++) {
        printf(VERDE "  Simulacion %2d: %8.2f kWh\n" RESET, i + 1, historial[i]);
    }
}

int main(void) {
    double energiaActual = 1500.0;   /* Energia REAL de la estacion */
    double historial[MAX_HISTORIAL];
    int totalRegistros = 0;
    int opcion;

    while (1) {
        mostrarMenu();
        opcion = leerOpcion();

        if (opcion == 1) {
            int indiceModulo = elegirModulo();
            char mensaje[100];
            double consumo, resultadoSimulado;

            sprintf(mensaje, AMARILLO_B "Ingrese el consumo del modulo de %s (kWh): " RESET,
                    MODULOS_DISPONIBLES[indiceModulo]);
            consumo = validarNumero(mensaje);

            /* energiaActual se pasa POR VALOR: la funcion recibe una copia */
            resultadoSimulado = simularConsumo(energiaActual, consumo);
            registrarSimulacion(historial, &totalRegistros, resultadoSimulado);

            printf("\n" VERDE_B "Energia simulada restante tras el consumo: %.2f kWh\n" RESET, resultadoSimulado);
            printf(CIAN_B "Energia REAL de la estacion (sin cambios):  %.2f kWh\n" RESET, energiaActual);

        } else if (opcion == 2) {
            mostrarHistorial(historial, totalRegistros);

        } else if (opcion == 3) {
            printf(MAGENTA_B "\nCerrando sistema de gestion energetica...\n" RESET);
            break;
        }
    }

    return 0;
}
