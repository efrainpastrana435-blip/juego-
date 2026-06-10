import random
import time

def guardar_puntuacion(nombre, puntos):
    with open("ranking.txt", "a") as f:
        f.write(f"{nombre},{puntos}\n")

def mostrar_ranking():
    print("\n🏆 Ranking de jugadores:")
    try:
        with open("ranking.txt", "r") as f:
            lineas = f.readlines()
            datos = []
            for linea in lineas:
                if "," in linea:
                    nombre, puntos = linea.strip().split(",")
                    datos.append((nombre, int(puntos)))
            datos.sort(key=lambda x: x[1], reverse=True)
            for nombre, puntos in datos[:10]:
                print(f"{nombre}: {puntos}")
    except FileNotFoundError:
        print("No hay puntuaciones registradas aún.")

def juego():
    print("🎮 Bienvenido a Catch the Number")
    print("Tienes 30 segundos para atrapar números correctos.")
    print("Se mostrarán números aleatorios, escribe el mismo número para ganar puntos.\n")

    puntos = 0
    inicio = time.time()

    while time.time() - inicio < 30:
        numero = random.randint(0, 9)
        print(f"Número mostrado: {numero}")
        intento = input("Tu respuesta: ")

        if intento.isdigit() and int(intento) == numero:
            puntos += 1
            print("✅ Correcto! +1 punto\n")
        else:
            print("❌ Fallaste\n")

    print("⏰ Tiempo terminado!")
    print(f"Tu puntuación final: {puntos}")
    nombre = input("Ingresa tu nombre: ")
    guardar_puntuacion(nombre, puntos)
    mostrar_ranking()

if __name__ == "__main__":
    juego()
