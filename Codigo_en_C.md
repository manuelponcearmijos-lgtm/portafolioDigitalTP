## 🧩 Código Fuente Completo

```c
#include <stdio.h>

#define FILAS 2
#define COLUMNAS 3

void completarMatriz(int matriz[FILAS][COLUMNAS], int numMatriz) {

    printf("\nIngrese los valores de la matriz %d:\n", numMatriz);

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            printf("Elemento [%d][%d]: ", i, j);
            scanf("%d", &matriz[i][j]);
        }
    }
}

 
void sumaMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] + B[i][j];
        }
    }
}

 
void restaMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] - B[i][j];
        }
    }
}

void multiplicacionMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] * B[i][j];
        }
    }
}


void mostrarResultado(int matriz[FILAS][COLUMNAS], char operacion[]) {

    printf("\nResultado de la %s:\n", operacion);

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            printf("%d\t", matriz[i][j]);
        }
        printf("\n");
    }
}

int main() {

    int matrizA[FILAS][COLUMNAS];
    int matrizB[FILAS][COLUMNAS];
    int resultado[FILAS][COLUMNAS];

    completarMatriz(matrizA, 1);
    completarMatriz(matrizB, 2);

    sumaMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "suma");

    restaMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "resta");

    multiplicacionMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "multiplicacion");

    return 0;
}
 ```
