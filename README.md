# pyflix.trabalho_de_pest
Grupo: Renara soares, Thalita Ellen e Beatriz de Souza
# Lista para armazenar os filmes
filmes = []

# Função para exibir o menu
def menu():
    print("-" * 30)
    print("1. Adicionar filme")
    print("2. Listar filmes")
    print("3. Buscar filme por título")
    print("4. Atualizar filme")
    print("5. Remover filme")
    print("6. Sair")
    print("-" * 30)
    opcao = int(input("Escolha uma opção: "))
    print("-"*30)
    return opcao

# Função para adicionar um filme
def adicionar_filme():
    titulo = input("Título do filme: ")
    diretor = input("Diretor: ")
    
  # Validação do ano de lançamento
   while True:
        lancamento = int(input("Ano de lançamento: "))
        if lancamento < 1889:
            print("Ano de lançamento inválido, tente novamente.")
        else:
            break
    
   genero = input("Gênero: ")
   novo_filme = [titulo, diretor, lancamento, genero]
   filmes.append(novo_filme)
   print(f"O filme {titulo} foi adicionado com sucesso.")

# Função para buscar os filmes
def buscar_filme():
    filme = input("Digite qual filme quer encontrar: ")
    filme = filme.lower()
    for n in range(len(filmes)):
        if  filmes[n][0].lower() == filme.lower():
          print(f"Título: {filmes[n][0]}")
          print(f"Diretor: {filmes[n][1]}")
          print(f"Ano de lançamento: {filmes[n][2]}")
          print(f"Gênero: {filmes[n][3]}")
        else:
          print("Filme não existente ou Filme não encontrado!")


# Função para listar os filmes
def listar_filmes():
    vazio = True  # lista está vazia
    print("Catálogo de Filmes:")
    
  indice = 1
    for filme in filmes:
        print(str(indice) + ". Título: " + filme[0] + ", Diretor: " + filme[1] + ", Ano: " + str(filme[2]) + ", Gênero: " + filme[3])
        indice += 1
        vazio = False  # se entrar no laço, a lista não está vazia
    
  if vazio:
        print("O catálogo de filmes está vazio.")

#função atualizar os filmes
def atualizar_filme():
    titulo = input("Digite o título do filme que deseja atualizar: ")
    encontrado = False
    for i in range(len(filmes)):
        if filmes[i][0].lower() == titulo.lower():
            novo_titulo = input(f"Novo título ({filmes[i][0]}): ") or filmes[i][0]
            novo_diretor = input(f"Novo diretor ({filmes[i][1]}): ") or filmes[i][1]
            
   #validação do ano de lançamento
   while True:
                novo_lancamento = input(f"Novo ano de lançamento ({filmes[i][2]}): ") or filmes[i][2]
                novo_lancamento = novo_lancamento.strip()
                
   if novo_lancamento == "":
                    novo_lancamento = filmes[i][2]
                    break
                
   #verifica se o ano é numérico e válido
   valido = True
                for char in novo_lancamento:
                    if char not in "0123456789":
                        valido = False
                        break
                
   if valido:
                    novo_lancamento_int = int(novo_lancamento)
                    if novo_lancamento_int >= 1889:
                        novo_lancamento = novo_lancamento_int
                        break
                    else:
                        print("Ano de lançamento inválido, tente novamente.")
                else:
                    print("Ano de lançamento inválido, tente novamente.")
            
  novo_genero = input(f"Novo gênero ({filmes[i][3]}): ") or filmes[i][3]
            
            #mostra a lista formatada 
  filmes[i] = [novo_titulo, novo_diretor, novo_lancamento, novo_genero]
            print(f"O filme '{novo_titulo}' foi atualizado com sucesso.")
            encontrado = True
            break
    
  if not encontrado:
        print("Filme não encontrado.")

# Função de deletar filmes

def deletar_filme():
    filme = input("Digite qual o Título do filme que você deseja deletar: ")
    filme = filme.lower()
    for n in range(len(filmes)):
        if  filmes[n][0].lower() == filme.lower():
          filmes.pop(n)
          print(f"O Filme '{filme}' foi removido com sucesso!")
        else:
          print("Ops! Houve algum erro, tente novamente se possivel!")
          
    

# Loop principal do sistema
while True:
    opcao = menu()
    
  if opcao == 1:
        adicionar_filme()
    elif opcao == 2:
        listar_filmes()
    elif opcao == 3:
        buscar_filme()
    elif opcao == 4:
        atualizar_filme()
    elif opcao == 5:
        deletar_filme()
    elif opcao == 6:
        print("Saindo do sistema...")
        break
    else:
        print("Opção inválida! Tente novamente.")
