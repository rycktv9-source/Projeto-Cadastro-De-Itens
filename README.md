#  ERP de Gestão de Estoque

##  Sobre o Projeto

Este é um **Sistema de Gestão de Estoque (ERP)** desenvolvido em Python, projetado para auxiliar no controle e acompanhamento de produtos. Ele permite realizar operações CRUD (Criar, Ler, Atualizar, Excluir) básicas e oferece um **Dashboard** com visualizações de dados para análise estratégica do inventário, como a **Curva ABC**.

##  Funcionalidades

O sistema é operado através de um menu interativo e oferece as seguintes opções:

1.  **Cadastrar Produto:** Adiciona um novo item ao estoque, solicitando nome, categoria, preço e quantidade inicial.
2.  **Excluir Produto:** Remove um item do estoque usando seu ID único.
3.  **Mostrar Relatório de Produtos:** Exibe uma lista formatada de todos os produtos, destacando aqueles com **estoque baixo** (quantidade < 5).
4.  **Visualizar Dashboard de Acompanhamento:** Gera dois gráficos de análise:
    * **Comparação de Categorias:** Gráfico de barras mostrando o número de produtos por categoria.
    * **Curva ABC:** Análise de Pareto para custos de estoque, ajudando a identificar os itens mais valiosos (Classe A).
5.  **Sair do Programa:** Encerra a aplicação.
