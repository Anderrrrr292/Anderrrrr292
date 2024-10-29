 Código de juego ficticio "DarkMarket"

import time
import random

class Player:
    def __init__(self, name):
        self.name = name
        self.money = 1000
        self.drops = 0
        self.level = 1

    def sell_drop(self):
        drop_value = random.randint(50, 200)
        self.money += drop_value
        self.drops += 1

    def level_up(self):
        self.level += 1
        self.money += self.level * 100

def main():
    player = Player("Jugador")
    print(f"Bienvenido, {player.name}!")

    while True:
        action = input("¿Qué deseas hacer? (vender, comprar, salir): ").lower()

        if action == "vender":
            player.sell_drop()
            print(f"¡Vendido un drop por {player.drops}! Tu dinero actual: {player.money}")
            player.drops = 0

        elif action == "comprar":
            drop_price = random.randint(100, 500)
            if player.money >= drop_price:
                player.money -= drop_price
                print(f"¡Compraste un drop por {drop_price}! Tu dinero actual: {player.money}")
            else:
                print("¡No tienes suficiente dinero!")

        elif action == "salir":
            print(f"¡Adiós, {player.name}! Tu dinero final: {player.money}")
            break

        else:
            print("¡Opción no válida!")

        time.sleep(1)
        print("-" * 20)

if __name__ == "__main__":
    main()
