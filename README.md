# jogodaforcanovo
import random

arquivo = open("br-sem-acentos.txt")
linhas = arquivo.readlines()
palavra = ''

while len(palavra) < 5 or len(palavra) > 10 :
    sorteio = random.randint(0, len(linhas))
    palavra = linhas[sorteio]
    palavra = palavra.upper().strip()
    arquivo.close()
print(palavra)

print("Bem vindo ao Jogo da Forca.")
print("Seu objetivo é tentar acertar a palavra secreta!")
print("Caso você acerte a letra, terás mais chances de advinhar a palavra secreta.")

def mostrar_palavra(palavra, letras_corretas):
    for letra in palavra:
        if letra in letras_corretas:
            print(letra, end=' ')
        else:
            print('_', end=' ')
    print('')


letras_corretas = []
tentativas = 6

while tentativas > 0:
    print()
    mostrar_palavra(palavra, letras_corretas)
    print(f"Tentativas restantes: {tentativas}")

    letra = input("Digite uma letra: ").upper()

    if letra.upper() in palavra:
        print("Letra correta!")
        letras_corretas.append(letra.upper())
    else:
        print("Letra incorreta!")
        tentativas = tentativas -1

    acertou_todas = True
    for letra in palavra:
        if letra not in letras_corretas:
            acertou_todas = False
            break

    if acertou_todas:
        print("Parabéns! Você acertou a palavra!")
        break

if tentativas == 0:
   print("Você perdeu, tenta outra vez!")
print(f"A palavra era:,{palavra}")
