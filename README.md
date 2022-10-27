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
insert INTO pessoa (cod,nome,sexo,data_nascimento,cpf,senha)
values(001,'Maria Aparecida','F','2010-11-30','422.521.150-92','123456789'),
	(002,'Antônio Pereira','M','2008-07-31','705.828.720-14','987654321'),
    (003,'José da silva','M','1995-02-10','355.652.980-75','654123987'),
    (004,'Marinalva Santos','F','1979-11-18','092.732.270-66','321789654'),
    (005,'Karina Aparecida','F','2010-09-30','820.795.060-99','852369741'),
    (006,'Marco Dombosco','M','1989-12-27','272.200.330-95','654123987'),
    (007,'Paula Ribeiro','F','2009-10-31','680.129.850-04','741963852'),
    (008,'Guilherme Damaceno','M','1999-08-25','432.162.100-30','741236589');

INSERT INTO musico(cod,cod_pess)
values(001,005),
	(002,004),
    (003,008),
    (004,007),
    (005,006);
	

INSERT into funcionario (cod,cod_pess)
values(001,001),
	(002,002),
    (003,003);

INSERT into contato_tipo(cod,descricao)
values(001,'Telefone'),
(002,'E-mail'),
(003,'Instagram'),
(004,'Facebook');

INSERT into contato(cod,cod_pes,cod_tipo,contato)
values(001,001,001,'(27) 9951-8505'),
	(002,001,002,'maria@gmail.com'),
    (003,002,001,'(63) 98954-7103'),
    (004,002,002,'antonio@gmail.com'),
    (005,003,001,'(64) 98541-8647'),
    (006,003,002,'jose@gmail.com'),
    (007,004,001,'(64) 99541-5684'),
    (008,004,002,'mari@hotmail.com'),
    (009,005,001,'(44) 98574-5443'),
    (010,006,001,'(84) 99782-1715'),
    (011,007,002,'paula@hotmail.com'),
    (012,008,001,'(87) 99816-7329'),
    (013,008,001,'(96) 98685-7688');
	
INSERT into endereco_tipo(cod,descricao)
values (001,'Rua'),
	(002,'Avenida'),
    (003,'Beco'),
    (004,'Condominio');
	
insert into endereco (cod,cod_musi,ender_tipo,endereco)
values(001,001,001,'Artus N°130'),
	(002,002,002,'Aralcaria N°6565'),
    (003,003,003,'Das armadilhas N°9856'),
    (004,004,004,'Paumeiras N°56 apt302'),
    (005,005,001,'Navegantes N°666');
	
INSERT into instrumento_tipo (cod,descricao)
values(001,'Violão'),
	(002,'Guitarra'),
    (003,'Flauta'),
    (004,'Clarinete'),
    (005,'Bateria');
	
INSERT into instrumento(cod,data_aquisicao,modelo,marca,ano_fabric,data_prox_manuten,tipo_instru)
values(001,'2003-10-10','a30506','Polishop','2002','2023-05-01',001),
	(002,'2001-09-08','p486','Duracel','2000','2023-06-05',002),
    (003,'2022-04-01','zip565','Qualy','2022','2023-02-01',003),
    (004,'2021-03-04','asd1512','Garoto','2021','2022-12-12',004),
    (005,'2022-01-05','put12315','Polishop','2019','2023-12-01',005);
	
INSERT into emprestimo(cod,cod_musi,cod_instru,data_inicio,data_fim)
values(001,001,001,'2022-10-27','2022-12-10'),
	(002,002,002,'2022-10-29','2023-10-01'),
    (003,003,003,'2022-10-30','2022-11-05'),
    (004,004,004,'2022-10-31','2022-12-01'),
    (005,005,005,'2022-10-27','2022-10-30');
	
INSERT INTO aprovacao_emprestimo(cod,cod_fun,cod_emp,data_aprov)
values(001,001,001,'2022-10-29'),
	(002,001,002,'2022-10-29'),
    (003,001,003,'2022-10-29'),
    (004,002,004,'2022-10-28'),
    (005,002,002,'2022-10-28');
 
 Link para baixar os arquivos .SQL:
 [trabalho BD.zip](https://github.com/MatheusButter/Trabalho-BD-/files/9882292/trabalho.BD.zip)


## 9.0 Tabelas e principais consultas

### 9.1 Consultas das tabelas com todos os dados inseridos
![1](https://user-images.githubusercontent.com/106558466/198372687-3f3ad636-0317-45e5-be7c-78d64d26bda6.PNG)
![2](https://user-images.githubusercontent.com/106558466/198372693-b93bd877-5cb8-49dc-b5b9-d24d198862d7.PNG)
![3](https://user-images.githubusercontent.com/106558466/198372695-dc20c1b7-9013-4711-8cc9-c38830575c15.PNG)
![4](https://user-images.githubusercontent.com/106558466/198372697-f8bb3441-7dda-4100-9ceb-db61cbafa542.PNG)
![5](https://user-images.githubusercontent.com/106558466/198372698-20aabb95-6b52-4bc9-baaf-4b3143a2f79b.PNG)
![6](https://user-images.githubusercontent.com/106558466/198372700-44e20f5f-4023-482a-9c1b-8f389bc71252.PNG)
![7](https://user-images.githubusercontent.com/106558466/198372703-b774342b-d3bc-4b7f-9b44-cdd0c81f4b56.PNG)
![8](https://user-images.githubusercontent.com/106558466/198372706-7ee558ab-62c9-45e7-85b4-03c820f5dbbc.PNG)
![9](https://user-images.githubusercontent.com/106558466/198372709-6b2de6b5-faf4-441c-a00f-1225cb649826.PNG)
![10](https://user-images.githubusercontent.com/106558466/198372713-6899eb76-2b0e-458c-bac9-297af78fdf38.PNG)
![11](https://user-images.githubusercontent.com/106558466/198372715-110ee1ed-3cea-4ec1-9f8a-4415d440d7f2.PNG)

