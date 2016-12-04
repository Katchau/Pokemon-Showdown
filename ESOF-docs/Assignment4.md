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

Na demanda da pesquisa por um bug no nosso projeto, começámos por simular vários cenários de combate, na esperança de encontrar alguma falha, uma vez que este é um dos elementos principais do servidor, sendo assim uma parte sensível a bugs.
Inicialmente encontramos um bug visual, relativo a uma nova mecânica de ataques denominada por *z-moves*. No entanto, este tratava-se de um bug do client, e não do servidor.
Depois, decidímos por apenas corrigir um bug que se encontrava nos issues do projeto, mas com insucesso, visto que muitos deles já tinham sido resolvidos, ou então não eram bugs, tendo mesmo perdido tempo a resolver um destes *fake bugs*.
Durante este ultimo , acabámos por encontrar um bug, tendo sido resolvido com sucesso.

Para poder explicar o bug, é necessário saber 2 conceitos/informações:

- Como já foi referido nos projetos anteriores, para poder efetuar combates com outras pessoas, o utilizador tem de escolher determinado formato, aqual todos os elementos da equipa devem respeitar as regras deste.
 Para tal, uma das condições necessárias é que todos os ataques escolhidos sejam válidos no formato. Dando um exemplo, o Charizard em 90% dos formatos, nunca pode utilizar o ataque *Surf*.
Na verificação da validação de um ataque, salvo os formatos onde tudo é válido, é verificado se este é aprendido por evolução ou por *level up* na mesma geração do formato, por transferência de gerações anteriores, por *breed* (método de acasalamento de *Pokémons*) entre *Pokémons* válidos, e se é possível transferir/existir os ataques ou pokémons na geração selecionada.

- O Pokémon Shodown é desprovido de uma base de dados bem estruturada e organizada, isto é, possui um conjunto de *Data Classes* (classes cuja função é de guardarem informação para ser usada por outras classes), sendo impossível em certas situações verificar a existência de certas relações entre classes, obrigando à existência de criação de novas funções.

Como tal, para verificar se um *Pokémon* pode utilizar um ataque que aprende através do método de *breeding*, teria de verificar se o *Pokémon* que permite realizar *breed* é válido no formato que se pretende jogar, e se este aprende o ataque de forma válida. No entanto, com o estado atual do projeto é impossível verificar isto de forma automática, obriga a que sejam feita alterações necessárias à mão, ou alterando a "base de dados", ou criar novas funções

Para resolver o bug, adicionámos as seguintes linhas de código:

por aqui imagem lmao

Já faço isto, uma vez que atualizar informação de forma manual de 802 Pokémons é um processo dispendioso, podendo facilmente esquecer de atualizar todos os ataques.
É de igual forma difícil de se deparar com um bug desta natureza, devido outra vez à quantidade enorme de Pokémons e ataques herdados, uma vez que não são efetuados testes individuáis de cada um.

### Conclusão

##Trabalho realizado por:

[Ana Rita Torres](https://github.com/AnaRitaTorres): Contribuição 

[Diogo Cepa](https://github.com/dcepa95): Contribuição 

[João Loureiro](https://github.com/Katchau): Contribução 

[João Pedro Silva](https://github.com/joaosilva22): Contribuição 
