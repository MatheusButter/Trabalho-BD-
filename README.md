TRABALHO 01: Título do Trabalho
Trabalho desenvolvido durante a disciplina de BD1

Sumário
1. COMPONENTES
Integrantes do grupo
primeiro_componente_do_grupo:email_primeiro_componente@dominio.com
segundo_componente_do_grupo:email_segundo_componente@dominio.com
...

2.INTRODUÇÃO E MOTIVAÇÃO
Este documento contém a especificação do projeto do banco de dados
e motivação da escolha realizada.

A empresa "Devcom Projetos" visa colaborar com desenvolvimento de projetos para uma sociedade melhor. Sabendo-se dos desafios para gerenciar projetos dentro de uma empresa e visando unir as informações relativas a funcionários, departamentos e projetos em um mesmo local, ficamos motivados com o desenvolvimento deste sistema. O Sistema "Devcom" tem como objetivo gerenciar todas as informações ao desenvolvimento das atividades de projetos em diversas localidades do país. Para realizar suas operações adequadamente e empresa necessita que sistema que armazene informações relativas aos Projetos, Departamentos e Empregados, além de também armazenar dados sobre Dependentes e Históricos de Salário dos empregados. O sistema deverá gerar um conjunto de relatórios que por sua vez atenderá os anseios da empresa em questão.

3.MINI-MUNDO
Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar)
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente real)
Descrição textual das regras de negócio definidas como um subconjunto do mundo real cujos elementos são propriedades que desejamos incluir, processar, armazenar, gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

O sistema proposto para a "Devcom Projetos conterá as informacões aqui detalhadas. Dos Projetos serão armazenados o número, nome e cidade. Dos Departamentos serão armazenados o número e nome. O cliente destacou que cada projeto pode ter vários departamentos auxiliando no seu desenvolvimento, e cada departamento pode estar envolvido em vários projetos. Os dados relativos aos empregados que serão armazenados são: rg, nome, cpf, salário, data inicial do salario e supervisor de cada empregado. É importante destacar que cada empregado pode ser supervisionado por outro empregado, e obrigatoriamente deve estar alocado a um único departamento, mas pode gerenciar vários departamentos ou não gerenciar nenhum. Um empregado também pode participar de vários projetos, caso seja necessário, mas não precisa obrigatoriamente estar alocado em algum projeto. Com relação aos dependentes serão armazenadas as informações de nome do dependente, data de nascimento, sexo e grau de parentesco. Cada empregado pode ter vários dependentes, mas um dependente esta associado apenas a um único empregado. Com relação ao histórico de salário devemos armazenar as informações de valor do salário, data de início do salário no período e data final do salário no período. É importante lembrar que cada funcionario pode ter diversos eventos de histórico de salário associados a ele visto que este dado pode ser alterado várias vezes.

4.PROTOTIPAÇÃO, PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS
4.1 RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)
Neste ponto a codificação não e necessária, somente as ideias de telas devem ser criadas, o princípio aqui é pensar na criação da interface para identificar possíveis informações a serem armazenadas ou descartadas

Sugestão: https://balsamiq.com/products/mockups/

Alt text Arquivo PDF do Protótipo Balsamiq feito para Empresa Devcom

4.2 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
A Empresa DevCom precisa inicialmente dos seguintes relatórios:

Relatório que mostre o nome de cada supervisor(a) e a quantidade de empregados supervisionados.
Relatório relativo aos os supervisores e supervisionados. O resultado deve conter o nome do supervisor e nome do supervisionado além da quantidade total de horas que cada supervisionado tem alocada aos projetos existentes na empresa.
Relatorio que mostre para cada linha obtida o nome do departamento, o valor individual de cada salario existente no departamento e a média geral de salarios dentre todos os empregados. Os resultados devem ser apresentados ordenados por departamento.
Relatório que mostre as informações relacionadas a todos empregados de empresa (sem excluir ninguém). As linhas resultantes devem conter informações sobre: rg, nome, salario do empregado, data de início do salario atual, nomes dos projetos que participa, quantidade de horas e localização nos referidos projetos, numero e nome dos departamentos aos quais está alocado, informações do historico de salário como inicio, fim, e valores de salarios antigos que foram inclusos na referida tabela (caso possuam informações na mesma), além de todas informações relativas aos dependentes.
Observações:
a) perceba que este relatório pode conter linhas com alguns dados repetidos (mas não todos).
b) para os empregados que não possuirem alguma destas informações o valor no registro deve aparecer sem informação/nulo.
Relatório que obtenha a frequencia absoluta e frequencia relativa da quantidade de cpfs únicos no relatório anterior. Apresente os resultados ordenados de forma decrescente pela frequencia relativa.
4.3 TABELA DE DADOS DO SISTEMA:
a) Esta tabela deve conter todos os atributos do sistema e um mínimo de 10 linhas/registros de dados.
b) Esta tabela tem a intenção de simular um relatório com todos os dados que serão armazenados 
Exemplo de Tabela de dados da Empresa Devcom

5.MODELO CONCEITUAL
A) Utilizar a Notação adequada (Preferencialmente utilizar o BR Modelo 3)
B) O mínimo de entidades do modelo conceitual pare este trabalho será igual a 3 e o Máximo 5.
    * informe quais são as 3 principais entidades do sistema em densenvolvimento<br>(se houverem mais de 3 entidades, pense na importância da entidade para o sistema)       
C) Principais fluxos de informação/entidades do sistema (mínimo 3). <br>Dica: normalmente estes fluxos estão associados as tabelas que conterão maior quantidade de dados 
D) Qualidade e Clareza
    Garantir que a semântica dos atributos seja clara no esquema (nomes coerentes com os dados).
    Criar o esquema de forma a garantir a redução de informação redundante, possibilidade de valores null, 
    e tuplas falsas (Aplicar os conceitos de normalização abordados).   
Alt text

5.1 Validação do Modelo Conceitual
[Grupo01]: [Nomes dos que participaram na avaliação]
[Grupo02]: [Nomes dos que participaram na avaliação]
5.2 Descrição dos dados
[objeto]: [descrição do objeto]

EXEMPLO:
CLIENTE: Tabela que armazena as informações relativas ao cliente<br>
CPF: campo que armazena o número de Cadastro de Pessoa Física para cada cliente da empresa.<br>
6 MODELO LÓGICO
    a) inclusão do esquema lógico do banco de dados
    b) verificação de correspondencia com o modelo conceitual 
    (não serão aceitos modelos que não estejam em conformidade)
7 MODELO FÍSICO
    a) inclusão das instruções de criacão das estruturas em SQL/DDL 
    (criação de tabelas, alterações, etc..) 
8 INSERT APLICADO NAS TABELAS DO BANCO DE DADOS
    a) inclusão das instruções de inserção dos dados nas tabelas criadas pelo script de modelo físico
    (Drop para exclusão de tabelas + create definição de para tabelas e estruturas de dados + insert para dados a serem inseridos)
    b) Criar um novo banco de dados para testar a restauracao 
    (em caso de falha na restauração o grupo não pontuará neste quesito)
    c) formato .SQL
9 TABELAS E PRINCIPAIS CONSULTAS
OBS: Incluir para cada tópico as instruções SQL + imagens (print da tela) mostrando os resultados.<br>
9.1 CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas)
