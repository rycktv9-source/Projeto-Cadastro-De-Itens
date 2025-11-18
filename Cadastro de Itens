import os
import matplotlib.pyplot as plt
import pandas as pd

estoque = []
id_contador = 1

# Commit 1: Implementa funções de cadastro e exclusão de produtos no estoque
def cadastrar_produto():
    """Permite ao usuário cadastrar um novo produto."""
    global id_contador
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Cadastrar Novo Produto \n")
    nome = input("Nome do produto: ").strip().capitalize()
    categoria = input("Categoria: ").strip().capitalize()

    while True:
        try:
            preco = float(input("Preço: "))
            if preco <= 0:
                print("O preço deve ser maior que zero. Tente novamente.")
            else:
                break
        except ValueError:
            print("Entrada inválida. Por favor, digite um número para o preço.")

    while True:
        try:
            quantidade = int(input("Quantidade inicial: "))
            if quantidade < 0:
                print("A quantidade não pode ser negativa. Tente novamente.")
            else:
                break
        except ValueError:
            print("Entrada inválida. Por favor, digite um número inteiro para a quantidade.")

    novo_produto = {
        "id": id_contador,
        "nome": nome,
        "categoria": categoria,
        "preco": preco,
        "quantidade": quantidade
    }
    estoque.append(novo_produto)
    id_contador += 1
    print("\nProduto cadastrado com sucesso!")
    input("\nPressione Enter para continuar...")

def excluir_produto():
    """Permite ao usuário excluir um produto pelo ID."""
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Excluir Produto \n")

    if not estoque:
        print("Nenhum produto cadastrado para excluir.")
        input("\nPressione Enter para continuar...")
        return

    try:
        produto_id = int(input("Digite o ID do produto que deseja excluir: "))
    except ValueError:
        print("ID inválido. Por favor, digite um número.")
        input("\nPressione Enter para continuar...")
        return

    produto_encontrado = None
    for produto in estoque:
        if produto['id'] == produto_id:
            produto_encontrado = produto
            break

    if produto_encontrado:
        confirmacao = input(f"Tem certeza que deseja excluir o produto '{produto_encontrado['nome']}'? (s/n): ").lower()
        if confirmacao == 's':
            estoque.remove(produto_encontrado)
            print("Produto excluído com sucesso!")
        else:
            print("Operação cancelada.")
    else:
        print(f"Produto com ID '{produto_id}' não encontrado.")

    input("\nPressione Enter para continuar...")

# Commit 2: Adiciona função de relatório de produtos em estoque
def mostrar_relatorio():
    """Exibe um relatório com todos os produtos e seus detalhes."""
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Relatório de Produtos em Estoque \n")

    if not estoque:
        print("Nenhum produto cadastrado no momento.")
        input("\nPressione Enter para continuar...")
        return

    print(f"{'ID':<4} | {'Nome do Produto':<30} | {'Categoria':<15} | {'Preço':<10} | {'Quantidade':<12}")
    print("-" * 75)

    for produto in estoque:
        destaque = ""

        if produto['quantidade'] < 5:
            destaque = " (ESTOQUE BAIXO)"

        print(
            f"{produto['id']:<4} | "
            f"{produto['nome']:<30} | "
            f"{produto['categoria']:<15} | "
            f"R$ {produto['preco']:<6.2f} | "
            f"{produto['quantidade']:<12}{destaque}"
        )

    print("\n--- Fim do Relatório ---")
    input("\nPressione Enter para continuar...")

# Commit 3: Adiciona dashboard com gráficos de comparação de categorias e curva ABC
def gerar_dashboard():
    """Gera os gráficos de acompanhamento do estoque."""
    os.system('cls' if os.name == 'nt' else 'clear')
    print("Dashboard de Acompanhamento \n")

    # Criar um DataFrame a partir dos produtos em estoque
    df = pd.DataFrame(estoque)

    if df.empty:
        print("Nenhum produto cadastrado para gerar gráficos.")
        input("\nPressione Enter para continuar...")
        return

    # Gráfico de evolução do estoque
    df['valor_estoque'] = df['preco'] * df['quantidade']

    # Gráfico de barras por categoria
    categoria_counts = df['categoria'].value_counts()
    categoria_counts.plot(kind='bar', title="Comparação de Categorias", color='skyblue')
    plt.xlabel("Categoria")
    plt.ylabel("Número de Produtos")
    plt.show()

    # Curva ABC para custo de estoques
    df_sorted = df.sort_values(by='valor_estoque', ascending=False)
    df_sorted['cumulative_cost'] = df_sorted['valor_estoque'].cumsum()
    df_sorted['percent_cumulative'] = 100 * df_sorted['cumulative_cost'] / df_sorted['valor_estoque'].sum()

    plt.plot(df_sorted['percent_cumulative'], label="Curva ABC", color='green')
    plt.axhline(80, color='red', linestyle='--', label="80%")
    plt.title("Curva ABC para Custos de Estoque")
    plt.xlabel("Produtos")
    plt.ylabel("Percentual Acumulado")
    plt.legend()
    plt.show()

    input("\nPressione Enter para voltar ao menu principal...")

def menu_principal():
    """Exibe o menu interativo e gerencia as opções do usuário."""
    while True:
        os.system('cls' if os.name == 'nt' else 'clear')
        print("ERP de Gestão de Estoque \n")
        print("1. Cadastrar produto")
        print("2. Excluir produto")
        print("3. Mostrar relatório de produtos")
        print("4. Visualizar dashboard de acompanhamento")
        print("5. Sair do programa")

        opcao = input("\nEscolha uma opção: ")

        if opcao == '1':
            cadastrar_produto()
        elif opcao == '2':
            excluir_produto()
        elif opcao == '3':
            mostrar_relatorio()
        elif opcao == '4':
            gerar_dashboard()
        elif opcao == '5':
            print("Encerrando o programa. Até logo!")
            break
        else:
            print("Opção inválida. Por favor, escolha uma opção de 1 a 5.")
            input("\nPressione Enter para continuar...")

if __name__ == "__main__":
    menu_principal()
