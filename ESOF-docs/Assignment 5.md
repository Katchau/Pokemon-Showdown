# **Engenharia de Software**
# Assignment 5: Software Evolution

## [Pokémon Showdown](https://www.pokemonshowdown.com)

# Falta por a cena do code hub, mas o site tá todo comido 

### Introdução
Para o último relatório da unidade curricular, procedemos à escolha e, mais tarde implementação de um funcionalidade que do nosso ponto de vista é uma adição interessante ao projeto "Pokémon Showdown". Durante o relatório será efetuada uma análise deste processo e no fim, conclusões relevantes relativas ao mesmo.

### 1.Manutenção de Software

No âmbito de avaliar qualidade de código do nosso projeto, foi utilizado o website [BetterCodeHub](bettercodehub.com). O objetivo principal deste é de testar 10 parâmetros distintos de boas condutas de código, especificamente à escrita, organização, legibilidade, e fácil manipulação de código, e atribuir uma nota ao projeto que foi avaliado, mencionando quais fatores precisam de ser melhorados no código para poder obter uma avaliação melhor.

Resumidamente, os parâmetros a serem avaliados são os seguintes:

- Escrever código de forma simples e organizada;
- Evitar repetições e a existência de "muros" de código, bem como mantê-lo legível, sem necessidade de haver código inútil.
- Manter unidades de interface pequenas;
- Separar funcionalidades em módulos
- Arquitetura com componentes independentes e equilibradas
- Boa cobertura de Testes Automáticos

Uma vez que esta ferramenta aínda é recente, foram encontrados vários erros(página não carregava, dava erro a analisar) e limitações(limite de 100 mil linhas de código) que nos obrigaram a efetuar alterações no projeto, de forma a que esta podesse ser executada. Como tal, criámos um novo repositório, onde removemos uma parte do projeto menos importante (classes históricas cuja utilidade é de guardar informação de gerações anteriores para jogar modos antigos de jogo), e obtemos a seguinte avaliação:

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/bch_grade.png?raw=true" />
</p>

Como podemos observar, o *Pokémon Showdown* obteve uma nota intermédia, no limiar daquilo a que poderia chamar-se aceitável. Isto indica que existem aspetos onde este projeto pode melhorar bastante. 
De mencionar que esta avaliação não representa a nota final correta, uma vez que o projeto não foi avaliado na íntegra, como já foi esclarecido no parágrafo anterior, levantando-se assim uma dúvida acerca da legitimidade do teste.

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/testespositivos.png?raw=true" />
</p>

Nesta figura estão presentes todos os testes que obtiveram resultados positivos.

Como podemos observar, o *Pokémon Showdown* mantém unidades de interface pequenas, facilitando a perceptibilidade das funções e a sua reutilização. Apresenta também uma boa organização em termos de módulos/funcionalidades, sendo possível identificar e de separar diferentes módulos de forma mais eficaz. No 3º teste, podemos concluir que o *Pokémon Showdown* possui uma boa organização em termos de componentes, sendo esta feita de acordo com as funções que cada componente é responsável. No 4º teste positivo, podemos verificar que este projeto tem uma base de código pequena, relativamente ao nº de pessoas que colabora no projeto, evitando que a responsabilidade de cada pessoa aumente, mantendo o crescimento do projeto ascendente.

No entanto surge uma dúvida quanto ao último teste, discordando da veracidade deste. Isto porque ao analisar o código que foi omitido verifica-se a existência de código repetido, vários *code smells* (os próprios ficheiros são protótipos de classes "base de dados"), constantes mágicas, entre outros. Ou seja, seria provável que este teste falhásse, caso fosse possível avaliar o projeto na totalidade.


<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/teste1.png?raw=true" />
</p>

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/teste2.png?raw=true" />
</p>

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/teste3.png?raw=true" />
</p>

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/teste6.png?raw=true" />
</p>

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bettercodehub%20results/teste9.png?raw=true" />
</p>


### 2. Introdução de uma Nova Funcionalidade

#### 2.1. Escolha da Funcionalidade a Implementar

A identificação de uma funcionalidade a implementar em Pokémon-Showdown revelou-se um problema mais complicado do que o anticipado. Isto porque o repositório para o qual decidimos contribuir não guarda todo o código relativo ao jogo, mas apenas o código relativo ao servidor. Isto significa que uma funcionalidade implementada no servidor pode não ser visível ao utilizador sem alterações ao código do cliente.

Num esforço para tentar manter as alterações a efetuar contidas apenas no âmbito do repositório que temos vindo a analisar, o nosso foco mudou para os módulos que são completamente implementados no servidor. Esta mudança de perspectiva deixou-nos com apenas duas possibilades realísticas:
* Implementar um novo modo de jogo
* Adicionar um chat plugin

Rapidamente demos conta que implementar um novo modo de jogo não sería uma boa escolha por várias razões, mas principalmente pelo tempo que iria ser necessário para implementar e testar uma alteração desse tamanho. Para além disso era uma modificação que iria necessitar de um consenso entre os principais contribuidores para o projeto, o que nem sempre é fácil conseguir, especialmente com tão pouco tempo para debate.

Posto isto, optamos por introduzir um plugin novo ao chat de Pokémon Showdown. Consideramos que esta escolha nos providenciava com a razão acertada entre complexidade de implementação e utilidade para o projeto, visto que a implementação se previa relativamente simples e as possiblidades eram vastas.

Restava agora escolher qual seria o comando em específico que queriamos introduzir no jogo. Uma situação imediatamente chamou a nossa atenção, fruto da familiaridade que ganhamos com o projeto durante os últimos meses: Todos os dias o servidor reinicia por volta da 00h00 ou 01h00, hora local; Acontece que até ao momento era impossível saber, em determindado momento, qual era a hora atual do servidor. Daí surgiu a ideia de oferecermos ao utilizador a possiblidade de saber a hora do servidor através da escrita de `/servertime` em qualquer sala de chat do jogo.

[Imagem do comando a funcionar]

#### 2.2. Identificação do Código a Modificar

Escolhida a funcionalidade a implementar, era tempo de encontrar no código fonte o sítio adequado para introduzir as alterações.

Tendo em conta que a funcionalidade se relacionava com o chat, começamos a busca pelo local mais lógico: O ficheiro `chat.js` no diretório raiz do projeto.
No cabeçalho deste ficheiro pode ser lido:

> This handles chat and chat commands sent from users to chatrooms and PMs

> Individual commands are put in:
 * chat-commands.js - "core" commands that shouldn't be modified
 * chat-plugins/ - other commands that can be safely modified

> The command API is (mostly) documented in chat-plugins/COMMANDS.md

Isto indicava-nos que este não seria o local adequado para introduzir quaisquer modificações, mas remetia-nos para `chat-plugins/` onde nos dizia que os comandos poderiam ser modificados com segurança. Fornecia ainda outra informação importante, indicando onde se encontrava a documentação da API para introdução de novos comandos.

Seguindo então para `chat-plugins/` deparamo-nos com vários ficheiros. Cada um agrupava comandos que estavam de alguma forma relacionados, por serem semelhantes, por fazerem parte de um mini-jogo, ou por qualquer outra razão que implicasse uma relação lógica entre eles. Após uma breve análise, determinamos que o ficheiro que continha os comandos genéricos e de utilidade se encontravam aglomerados em `info.js`. Era esse, portanto, o ficheiro que viríamos a modificar.

#### 2.3. Implementação da Funcionalidade

Após a identificação do local onde iríamos introduzir as alterações, faltava apenas a parte nuclear deste processo: a codificação da funcionalidade propriamente dita.

Em primeiro lugar, consideramos importante consultar a API de introdução de novos comandos. Interessava-nos descobrir qual era a função a utilizar para mostrar uma mensagem ao utilizador. Sobre isso, encontramos em `COMMANDS.md`:

> Commands have access to the following functions:
* this.sendReply(message)
  * Sends a message back to the room the user typed the command into.

Verificamos assim que enviar uma resposta a um comando de um utilizador era tão simples como utilizar `this.sendReply(message)`.

Agora que sabíamos como enviar a resposta, era altura de obter o conteúdo da resposta em si: a data e hora atual. Para isto utilizamos o objeto `Date` de Javascript, cujo construtor, se chamado sem argumentos, devolve a data e hora no momento da sua evocação. Para imprimir o objeto numa forma legível e de acordo com o fuso horário do servidor, utilizamos a função `toLocaleString()` de `Date`.

Sendo assim, o código resultante de toda a nossa pesquisa e aquele que submetemos para ser revisto e, esperemos, incorporado no projeto foi:

```javascript
'!servertime': true,
servertime: function (target, room, user) {
	    if (!this.runBroadcast()) return;
	    let servertime = new Date();
	    this.sendReplyBox(`Server Time: <b>${servertime.toLocaleString()}</b>`);
},
```

### 3.Submissão do *Pull Request*

### Conclusão

##Trabalho realizado por:

[Ana Rita Torres](https://github.com/AnaRitaTorres): Contribuição 

[Diogo Cepa](https://github.com/dcepa95): Contribuição 

[João Loureiro](https://github.com/Katchau): Contribução 

[João Pedro Silva](https://github.com/joaosilva22): Contribuição 
