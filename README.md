# JogoDeDados
# JOGO DE DADOS (PROGRAMAÇÃO ORIENTADA A OBJETOS)

## Visão Geral do Sistema

Este projeto implementa um **Jogo de Dados** utilizando conceitos de Programação Orientada a Objetos (POO). O sistema consiste em **dois dados** e uma quantidade $X$ de jogadores, que é informada no início do jogo.

O fluxo principal do jogo é o seguinte:
1. Cada jogador escolhe um valor para apostar.
2. Após todos os jogadores informarem suas apostas, os dados são lançados.
3. O sistema apresenta o resultado.
4. Se a **soma do valor das faces dos dados for igual ao valor de uma das apostas**, o sistema informa qual o jogador vencedor.
5. Caso nenhum jogador acerte o valor da soma, é informado que o **computador (Máquina) venceu**.

## Requisitos e Regras de Negócio

### Requisitos Funcionais
1. Inserir Jogadores
2. Escolher Valor para Apostar
3. Lançar Dados
4. Apresentar Resultado
5. Informar Jogador Vencedor

### Regras de Negócio
1. O máximo de jogadores é **11**.
2. O valor escolhido para a aposta deve estar entre **2 e 12**, que são os resultados possíveis da soma dos dados.
3. Um jogador pode escolher um valor já escolhido por outro, o que implica que eles podem **dividir o prêmio**.

## Modelagem Conceitual e Classes

O sistema foi modelado usando classes candidatas que representam as entidades do problema: `Jogador`, `Dado` e `Jogo`. A modelagem detalha classes, atributos, associações e métodos.

### Classes e Atributos
| Classe | Atributos (Tipo) |
| :--- | :--- |
| **Jogador** | `nome: String`, `valorAposta: int` |
| **Dado** | `valorFace: int` |
| **Jogo** | `qtdJogadores: int`, `resultado: int`, `dado1: Dado`, `dado2: Dado`, `jogadores: Jogador[]` |

### Cardinalidade das Associações
A cardinalidade informa restrições importantes para a implementação:
*   O objeto `Jogo` associa-se a **2** instâncias de `Dado`.
*   O objeto `Jogo` associa-se a **1 a 11** instâncias de `Jogador` (`1...11`).

**Nota sobre a Comunicação entre Classes:** Para que a classe `Jogo` possa calcular o resultado e verificar o vencedor, ela utiliza **objetos** (variáveis que interligam classes). Por exemplo, a classe `Jogo` precisa saber o `valorFace` dos dados e o `valorAposta` e `nome` de cada `Jogador`.

### Métodos (Operações)

Os métodos (operações) são bem específicos, seguindo o Princípio de Responsabilidade Única (Single Responsibility Principle):

| Classe | Métodos Principais | Propósito (Exemplos) |
| :--- | :--- | :--- |
| **Jogador** | `getNome():String`, `setNome(String)`, `getValorAposta():int`, `setValorAposta(int)` | Acesso e modificação de atributos (Métodos Get e Set). |
| **Dado** | `getValorFace():int`, `setValorFace()` | O método `setValorFace()` implementa o lançamento, gerando um valor aleatório entre 1 e 6. |
| **Jogo** | `inserirJogadores()`, `inserirApostas()`, `lancarDados()`, `mostrarResultado()`, `mostrarVencedor()` | Gerenciam o fluxo do jogo e a lógica de aposta/resultado. |

## Fluxo de Execução

A classe principal (`Principal.java`) coordena a execução do jogo chamando os métodos da classe `Jogo` na ordem correta:

1. **Inicialização do Jogo:** Criação de um objeto `Jogo`.
2. **`run.inserirJogadores()`:** Solicita e armazena a quantidade e o nome de cada jogador.
3. **`run.inserirApostas()`:** Solicita a aposta de cada jogador (valor entre 2 e 12).
4. **`run.lancarDados()`:** Cria os objetos `Dado` e realiza o lançamento para obter os valores das faces.
5. **`run.mostrarResultado()`:** Calcula a soma dos dados e a exibe.
6. **`run.mostrarVencedor()`:** Verifica se algum jogador acertou o resultado, informando o vencedor ou a vitória da Máquina.
