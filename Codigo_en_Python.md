 ```Python

FILAS = 2
FILAS_COLUMNAS = 3  # Usamos COLUMNAS para mantener la estructura clara

# Como en Python no hay macros #define directas, usamos constantes
FILAS = 2
COLUMNAS = 3

def completar_matriz(matriz, num_matriz):
    print(f"\nIngrese los valores de la matriz {num_matriz}:")
    for i in range(FILAS):
        for j in range(COLUMNAS):
            # En Python pedimos el valor y lo convertimos a entero
            matriz[i][j] = int(input(f"Elemento [{i}][{j}]: "))

def suma_matriz(A, B, resultado):
    for i in range(FILAS):
        for j in range(COLUMNAS):
            resultado[i][j] = A[i][j] + B[i][j]

def resta_matriz(A, B, resultado):
    for i in range(FILAS):
        for j in range(COLUMNAS):
            resultado[i][j] = A[i][j] - B[i][j]

def multiplicacion_matriz(A, B, resultado):
    for i in range(FILAS):
        for j in range(COLUMNAS):
            resultado[i][j] = A[i][j] * B[i][j]

def mostrar_resultado(matriz, operacion):
    print(f"\nResultado de la {operacion}:")
    for i in range(FILAS):
        for j in range(COLUMNAS):
            print(f"{matriz[i][j]}\t", end="")
        print()

def main():
    # Inicializamos las matrices con ceros (arreglos bidimensionales de 2x3)
    matrizA = [[0] * COLUMNAS for _ in range(FILAS)]
    matrizB = [[0] * COLUMNAS for _ in range(FILAS)]
    resultado = [[0] * COLUMNAS for _ in range(FILAS)]

    completar_matriz(matrizA, 1)
    completar_matriz(matrizB, 2)

    suma_matriz(matrizA, matrizB, resultado)
    mostrar_resultado(resultado, "suma")

    resta_matriz(matrizA, matrizB, resultado)
    mostrar_resultado(resultado, "resta")

    multiplicacion_matriz(matrizA, matrizB, resultado)
    mostrar_resultado(resultado, "multiplicacion")

if __name__ == "__main__":
    main()
 ```
