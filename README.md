# JOGO DE DADOS

## 1. Visão Geral e Arquitetura

Este projeto implementa o **Jogo de Dados** com uma arquitetura web, onde a lógica central do jogo é estritamente aderente aos princípios de Programação Orientada a Objetos (POO), conforme modelado nas classes `Jogo`, `Dado` e `Jogador`.

O sistema consiste em dois dados e uma quantidade $X$ de jogadores. A interação (input) e a apresentação (output) do jogo, anteriormente gerenciadas por um console, agora são realizadas através de uma **Interface Web**.

### Componentes Chave da Arquitetura:

1.  **Camada de Apresentação (Frontend):** Responsável por coletar as entradas dos usuários (nomes e apostas) e exibir o resultado final.
2.  **Camada de Negócio (Backend/POO Core):** Onde as classes `Jogo`, `Dado` e `Jogador` residem. Esta camada implementa os requisitos funcionais e as regras de negócio.

O fluxo do jogo é mediado pela Interface Web, que chama os métodos do objeto `Jogo` (que funciona como a **API de Serviço** do jogo) para processar as ações.

## 2. Requisitos e Regras de Negócio (Lógica Preservada no Backend)

As regras de negócio são mantidas no *backend* e são essenciais para a validação das entradas da Interface Web:

### Requisitos Funcionais (Interação Web)
Estes requisitos descrevem as interações que o usuário realizará no frontend, que acionam os métodos correspondentes no backend POO:
1.  **Inserir Jogadores:** O sistema solicita a quantidade e o nome de até 11 jogadores através de campos de formulário na web.
2.  **Escolher Valor para Apostar:** Cada jogador informa sua aposta (valor entre 2 e 12) através de campos de entrada na web.
3.  **Lançar Dados:** Uma ação ou botão na interface web aciona o lançamento dos dados no backend.
4.  **Apresentar Resultado:** O sistema exibe o resultado da soma dos dados no frontend.
5.  **Informar Jogador Vencedor:** A interface exibe qual jogador venceu ou se a Máquina venceu.

### Regras de Negócio
1.  O máximo de jogadores permitido na entrada de dados é **11**. A cardinalidade da associação entre `Jogo` e `Jogador` é de **1 a 11**.
2.  O valor escolhido para a aposta deve ser validado no backend para estar entre **2 e 12** (resultados possíveis da soma dos dados).
3.  Vários jogadores podem escolher o mesmo valor, e eles dividirão o prêmio em caso de acerto.
4.  Se a **soma do valor das faces dos dados for igual ao valor de uma das apostas**, o sistema informa o jogador vencedor. Caso contrário, é informado que o **computador (Máquina) venceu**.

***

# DIAGRAMA DE CALASSES
<img width="655" height="273" alt="Image" src="https://github.com/user-attachments/assets/b3a501ea-47d3-42ef-a781-6cef04d5b0c6" />


# DIAGRAMA DE CASOS DE USO


<img width="833" height="475" alt="Image" src="https://github.com/user-attachments/assets/12b5861e-e647-41ad-9504-b0a557a366e2" />
