import random
import time


# Estoque
estacas = 4
sacos_de_
grao = 22
plantacoes = 4


ferreiro = 10
mineiro = 10
lenhador = 4


def combate():
    global estacas, plantacoes, ferreiro, mineiro, lenhador


    # 2 ou 3 invasões
    r = random.random()
    if r < 0.5:
        invasoes = 2
    else:
        invasoes = 3


    for i in range(invasoes):
        print(f"\nINVASÃO {i+1}")
        time.sleep(1)


        # 2 a 5 goblins
        goblins = int(random.random() * 4) + 2


        print(f"Goblins se aproximando... ({goblins} goblins)")
        time.sleep(1)


        for g in range(goblins):
            print(f"\nGOBLIN {g+1}")
            time.sleep(1)


            if estacas > 0:
                chance_quebrar = random.random()
                if chance_quebrar <= 0.3:
                    estacas -= 1
                    print(f"Goblin quebrou uma estaca! Estacas restantes: {estacas}")


                    luta = input("Goblin avançou! Você quer enfrentar? (s/n) ").strip().lower()
                    if luta == "s":
                        print("Você enfrentou o goblin! que comece a porradaria de cartas!")
                    else:
                        ferreiro -= 1
                        mineiro -= 1
                        lenhador -= 1
                        print("O goblin atacou nossos amigos! (-1 de vida cada)")
                        morte()
                        # Queima
                        if random.random() <= 0.05 and plantacoes > 0:
                            plantacoes -= 1
                            print("Uma plantação foi queimada🔥!")
                else:
                    print("A estaca resistiu bobão!")
            else:
                print("!!!Sem estacas!!! Goblin passou direto!")
                resposta = input("Você quer enfrentar? (s/n) ").strip().lower()
                if resposta == "s":
                    print("Você enfrentou o goblin! que comece a porradaria de cartas!")
                else:
                    ferreiro -= 1
                    mineiro -= 1
                    lenhador -= 1
                    print("O goblin atacou nossos amigos! (-1 de vida cada)")
                    morte()
                    if random.random() <= 0.05 and plantacoes > 0:
                        plantacoes -= 1
                        print("Uma plantação foi queimada🔥!")


def morte():
    if ferreiro <= 0:
        print("!!!O Ferreiro morreu!!!")
    if mineiro <= 0:
        print("!!!O Mineiro morreu!!!")
    if lenhador <= 0:
        print("!!!O Lenhador morreu!!!")


combate()


# Resultado
print("\n   FIM DO COMBATE   ")
print(f"Estacas restantes: {estacas}")
print(f"Plantações restantes: {plantacoes}")
print(f"Sacos de grão restantes: {sacos_de_grao}")
print("Estado final dos moradores:")
print(f"Ferreiro: {max(ferreiro, 0)}")
print(f"Mineiro: {max(mineiro, 0)}")
print(f"Lenhador: {max(lenhador, 0)}")