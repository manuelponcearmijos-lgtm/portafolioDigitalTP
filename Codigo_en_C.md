## 🧩 Código Fuente Completo

```c
 #include <stdio.h>

#define FILAS 2
#define COLUMNAS 3

// Función para completar los datos de una matriz solicitando los valores al usuario por teclado
void completarMatriz(int matriz[FILAS][COLUMNAS], int numMatriz) {

    printf("\nIngrese los valores de la matriz %d:\n", numMatriz);

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            printf("Elemento [%d][%d]: ", i, j);
            scanf("%d", &matriz[i][j]);
        }
    }
}

// Función para sumar dos matrices elemento a elemento y guardar el resultado
void sumaMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] + B[i][j];
        }
    }
}

// Función para restar dos matrices elemento a elemento y guardar el resultado
void restaMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] - B[i][j];
        }
    }
}

// Función para multiplicar dos matrices elemento a elemento y guardar el resultado
void multiplicacionMatriz(int A[FILAS][COLUMNAS], int B[FILAS][COLUMNAS], int resultado[FILAS][COLUMNAS]) {

    for (int i = 0; i < FILAS; i++) {

        for (int j = 0; j < COLUMNAS; j++) {

            resultado[i][j] = A[i][j] * B[i][j];
        }
    }
}

// Función para mostrar por pantalla la matriz resultante de una operación con formato de filas y columnas
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

    // Declaración de las matrices de 2x3
    int matrizA[FILAS][COLUMNAS];
    int matrizB[FILAS][COLUMNAS];
    int resultado[FILAS][COLUMNAS];

    // Llamada a la función para llenar las matrices A y B
    completarMatriz(matrizA, 1);
    completarMatriz(matrizB, 2);

    // Operación de suma y muestra del resultado
    sumaMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "suma");

    // Operación de resta y muestra del resultado
    restaMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "resta");

    // Operación de multiplicación y muestra del resultado
    multiplicacionMatriz(matrizA, matrizB, resultado);
    mostrarResultado(resultado, "multiplicacion");

    return 0;
}
 ```
