 /*
 * paso_por_referencia.c
 * --------------------------------------------------------------------
 * Sistema de Escudos de una Estacion Espacial
 * --------------------------------------------------------------------
 * Este programa demuestra el PASO DE PARAMETROS POR REFERENCIA en C,
 * simulado mediante PUNTEROS.
 *
 * En C no existe un paso "por referencia" nativo como en otros lenguajes;
 * se simula pasando la DIRECCION de memoria de una variable (un puntero).
 * La funcion recibe una copia del puntero, pero esa copia sigue
 * apuntando exactamente al mismo lugar de memoria que la variable
 * original, por lo que cualquier modificacion realizada a traves de
 * "*puntero" SI se refleja en la variable original de main().
 */

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

/* Crea el estado inicial de los tres sectores de escudos. */
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
    printf(AZUL "  2." RESET " Ver estado actual de los escudos\n");
    printf(AZUL "  3." RESET " Reforzar un sector\n");
    printf(AZUL "  4." RESET " Salir\n");
    linea(AZUL_B);
}

static int leerOpcion(void) {
    int opcion;
    char basura[100];

    while (1) {
        printf(AMARILLO_B "Seleccione una opcion: " RESET);
        if (scanf("%d", &opcion) == 1 && opcion >= 1 && opcion <= 4) {
            fgets(basura, sizeof(basura), stdin);
            return opcion;
        }
        fgets(basura, sizeof(basura), stdin);
        printf(ROJO_B "Opcion invalida. Intente nuevamente.\n" RESET);
    }
}

/* Retorna el indice del sector cuyo nombre coincide, o -1 si no existe. */
static int buscarSector(const Sector escudos[], const char *nombre) {
    for (int i = 0; i < TOTAL_SECTORES; i++) {
        if (strcmp(escudos[i].nombre, nombre) == 0) {
            return i;
        }
    }
    return -1;
}

/* Solicita al usuario un sector valido dentro del arreglo de escudos. */
static int elegirSector(const Sector escudos[]) {
    char entrada[20];
    int indice;

    printf(MAGENTA_B "Sectores disponibles: " RESET);
    for (int i = 0; i < TOTAL_SECTORES; i++) {
        printf("%s%s", escudos[i].nombre, (i < TOTAL_SECTORES - 1) ? ", " : "\n");
    }

    while (1) {
        printf("Ingrese el sector: ");
        scanf("%19s", entrada);
        getchar();
        indice = buscarSector(escudos, entrada);
        if (indice != -1) {
            return indice;
        }
        printf(ROJO_B "Sector no reconocido. Intente nuevamente.\n" RESET);
    }
}

static int validarEnteroPositivo(const char *mensaje) {
    int valor;
    char basura[100];

    while (1) {
        printf("%s", mensaje);
        if (scanf("%d", &valor) == 1 && valor >= 0) {
            fgets(basura, sizeof(basura), stdin);
            return valor;
        }
        fgets(basura, sizeof(basura), stdin);
        printf(ROJO_B "Debe ingresar un entero valido y no negativo.\n" RESET);
    }
}

/*
 * Modifica DIRECTAMENTE el nivel del sector apuntado por "sector".
 * Como recibe un PUNTERO (Sector *), lo que hay dentro de "*sector"
 * es el mismo espacio de memoria que existe en el arreglo original
 * de main(): el cambio persiste fuera de la funcion.
 */
static void aplicarImpacto(Sector *sector, int danio) {
    sector->nivel -= danio;
    if (sector->nivel < ESCUDO_MINIMO) {
        sector->nivel = ESCUDO_MINIMO;
    }
}

/* Aumenta el nivel de un sector sin superar el maximo permitido. */
static void reforzarSector(Sector *sector, int refuerzo) {
    sector->nivel += refuerzo;
    if (sector->nivel > ESCUDO_MAXIMO) {
        sector->nivel = ESCUDO_MAXIMO;
    }
}

/* Elige el color segun el nivel de integridad restante del sector. */
static const char *colorSegunNivel(int nivel) {
    if (nivel >= 70) return VERDE_B;
    if (nivel >= 30) return AMARILLO_B;
    return ROJO_B;
}

static void mostrarEstado(const Sector escudos[]) {
    titulo(CIAN_B, "ESTADO ACTUAL DE LOS ESCUDOS");
    for (int i = 0; i < TOTAL_SECTORES; i++) {
        const char *color = colorSegunNivel(escudos[i].nivel);
        printf("  %-10s %s[", escudos[i].nombre, color);
        int barras = escudos[i].nivel / 5;
        for (int b = 0; b < 20; b++) {
            printf("%s", (b < barras) ? "#" : "-");
        }
        printf("]%s %3d/%d\n", RESET, escudos[i].nivel, ESCUDO_MAXIMO);
    }
}

int main(void) {
    Sector escudos[TOTAL_SECTORES];
    int opcion;

    estadoInicialEscudos(escudos);
    printf(CIAN_B "\nEstado inicial: todos los escudos al 100%%\n" RESET);

    while (1) {
        mostrarMenu();
        opcion = leerOpcion();

        if (opcion == 1) {
            int indice = elegirSector(escudos);
            int danio = validarEnteroPositivo("Ingrese el dano recibido: ");

            /* &escudos[indice] es un PUNTERO: paso por referencia real */
            aplicarImpacto(&escudos[indice], danio);

            printf(ROJO_B "\nImpacto aplicado. Nuevo nivel de '%s': %d\n" RESET,
                   escudos[indice].nombre, escudos[indice].nivel);
            mostrarEstado(escudos);

        } else if (opcion == 2) {
            mostrarEstado(escudos);

        } else if (opcion == 3) {
            int indice = elegirSector(escudos);
            int refuerzo = validarEnteroPositivo("Ingrese el nivel de refuerzo: ");

            reforzarSector(&escudos[indice], refuerzo);

            printf(VERDE_B "\nSector '%s' reforzado. Nuevo nivel: %d\n" RESET,
                   escudos[indice].nombre, escudos[indice].nivel);

        } else if (opcion == 4) {
            printf(MAGENTA_B "\nCerrando sistema de escudos...\n" RESET);
            break;
        }
    }

    return 0;
}

