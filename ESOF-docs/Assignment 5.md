# **Engenharia de Software**
# Assignment 5: Software Evolution

## [Pokémon Showdown](https://www.pokemonshowdown.com)

### Introdução
Para o último relatório da unidade curricular, procedemos à escolha e, mais tarde implementação de um funcionalidade que do nosso ponto de vista é uma adição interessante ao projeto "Pokémon Showdown". Durante o relatório será efetuada uma análise deste processo e no fim, conclusões relevantes relativas ao mesmo.

### 1.Identificação da Funcionalidade

#### 1.1. Escolha da Funcionalidade a Implementar

A identificação de uma funcionalidade a implementar em Pokémon-Showdown revelou-se um problema mais complicado do que o anticipado. Isto porque o repositório para o qual decidimos contribuir não guarda todo o código relativo ao jogo, mas apenas o código relativo ao servidor. Isto significa que uma funcionalidade implementada no servidor pode não ser visível ao utilizador sem alterações ao código do cliente.

Num esforço para tentar manter as alterações a efetuar contidas apenas no âmbito do repositório que temos vindo a analisar, o nosso foco mudou para os módulos que são completamente implementados no servidor. Esta mudança de perspectiva deixou-nos com apenas duas possibilades realísticas:
* Implementar um novo modo de jogo
* Adicionar um chat plugin

Rapidamente demos conta que implementar um novo modo de jogo não sería uma boa escolha por várias razões, mas principalmente pelo tempo que iria ser necessário para implementar e testar uma alteração desse tamanho. Para além disso era uma modificação que iria necessitar de um consenso entre os principais contribuidores para o projeto, o que nem sempre é fácil conseguir, especialmente com tão pouco tempo para debate.

Posto isto, optamos por introduzir um plugin novo ao chat de Pokémon Showdown. Consideramos que esta escolha nos providenciava com a razão acertada entre complexidade de implementação e utilidade para o projeto, visto que a implementação se previa relativamente simples e as possiblidades eram vastas.

Restava agora escolher qual seria o comando em específico que queriamos introduzir no jogo. Uma situação imediatamente chamou a nossa atenção, fruto da familiaridade que ganhamos com o projeto durante os últimos meses: Todos os dias o servidor reinicia por volta da 00h00 ou 01h00, hora local; Acontece que até ao momento era impossível saber, em determindado momento, qual era a hora atual do servidor. Daí surgiu a ideia de oferecermos ao utilizador a possiblidade de saber a hora do servidor através da escrita de `/servertime` em qualquer sala de chat do jogo.

#### 1.2. Identificação do Código a Modificar

Escolhida a funcionalidade a implementar, era tempo de encontrar no código fonte o sítio adequado para introduzir as alterações.

Tendo em conta que a funcionalidade se relacionava com o chat, começamos a busca pelo local mais lógico: O ficheiro `chat.js` no diretório raiz do projeto.
No cabeçalho deste ficheiro pode ser lido:

> This handles chat and chat commands sent from users to chatrooms and PMs

Individual commands are put in:
 *   chat-commands.js - "core" commands that shouldn't be modified
 *   chat-plugins/ - other commands that can be safely modified

### 2.Submissão do *Pull Request*

### Conclusão

##Trabalho realizado por:

[Ana Rita Torres](https://github.com/AnaRitaTorres): Contribuição 

[Diogo Cepa](https://github.com/dcepa95): Contribuição 

[João Loureiro](https://github.com/Katchau): Contribução 

[João Pedro Silva](https://github.com/joaosilva22): Contribuição 
