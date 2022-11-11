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

![image](https://user-images.githubusercontent.com/106558466/200628949-796744cf-28e2-4f2a-8458-3cf99eeb11b1.png)

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

![image](https://user-images.githubusercontent.com/106558466/200631022-962a937c-68ed-4709-a48c-2685b1194617.png)


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
    FOREIGN key (cod_musi) REFERENCES pessoa(cod),
    FOREIGN key (ender_tipo) REFERENCES endereco_tipo(cod)
    
);

CREATE table instrumento_tipo(
	cod int,
    descricao varchar(100),
    
    PRIMARY key(cod)
);

CREATE table marca(
	cod int,
    descricao varchar(100),
    
    PRIMARY key(cod)
);

CREATE table modelo(
	cod int,
    descricao varchar(100),
    
    PRIMARY key(cod)
);

CREATE table instrumento (
	cod int,
    data_aquisicao date,
    cod_modelo int,
    cod_marca int,
    ano_fabric varchar(5),
    data_prox_manuten date,
    tipo_instru int,
    
    PRIMARY key(cod),
    
    FOREIGN key (tipo_instru) REFERENCES instrumento_tipo(cod),
	FOREIGN key (cod_modelo) REFERENCES modelo(cod),
	FOREIGN key (cod_marca) REFERENCES marca(cod)
);

create table emprestimo(
	cod int,
    cod_musi int,
    cod_instru int,
    data_inicio date,
    data_fim date,
    
    PRIMARY key (cod),
    FOREIGN key (cod_musi) REFERENCES pessoa(cod),
    FOREIGN key (cod_instru) REFERENCES instrumento(cod)
);


create table aprovacao_emprestimo(
	cod int,
    cod_fun int,
    cod_emp int,
    data_aprov date,
    
    PRIMARY key (cod),
    FOREIGN key (cod_fun) REFERENCES pessoa(cod),
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
	
INSERT into marca (cod,descricao)
values(001,'Polishop'),
	(002,'Duracel'),
    (003,'Qualy'),
    (004,'Garoto'),
    (005,'AOC');	
	
INSERT into modelo (cod,descricao)
values(001,'a30506'),
	(002,'p486'),
    (003,'zip565'),
    (004,'asd1512'),
    (005,'put12315');
	
INSERT into instrumento(cod,data_aquisicao,cod_modelo,cod_marca,ano_fabric,data_prox_manuten,tipo_instru)
values(001,'2003-10-10',001,001,'2002','2023-05-01',001),
	(002,'2001-09-08',002,002,'2000','2023-06-05',002),
    (003,'2022-04-01',003,003,'2022','2023-02-01',003),
    (004,'2021-03-04',004,004,'2021','2022-12-12',004),
    (005,'2022-01-05',005,001,'2019','2023-12-01',005),
	(006,'2001-10-10',001,001,'2002','2023-01-02',001),
	(007,'2002-10-10',001,001,'2002','2023-04-02',001),
	(008,'2004-10-10',001,001,'2002','2023-08-03',001);
	
INSERT into emprestimo(cod,cod_musi,cod_instru,data_inicio,data_fim)
values(001,001,001,'2022-10-27','2022-12-10'),
	(002,002,002,'2022-10-29','2023-10-01'),
    (003,003,003,'2022-10-30','2022-11-05'),
    (004,004,004,'2022-10-31','2022-12-01'),
    (005,005,005,'2022-10-27','2022-10-30'),
	(006,001,006,'2022-10-28','2022-11-30'),
	(007,003,007,'2022-10-28','2022-11-11'),
	(008,004,008,'2022-10-28','2022-11-11');
	
INSERT INTO aprovacao_emprestimo(cod,cod_fun,cod_emp,data_aprov)
values(001,007,001,'2022-10-29'),
	(002,007,002,'2022-10-29'),
    (003,007,003,'2022-10-29'),
    (004,008,004,'2022-10-28'),
    (005,008,005,'2022-10-28'),
	(006,008,006,'2022-10-28'),
	(007,008,007,'2022-10-28'),
	(008,008,008,'2022-10-28');
 
 Link para baixar os arquivos .SQL:
 [sqls.zip](https://github.com/MatheusButter/Trabalho-BD-/files/9964059/sqls.zip)



## 9.0 Tabelas e principais consultas

### 9.1 Consultas das tabelas com todos os dados inseridos
![1](https://user-images.githubusercontent.com/106558466/200667112-290ce432-0702-4894-8483-1e26cc7e166b.PNG)
![2](https://user-images.githubusercontent.com/106558466/200667115-55fd9a52-eb85-43ee-bd6a-d42421df796f.PNG)
![3](https://user-images.githubusercontent.com/106558466/200667116-d67d1eee-c083-4414-a92c-fb93b16fb2d3.PNG)
![4](https://user-images.githubusercontent.com/106558466/200667117-69e4bda2-8e08-4d01-881a-2e19bd40d013.PNG)
![5](https://user-images.githubusercontent.com/106558466/200667120-578d99c2-6147-411c-ae5a-7fb32c162ffb.PNG)
![6](https://user-images.githubusercontent.com/106558466/200667121-8933e825-c208-41da-936b-606f076902bf.PNG)
![7](https://user-images.githubusercontent.com/106558466/200667123-5d5c3267-afec-4ea9-a7b4-0fe0178f7402.PNG)
![8](https://user-images.githubusercontent.com/106558466/200667127-42d6f78c-cdf1-48f8-b23d-6939ab992945.PNG)
![9](https://user-images.githubusercontent.com/106558466/200667129-d4240006-0828-46b7-8d43-d72ea4e94ba4.PNG)
![10](https://user-images.githubusercontent.com/106558466/200667132-599b21bb-4acc-4c44-bf08-e783ea763690.PNG)
![11](https://user-images.githubusercontent.com/106558466/200667134-b01b04db-5a7a-4c51-87a2-7860d910f644.PNG)

### 9.2 consultas das tabelas com filtros whare
![image](https://user-images.githubusercontent.com/106558466/201400074-3a17012e-9306-4e97-9baf-5aa1e4068fa6.png)
![image](https://user-images.githubusercontent.com/106558466/201400757-d2c973eb-8421-4aa9-b826-e204521c226f.png)
![image](https://user-images.githubusercontent.com/106558466/201401233-ed7f2cac-7ae0-4311-90e2-d005db071bd3.png)
![image](https://user-images.githubusercontent.com/106558466/201401936-a01800d1-235a-45de-8d35-77690ee5d38f.png)

### 9.3 Consultas usando operadores lógicos, aritiméticos e tabelas ou campus renomeados

![image](https://user-images.githubusercontent.com/106558466/201424300-f55b2e12-e358-4a15-91ab-207dde80fd1d.png)
![image](https://user-images.githubusercontent.com/106558466/201424736-f159cfc4-06e8-4112-a32c-6c501e25dec8.png)
![image](https://user-images.githubusercontent.com/106558466/201425013-34aedce3-f5c6-42a8-9d90-df909f3cb6e7.png)
![image](https://user-images.githubusercontent.com/106558466/201425500-5f867d63-0cae-4baa-be2a-871efce78db8.png)
![image](https://user-images.githubusercontent.com/106558466/201427979-402fa8ea-4961-4ecd-ad1c-24d1aac25a31.png)
![image](https://user-images.githubusercontent.com/106558466/201432217-869a3ecd-6166-4989-a646-2cdfa9dc8402.png)
![image](https://user-images.githubusercontent.com/106558466/201434284-a8e1a7cd-ab08-435c-ba38-cab669057946.png)
![image](https://user-images.githubusercontent.com/106558466/201434537-a88aab44-7d0b-4ad5-b918-d08500ce008d.png)
![image](https://user-images.githubusercontent.com/106558466/201435030-9043345e-bbb8-410a-9018-1f5e72b2b82e.png)
![image](https://user-images.githubusercontent.com/106558466/201441289-b85571da-5aa4-48b2-b56e-d718df2b0549.png)
![image](https://user-images.githubusercontent.com/106558466/201441453-7f38ae62-7140-4584-b982-ed540e8d0560.png)
![image](https://user-images.githubusercontent.com/106558466/201441742-d43bd0f6-3251-4244-b172-5d5a540b4e40.png)


### 9.4 Consultas que usam operadores like e datas
![image](https://user-images.githubusercontent.com/106558466/201442211-cc690dbb-6f09-45d3-bf6e-da114303e27c.png)
![image](https://user-images.githubusercontent.com/106558466/201442360-0f06bae8-bd3d-4cc7-9e6d-a389a30f11f2.png)
![image](https://user-images.githubusercontent.com/106558466/201442473-32ff0104-a67e-4c9e-a2a9-8e46bb3d85b1.png)
![image](https://user-images.githubusercontent.com/106558466/201442614-82e0f0dc-b880-4a03-aeda-c66dc95b887b.png)
![image](https://user-images.githubusercontent.com/106558466/201442728-f85b6ccc-ac78-4285-8f62-b6d16d839c5e.png)
![image](https://user-images.githubusercontent.com/106558466/201442895-8a5c2dec-9d54-455d-a67e-331e56b53e23.png)
![image](https://user-images.githubusercontent.com/106558466/201443143-5d955902-6c97-4d92-97b9-ff512b197012.png)
![image](https://user-images.githubusercontent.com/106558466/201443541-2305d1c7-ebf6-4036-8630-fe098ebea9e2.png)
![image](https://user-images.githubusercontent.com/106558466/201443883-9469054d-c8bf-4fd5-9c85-c46ba23145ca.png)
![image](https://user-images.githubusercontent.com/106558466/201444073-3db384dc-7f93-4e18-8bfd-551eb0f62198.png)
![image](https://user-images.githubusercontent.com/106558466/201444437-4dea1f66-8986-4460-95d5-8212f0fdf35f.png)





