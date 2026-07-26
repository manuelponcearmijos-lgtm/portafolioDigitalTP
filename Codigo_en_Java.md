
## 🧩 Código Fuente Completo

 ```Java
 public class OperacionesMatrices {

    static final int FILAS = 2;
    static final int COLUMNAS = 3;

    // Función para completar los datos de una matriz solicitando los valores al usuario por teclado
    public static void completarMatriz(int[][] matriz, int numMatriz, java.util.Scanner scanner) {
        System.out.println("\nIngrese los valores de la matriz " + numMatriz + ":");
        for (int i = 0; i < FILAS; i++) {
            for (int j = 0; j < COLUMNAS; j++) {
                System.out.print("Elemento [" + i + "][" + j + "]: ");
                matriz[i][j] = scanner.nextInt();
            }
        }
    }

    // Función para sumar dos matrices elemento a elemento y guardar el resultado
    public static void sumaMatriz(int[][] A, int[][] B, int[][] resultado) {
        for (int i = 0; i < FILAS; i++) {
            for (int j = 0; j < COLUMNAS; j++) {
                resultado[i][j] = A[i][j] + B[i][j];
            }
        }
    }

    // Función para restar dos matrices elemento a elemento y guardar el resultado
    public static void restaMatriz(int[][] A, int[][] B, int[][] resultado) {
        for (int i = 0; i < FILAS; i++) {
            for (int j = 0; j < COLUMNAS; j++) {
                resultado[i][j] = A[i][j] - B[i][j];
            }
        }
    }

    // Función para multiplicar dos matrices elemento a elemento y guardar el resultado
    public static void multiplicacionMatriz(int[][] A, int[][] B, int[][] resultado) {
        for (int i = 0; i < FILAS; i++) {
            for (int j = 0; j < COLUMNAS; j++) {
                resultado[i][j] = A[i][j] * B[i][j];
            }
        }
    }

    // Función para mostrar por pantalla la matriz resultante de una operación con formato de filas y columnas
    public static void mostrarResultado(int[][] matriz, String operacion) {
        System.out.println("\nResultado de la " + operacion + ":");
        for (int i = 0; i < FILAS; i++) {
            for (int j = 0; j < COLUMNAS; j++) {
                System.out.print(matriz[i][j] + "\t");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        java.util.Scanner scanner = new java.util.Scanner(System.in);

        // Declaración de las matrices de 2x3
        int[][] matrizA = new int[FILAS][COLUMNAS];
        int[][] matrizB = new int[FILAS][COLUMNAS];
        int[][] resultado = new int[FILAS][COLUMNAS];

        // Llamada a la función para llenar las matrices A y B
        completarMatriz(matrizA, 1, scanner);
        completarMatriz(matrizB, 2, scanner);

        // Operación de suma y muestra del resultado
        sumaMatriz(matrizA, matrizB, resultado);
        mostrarResultado(resultado, "suma");

        // Operación de resta y muestra del resultado
        restaMatriz(matrizA, matrizB, resultado);
        mostrarResultado(resultado, "resta");

        // Operación de multiplicación y muestra del resultado
        multiplicacionMatriz(matrizA, matrizB, resultado);
        mostrarResultado(resultado, "multiplicacion");

        scanner.close();
    }
}
 ```
