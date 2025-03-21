import random

palavras = ["python", "programacao", "computador", "jogos", "algoritmo"]


def jogo_da_forca():
    
    palavra_secreta = random.choice(palavras)
    letras_descobertas = ["_" for _ in palavra_secreta]
    tentativas_restantes = 6  
    letras_erradas = []

    print("Bem-vindo ao jogo da forca!")

    # Loop do jogo
    while tentativas_restantes > 0 and "_" in letras_descobertas:
        print("\nPalavra:", " ".join(letras_descobertas))
        print("Letras erradas:", " ".join(letras_erradas))
        print(f"Tentativas restantes: {tentativas_restantes}")
        
    
        letra = input("Digite uma letra: ").lower()
        
        if len(letra) != 1 or not letra.isalpha():
            print("Por favor, digite apenas uma letra.")
            continue
        
        
        if letra in letras_descobertas or letra in letras_erradas:
            print("Você já tentou essa letra.")
            continue
        
        
        if letra in palavra_secreta:
            for i, l in enumerate(palavra_secreta):
                if l == letra:
                    letras_descobertas[i] = letra
            print("Boa! Você acertou uma letra.")
        else:
            tentativas_restantes -= 1
            letras_erradas.append(letra)
            print("Essa letra não está na palavra.")

    # Resultado do jogo
    if "_" not in letras_descobertas:
        print("\nParabéns! Você descobriu a palavra:", palavra_secreta)
    else:
        print("\nQue pena! Você foi enforcado. A palavra era:", palavra_secreta)


jogo_da_forca()
