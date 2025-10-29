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

# 3. Modelagem de Classes POO (O Core do Jogo)

O projeto do Jogo de Dados é estruturado em três classes candidatas principais: `Jogador`, `Dado` e `Jogo`. Esta modelagem de classes, atributos e associações representa a arquitetura de mais alto nível do sistema.

## 3.1 Classes e Atributos Definidos

O modelo conceitual define as entidades e os tipos de seus atributos, detalhando os dados necessários para a execução do jogo:

| Classe | Atributos (Tipo) | Propósito |
| :--- | :--- | :--- |
| **Jogador** | `nome: String`, `valorAposta: int` | Representa um participante do jogo. |
| **Dado** | `valorFace: int` | Representa um dos dois dados lançados. |
| **Jogo** | `qtdJogadores: int`, `resultado: int` | Gerencia o fluxo e armazena o estado geral da partida. |

## 3.2 Relações e Comunicação entre Classes

A comunicação entre as classes é essencial para que o sistema funcione. No diagrama de classes, é necessário definir **variáveis que interliguem** as classes, chamadas de **objetos**.

Para que a classe **`Jogo`** possa calcular o resultado e determinar o vencedor, ela deve acessar informações definidas em outras classes:

*   **Acesso ao Dado:** `Jogo` precisa saber o `valorFace` de cada `Dado`.
*   **Acesso ao Jogador:** `Jogo` precisa saber o `valorAposta` e o `nome` de cada `Jogador`.

Na implementação, a classe `Jogo` é interligada às outras classes através da declaração de objetos como atributos:

| Classe Controladora | Atributos Objeto | Tipo da Classe Associada |
| :--- | :--- | :--- |
| **Jogo** | `dado1`, `dado2` | `Dado` |
| **Jogo** | `jogadores` | `Jogador[]` (Vetor de Objetos) |

Os objetos são as classes em execução. Por exemplo, no diagrama de objetos de uma partida, são vistas instâncias como `dado1:Dado` e `jogador:Jogador`.

## 3.3 Cardinalidade (Multiplicidade) das Associações

A cardinalidade define as restrições quantitativas (multiplicidade) que devem ser consideradas na implementação, indicando quantas instâncias de uma classe podem estar associadas a uma instância de outra classe.

As associações e suas cardinalidades no Jogo de Dados são:

| Associação | Cardinalidade | Restrição de Implementação |
| :--- | :--- | :--- |
| **Jogo** **lança** **Dado** | Exatamente **2** | Uma instância de `Jogo` deve associar-se a 2 instâncias de `Dado` (`dado1` e `dado2`). |
| **Jogo** **joga** **Jogador** | De **1 a 11** (`1...11`) | O número máximo de jogadores é **11**. |
## 4. Fluxo de Execução Web

O fluxo de execução, coordenado pela classe principal no ambiente POO, seria mapeado para rotas ou *endpoints* da aplicação web:

1.  **Setup (Input Web):** A Interface Web chama o método `inserirJogadores()` para inicializar o array de objetos `Jogador`.
2.  **Apostas (Input Web):** A Interface Web coleta as apostas e chama `inserirApostas()`, utilizando `setValorAposta()` para atribuir o valor a cada objeto `Jogador`.
3.  **Ação do Jogo (Requisição):** O usuário solicita o lançamento dos dados. O backend chama `lancarDados()`, que cria os objetos `Dado` e utiliza `setValorFace()` para gerar os valores aleatórios.
4.  **Processamento:** O backend executa `mostrarResultado()` (calculando a soma das faces) e `mostrarVencedor()` (comparando o resultado com `getValorAposta()` de cada jogador).
5.  **Output (Exibição Web):** O resultado (valor da soma e o nome do vencedor ou a vitória da Máquina) é retornado ao frontend para exibição.

# DIAGRAMA DE CALASSES
  d_classes.PNG

# DIAGRAMA DE CASOS DE USO

 d_casos_uso.PNG
