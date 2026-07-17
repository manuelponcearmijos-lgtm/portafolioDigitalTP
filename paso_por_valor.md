 """
Sistema Inteligente de Gestión Energética de una Estación Espacial
--------------------------------------------------------------------
Este programa demuestra el PASO DE PARÁMETROS POR VALOR en Python.

La energía real de la estación (energia_actual) se pasa a la función
simular_consumo() como argumento. Al ser un dato de tipo float
(inmutable), cualquier cálculo realizado dentro de la función se
efectúa sobre una copia local, por lo que el valor original NUNCA
se modifica desde fuera de esa función.
"""

MODULOS_DISPONIBLES = ("navegación", "soporte vital", "comunicaciones", "laboratorio")


def mostrar_menu() -> None:
    """Imprime en pantalla las opciones del sistema."""
    print("\n===== Sistema de Gestión Energética =====")
    print("1. Simular consumo de un módulo")
    print("2. Ver historial de simulaciones")
    print("3. Salir")


def leer_opcion() -> int:
    """Valida que la opción ingresada sea un entero entre 1 y 3."""
    while True:
        entrada = input("Seleccione una opción: ").strip()
        if entrada.isdigit() and int(entrada) in (1, 2, 3):
            return int(entrada)
        print("Opción inválida. Intente nuevamente.")


def validar_numero(mensaje: str) -> float:
    """Solicita un número al usuario y valida que sea positivo."""
    while True:
        entrada = input(mensaje).strip()
        try:
            valor = float(entrada)
            if valor < 0:
                print("El valor no puede ser negativo.")
                continue
            return valor
        except ValueError:
            print("Debe ingresar un número válido.")


def simular_consumo(energia_disponible: float, consumo: float) -> float:
    """
    Calcula la energía restante tras un consumo, SIN alterar el valor
    original recibido (paso por valor: energia_disponible es una copia
    local del float que existe en main()).
    """
    energia_disponible -= consumo  # Esta resta solo afecta la copia local
    if energia_disponible < 0:
        energia_disponible = 0
    return energia_disponible


def registrar_simulacion(historial: list, resultado: float) -> None:
    """Agrega el resultado de una simulación al historial del programa."""
    historial.append(resultado)


def mostrar_historial(historial: list) -> None:
    """Imprime todas las simulaciones registradas durante la sesión."""
    if not historial:
        print("Aún no se ha realizado ninguna simulación.")
        return
    print("\n--- Historial de simulaciones (kWh restantes) ---")
    for indice, valor in enumerate(historial, start=1):
        print(f"Simulación {indice}: {valor:.2f} kWh")


def elegir_modulo() -> str:
    """Permite al usuario elegir un módulo de la estación."""
    print("Módulos disponibles:", ", ".join(MODULOS_DISPONIBLES))
    while True:
        modulo = input("Ingrese el módulo que consumirá energía: ").strip().lower()
        if modulo in MODULOS_DISPONIBLES:
            return modulo
        print("Módulo no reconocido. Intente nuevamente.")


def main() -> None:
    """Función principal: orquesta el menú y el flujo del programa."""
    energia_actual = 1500.0  # Energía real de la estación
    historial_consumos = []

    while True:
        mostrar_menu()
        opcion = leer_opcion()

        if opcion == 1:
            modulo = elegir_modulo()
            consumo = validar_numero(f"Ingrese el consumo del módulo de {modulo} (kWh): ")

            resultado_simulado = simular_consumo(energia_actual, consumo)
            registrar_simulacion(historial_consumos, resultado_simulado)

            print(f"\nEnergía simulada restante tras el consumo: {resultado_simulado:.2f} kWh")
            print(f"Energía REAL de la estación (sin cambios): {energia_actual:.2f} kWh")

        elif opcion == 2:
            mostrar_historial(historial_consumos)

        elif opcion == 3:
            print("Cerrando sistema de gestión energética...")
            break


if __name__ == "__main__":
    main()
