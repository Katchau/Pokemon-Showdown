# **Engenharia de Software**
# Assignment 4: Software Tests

## [Pokémon Showdown](https://www.pokemonshowdown.com)

### Introdução
 Os testes de *software* têm como objetivo principal verificar até que nível um artifacto de *software*, podendo este ser: um sistema de *software*, um módulo de *software*, entre outros, suporta um teste em determinado contexto. No caso de a testabilidade do artifacto ser elevada significa que é mais simples encontrar erros e falhas através de *testing*. 

### 1.Grau de Testabilidade

#### 1.1.Controlabilidade
A controlabilidade determina o grau de possibilidade do teste a ser executado.

#### 1.2.Observabilidade

#### 1.3.Isolabilidade
#### 1.4.Separação de responsabilidades
#### 1.5.Heterogeneidade

### 2.Estatísticas de Teste

No *Pokémon Showdown*, os testes efetuados pelos contribuidores estão presentes na pasta "test" do projeto. Dentro desta, estão presentes de forma organizada por tópicos de interesse distintos (informação relativa a abilidades numa pasta, ataques noutra, etc..).
Para poder correr estes testes, é utilizado o programa *node.js*, que também é utilizado para poder correr o projeto. Este consegue correr testes graças à existência do plugin *Mocha*.

O comando que executa todos os testes unitários do projeto em análise é : *npm test*. Ao correr este é impressa uma lista onde estão descritos todos os testes, neste caso os que passaram(762) e os que ficaram pendentes(6). A imagem que se segue é representativa disto:

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/npm%20test%202.png" />
</p>

É possível também correr apenas um ficheiro de testes, tendo de se deslocar na linha de comandos à pasta desejada, e indicar um ficheiro de testes em específico.

Um dos problemas principais do nosso projeto, em termos de testes, é a negligência da *coverage* do projeto uma vez que  os testes realizados são fruto de *black box testing*.
Isto é, apenas testam funções que dizem respeito às funcionabilidades que o projeto fornece aos utilizadores. Ou seja, apenas avaliam as funções principais do *Pokémon Showdown*, como por exemplo, mecânicas de combate, se as abilidades funcionam bem, etc.. . Certos aspectos como a criação de um novo *Pokémon*, ou a criação de uma nova abilidade, aspectos que não são fruto de interação com o utilizador, são ignorados em questão de testes.

Desta forma, não é efetuado qualquer tipo de *white box testing*, sendo que a coverage geral do projeto, como podemos observar, é bastante baixa:

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/coverage.png" />
</p>


### 3.Correção do Bug


Para compreender o problema que procuramos resolver, é necessário ter o conhecimento de algumas das peculiaridades dos jogos Pokémon, e em específico das versões Sun e Moon para a Nintendo 3DS. Tentaremos, portanto, apresentá-las de uma forma abreviada:

- Nem todos os Pokémon estão disponíveis nas versões Sun e Moon.
- Nem todos os ataques de Pokémon estão disponíveis nas versões Sun e Moon.
- Alguns Pokémon aprendem ataques exclusivamente a partir de outros Pokémon.
- Os Pokémons que não estão disponíveis podem ser obtidos através de um mecanismo de transferência de versões anteriores, chamado de Pokebank.
- O Pokebank ainda não se encontra disponível nas versões Sun e Moon.

Esta conjugação de restrições causa que, em determinados casos, alguns ataques que os Pokémon poderiam utilizar em teoria não podem ser aprendidos por estes já que o Pokémon ou Pokémons que os poderiam ensinar ainda não se encontram presentes no jogo, e ainda não podem ser transferidos.

Acontece que em Pókemon Showdown, mais especificamente no formato 'Gen7 OU', que pretende ser uma simulação fiel dos jogos para Nintendo 3DS, este comportamento não se verificava. Alguns Pokémon utilizavam ataques aos quais não deveriam ter acesso, pelo facto de o Pokebank ainda não estar disponível.

Após alguma análise, verificamos que este problema acontecia porque, aquando da criação de uma equipa, a validação dos ataques de cada Pokémon não tinha em conta a sua disponibilidade na geração e no modo de jogo escolhido. Propusemo-nos então a modificar o algoritmo de validação de ataques para ter em conta esta situação. 

Os passos para resolver este problema seriam, então, para cada ataque a validar:

1. Realizar a verificação apenas em modos de jogo da última geração e que não permitam transferência de Pokémon de gerações anteriores.
2. Verificar se o ataque pode ser ensinado ao Pokémon por qualquer outro presente na geração escolhida.
3. Marcar o ataque como ilegal se o nenhum Pokémon for encontrado no passo dois.

As modificações que fizemos ao código para implementar esta solução podem ser consultadas na imagem seguinte.

<p align="center">
   <img src="https://github.com/Katchau/Pokemon-Showdown/blob/master/ESOF-docs/Resources/bugfix.png?raw=true" />
</p>

No processo de resolução deste problema verificamos alguns problemas no que diz respeito ao armazenamento de dados. Todos a informação relativa ao jogo encontra-se em ficheiros mal documentados, mantidos à mão e frequentemente modificados, o que aumenta bastante a probabilidade de problemas como o que resolvemos desta vez se repetirem no futuro.

### Conclusão

##Trabalho realizado por:

[Ana Rita Torres](https://github.com/AnaRitaTorres): Contribuição 25%

[Diogo Cepa](https://github.com/dcepa95): Contribuição 25%

[João Loureiro](https://github.com/Katchau): Contribução 25%

[João Pedro Silva](https://github.com/joaosilva22): Contribuição 25% 
