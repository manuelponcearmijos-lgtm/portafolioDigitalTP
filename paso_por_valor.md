 /*
 * paso_por_valor.c
 * ------------------------------------------------------------
 * Sistema de Escudos de una Estacion Espacial
 * ------------------------------------------------------------
 * Este programa demuestra el PASO DE PARAMETROS POR VALOR en C.
 * En este caso, la función recibe una copia del valor original,
 * por lo que las modificaciones internas no afectan la variable
 * del programa principal.
 */

#include <stdio.h>

void aplicarImpacto(int nivel, int danio) {
    nivel -= danio;
    if (nivel < 0) nivel = 0;
    printf("Nivel dentro de la funcion: %d\n", nivel);
}

int main(void) {
    int escudo = 100;
    printf("Nivel inicial del escudo: %d\n", escudo);
    aplicarImpacto(escudo, 30);
    printf("Nivel final del escudo (main): %d\n", escudo);
    return 0;
}
