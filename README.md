# Trabalho 01 Empréstimo de instrumentos musicais

## Sumário
1. Componentes
2. Introdução e motivação
3. Mini mundo
4. Prototipação, perguntas a serem respondidas e tabela de dados
	- 4.1. Rascunhos básicos da interface (MocKups)
	- 4.2. Quais perguntas podem ser respondidas com o sistema proposto
	- 4.3. Tabela de dados do sistema
5. Modelo conceitual
	- 5.1. Validação do modelo conceitual
	- 5.2. Descrição dos dados
6. Modelo lógico
7. Modelo físico
8. Insert aplicado nas tabelas
9. Tabelas e principais consultas
	- 9.1. Consulta das tabelas com todos os dados inseridos
	- 9.2. Consulta das tabelas com filtros where
	- 9.3. Consultas que usam operadores lógicos, aritméticos e tabelas ou campos renomeados.
	- 9.4. Consultas que usam operadores Like e datas
	- 9.5. Instruções aplicando atualização e exclusão de dados
	- 9.6. Consultas com inner join e order by
	- 9.7. Consultas com Group by e funções de agrupamento
	- 9.8. Consultas com left, right w full join 
	- 9.9. Consultas com self join e view
	- 9.10. Sub consultas
10. Relatórios e gráficos
11. Ajustes da documentação, criação dos slides e vídeo para apresentação 

## 1.0 Componentes
Matheus Butter Dias 2017bsi0181
## 2.0 Introdução e motivação
Este documento apresenta uma descrição geral do sistema para emprestar
instrumentos musicais e seus diagramas necessários para a melhor estruturação do
projeto.O propósito do sistema é informatizar os processos de empréstimo de
instrumentos musicais de uma banda, onde os músicos poderão solicitar o
empréstimo de um instrumento de maneira online, além de lembrar os músicos da
manutenção nos instrumentos.

## 3.0 Mini mundo

É um sistema para a banda, visa facilitar os empréstimos. Dessa maneira, o
sistema precisa controlar os instrumentos através da identificação, tipo (corda,
sopro, percussão, idiofones e eletrofones), data de aquisição, modelo, marca e ano
de lançamento. O sistema também deve permitir o controle dos músicos através do
nome, idade, sexo, email, cpf, endereço e telefone. Também é preciso controlar os
empréstimos dos instrumentos através do atual responsável pelo instrumento, a
data do empréstimo e a data de renovação. Os instrumentos devem passar por
períodos de manutenção, informando a data prevista de realizar os reparos nos
instrumentos e também emitir um alerta com 15 dias de antecedência para que
quem seja o responsável pelo instrumento no momento leve-o para a manutenção.
Esse alerta precisa estar integrado com o WhatsApp para enviar mensagens. Ao
pegar um instrumento emprestado o mesmo deve assinar o termo de
responsabilidade, onde ele se responsabiliza por quaisquer danos ao equipamento.
O sistema não deve permitir que um músico pegue mais do que um instrumento

## 4.0 Prototipação, perguntas a serem respondidas e tabela de dados
### 4.1. Rascunhos básicos da interface (MocKups)
![image](https://user-images.githubusercontent.com/106558466/198100622-44d39bbc-679e-4aaa-8f8c-cf2d8ca66d23.png)
Link para o projeto:https://www.quant-ux.com/#/share.html?h=a2aa10aI9Xh8YmhSPZlNzGyGyB8POz6Vw0ENuiJDCRx5wlysItafwTaooeFK

### 4.2 Quais perguntas podem ser respondidas com o sistema proposto
- a) O sistema proposto poderá fornecer quais tipos de relatórios e informações? 
   * Todo o tipo de relatório que envolva a gestão dos instrumentos e dos músicos cadastrados.
- b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
   * Quais os principais instrumentos emprestados em determinados períodos de tempo.
   * Quais músicos mais pegaram instrumentos emprestados em determinado período de tempo.
   * Qual o tempo médio que cada instrumento ficou emprestado
   * Qual a localidade que contem mais músicos 
   * De quais localidades tem a maior quantidade de músicos que fizeram empréstimos dado um período de tempo
### 4.3 Tabela de dados do sistema

[Tabela emprestimo de instrumentos.xlsx](https://github.com/MatheusButter/Trabalho-BD-/files/9873578/Tabela.emprestimo.de.instrumentos.xlsx)

## 5.0 Modelo Conceitual

![image](https://user-images.githubusercontent.com/106558466/198133158-5e3606ef-fb19-41d7-a13c-e2282a969bf7.png)

### 5.1 Validação do Modelo Conceitual

O professo sugeriu uma pequena alterações no modelo que já foram efetuadas

### 5.2 Descrição dos dados
* [Pessoa] : [Armazena os dados pessoais de cada pessoa cadastrada no sistema]
* [Musico] : [Identifica a pessoa cadastrada no sistema como músico]
* [Funcionario] : [Identifica a pessoa cadastrada no sistema como funcionário da banda]
* [Contato] : [Registra os contatos das pessoas adastradas no sistema]
* [Contato_tipo] : [Registra os tipos de contato que as pessoas podem ter]
* [Endereco] : [Registra os endereços dos músicos]
* [Endereco_tipo] : [Registra os tipos de endereços que os músicos possam ter]	
* [Instrumento] : [Registra todos os instrumentos que a banda tem]
* [Instrumento_tipo] : [Registra todos os tipos de instrumentos que a banda tem ]	
* [Solicita] : [Gerencia uma solicitação de empréstimo de um instrumento]	

## 6.0 Modelo lógico

![image](https://user-images.githubusercontent.com/106558466/198136497-00a3e7c7-66f9-45f8-8815-a6c95a051c8f.png)

## 7.0 Modelo Físico

CREATE TABLE CONTATO_TIPO(
	cod INT,
    descricao varchar(100),
    
    PRIMARY key (cod)
);

create table contato(
	cod int,
    cod_pes int,
    cod_tipo int,
    contato varchar(100),
    
    PRIMARY key (cod),
    FOREIGN key (cod_tipo) REFERENCES contato_tipo(cod)
);

create table pessoa(
	cod int,
    nome varchar(100),
    sexo char(1),
    data_nascimento date,
    cpf varchar(100),
    senha varchar(100),
    
    PRIMARY key (cod)
);

alter TABLE contato add FOREIGN key (cod_pes) REFERENCES pessoa(cod);

create table musico(
	cod int,
    cod_pess int,
    
    PRIMARY key(cod),
    FOREIGN key(cod_pess) REFERENCES pessoa(cod)
);

create table funcionario( 
	cod int,
	cod_pess int,
	PRIMARY KEY(cod),
	FOREIGN key (cod_pess) REFERENCES pessoa(cod)
 );
 
 CREATE table endereco_tipo(
	cod int,
    descricao varchar(100),
    
    PRIMARY key (cod)
);

CREATE table endereco(
	cod int,
    cod_musi int,
    ender_tipo int,
    endereco varchar(100),
    
    PRIMARY key (cod),
    FOREIGN key (cod_musi) REFERENCES musico(cod),
    FOREIGN key (ender_tipo) REFERENCES endereco_tipo(cod)
    
);

CREATE table instrumento_tipo(
	cod int,
    descricao varchar(100),
    
    PRIMARY key(cod)
    
);

CREATE table instrumento (
	cod int,
    data_aquisicao date,
    modelo varchar(100),
    marca varchar(100),
    ano_fabric varchar(5),
    data_prox_manuten date,
    tipo_instru int,
    
    PRIMARY key(cod),
    
    FOREIGN key (tipo_instru) REFERENCES instrumento_tipo(cod)
    

);

create table emprestimo(
	cod int,
    cod_musi int,
    cod_instru int,
    data_inicio date,
    data_fim date,
    
    PRIMARY key (cod),
    FOREIGN key (cod_musi) REFERENCES musico(cod),
    FOREIGN key (cod_instru) REFERENCES instrumento(cod)
);


create table aprovacao_emprestimo(
	cod int,
    cod_fun int,
    cod_emp int,
    data_aprov date,
    
    PRIMARY key (cod),
    FOREIGN key (cod_fun) REFERENCES funcionario(cod),
    FOREIGN key (cod_emp) REFERENCES emprestimo(cod)
);


## 8.0 Insert aplicado nas tabelas do banco de dados
