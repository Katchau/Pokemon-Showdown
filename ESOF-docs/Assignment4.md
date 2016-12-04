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

#### 2.1.Testes Unitários
Os testes unitários testam as menores unidades de *software* desenvolvidas, sendo estas pequenas secções de código ou a unidade definida para o projeto em estudo. O principal objetivo, deste tipo de *testing* é encontrar falhas de funcionamento numa pequena parte do sistema funcionando independentemente do todo.

#### 2.2.Cobertura de Código

#### 2.3.Testes de Integração
Os testes de integração visam avaliar a interação entre os componentes de *software* e *hardware*, posto isto, o seu principal desafio é encontrar erros nas unidades de interface.

#### 2.4.Testes de Sistema
Os testes de sistema consideram a robustez deste, verificando se age em conformidade com requerimentos funcionais de comportamento e qualidade.

#### 2.5.Testes de Aceitação
Os testes de aceitação são chamados de testes formais, uma vez que têm de estar de acordo com os seus critérios de aceitação, primeiramente e de seguida, são alvo de uma aceitação ou não por parte do cliente final.

#### 2.6.Testes de Regressão
Os testes de regressão são realizados de forma seletiva sobre determinada secção de código para garantir que qualquer alteração neste não causou nenhum distúrbio ou mau funcionamento do que estava, anteriormente, imlplementado.

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

[Ana Rita Torres](https://github.com/AnaRitaTorres): Contribuição 

[Diogo Cepa](https://github.com/dcepa95): Contribuição 

[João Loureiro](https://github.com/Katchau): Contribução 

[João Pedro Silva](https://github.com/joaosilva22): Contribuição 
