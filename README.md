# Algoritmo-Constante-de-Kaprekar
Este repositório contém uma implementação em Python do algoritmo da Constante de Kaprekar (6174) para números de até 4 dígitos.  O programa realiza a leitura de um número, aplica validações e executa iterativamente o processo de Kaprekar até atingir a constante 6174 ou encontrar uma condição inválida.

# Algoritmo Constante de Kaprekar 
# Entrada numérica
valor = float(input("Digite um número de até 4 dígitos: "))

# 1) Validação de tipo: inteiro e positivo
if valor < 0:
    print("Erro: o número deve ser inteiro e positivo.")
else:
    if valor // 1 != valor:
        print("Erro: o valor informado não é um número inteiro.")
    else:
        numero = int(valor // 1)

        # 2) Validação de faixa: 0000 a 9999
        if numero > 9999:
            print("Erro: número inválido. Deve estar entre 0000 e 9999.")
        else:
            # Exibir número informado com 4 dígitos (sem string)
            n1 = numero // 1000
            r = numero % 1000
            n2 = r // 100
            r = r % 100
            n3 = r // 10
            n4 = r % 10

            print("Número informado: ", end="")
            print(n1, n2, n3, n4, sep="")
            print()

            iteracao = 0
            continuar = 1

            while continuar == 1:
                # Extrai os dígitos
                d1 = numero // 1000
                resto = numero % 1000
                d2 = resto // 100
                resto = resto % 100
                d3 = resto // 10
                d4 = resto % 10

                # 3) Validação de repetição: 3 ou mais dígitos iguais
                c1 = 0
                if d1 == d1:
                    c1 = c1 + 1
                if d2 == d1:
                    c1 = c1 + 1
                if d3 == d1:
                    c1 = c1 + 1
                if d4 == d1:
                    c1 = c1 + 1

                c2 = 0
                if d1 == d2:
                    c2 = c2 + 1
                if d2 == d2:
                    c2 = c2 + 1
                if d3 == d2:
                    c2 = c2 + 1
                if d4 == d2:
                    c2 = c2 + 1

                c3 = 0
                if d1 == d3:
                    c3 = c3 + 1
                if d2 == d3:
                    c3 = c3 + 1
                if d3 == d3:
                    c3 = c3 + 1
                if d4 == d3:
                    c3 = c3 + 1

                c4 = 0
                if d1 == d4:
                    c4 = c4 + 1
                if d2 == d4:
                    c4 = c4 + 1
                if d3 == d4:
                    c4 = c4 + 1
                if d4 == d4:
                    c4 = c4 + 1

                if c1 >= 3 or c2 >= 3 or c3 >= 3 or c4 >= 3:
                    print("Erro: número possui muitos dígitos repetidos (3 ou mais iguais).")
                    continuar = 0
                else:
                    # 4) Construção do NDC (crescente) por trocas
                    a = d1
                    b = d2
                    c = d3
                    d = d4
                    aux = 0

                    if a > b:
                        aux = a
                        a = b
                        b = aux
                    if a > c:
                        aux = a
                        a = c
                        c = aux
                    if a > d:
                        aux = a
                        a = d
                        d = aux
                    if b > c:
                        aux = b
                        b = c
                        c = aux
                    if b > d:
                        aux = b
                        b = d
                        d = aux
                    if c > d:
                        aux = c
                        c = d
                        d = aux

                    ndc = a * 1000 + b * 100 + c * 10 + d

                    # 5) Construção do NDD (decrescente)
                    ndd = d * 1000 + c * 100 + b * 10 + a

                    # 6) Subtração
                    resultado = ndd - ndc
                    iteracao = iteracao + 1

                    # Mostrar operação com 4 dígitos
                    x1 = ndd // 1000
                    xr = ndd % 1000
                    x2 = xr // 100
                    xr = xr % 100
                    x3 = xr // 10
                    x4 = xr % 10

                    y1 = ndc // 1000
                    yr = ndc % 1000
                    y2 = yr // 100
                    yr = yr % 100
                    y3 = yr // 10
                    y4 = yr % 10

                    z1 = resultado // 1000
                    zr = resultado % 1000
                    z2 = zr // 100
                    zr = zr % 100
                    z3 = zr // 10
                    z4 = zr % 10

                    print("Iteração ", iteracao, ": ", sep="", end="")
                    print(x1, x2, x3, x4, sep="", end="")
                    print(" - ", end="")
                    print(y1, y2, y3, y4, sep="", end="")
                    print(" = ", end="")
                    print(z1, z2, z3, z4, sep="")

                    # 8) Parada
                    if resultado == 6174:
                        print()
                        print("Constante de Kaprekar (6174) atingida em", iteracao, "iterações.")
                        continuar = 0
                    else:
                        # 7) Iteração
                        numero = resultado

                        # Validação de faixa no ciclo
                        if numero < 0 or numero > 9999:
                            print("Erro: resultado fora da faixa 0000 a 9999.")
                            continuar = 0
