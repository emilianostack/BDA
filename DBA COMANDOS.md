desc dba_users  	// Mostra informações 
clear 			// Limpa memoria
clear screen 		// limpa a tela
spqplus 		// para entrar no modo sql
login: system senha: manager
connect sys as sysdba 	// entrar no modo sys
shutdown 		// desliga o banco, funciona somente no modo sys. Tem que esperar todos os processos para desligar
startup 		// liga o banco, funciona somente no modo sys
top 			// mostra os processos que estão rodando
01090 - shutdown in progress - Connection in not permitted
Instância		// Memoria !!! Buffers !!! Usuarios!!!

Processos START:
Estagio <NOMOUNT>	// Serve para a movimentação dos arquivos
Estagio <MOUNT>		// Monta o dba, mas não permite conexão com o usuario
Estagio <OPEN>		// Permite conexão com os usuarios
Estagio <PFILE>		// Permite que o arquivo de paramentros alternativo seje usuario para configurar a instacia

desc XXX		// describre (descrição da tabela qualquer) 
show user		// Mostra o usuario logado

Tipos de Startup:
FORCE			// Força a inicialização
RESTRICT		// Somente usuarios com permissão RESTRICT SESSION
RECOVER			// 

ALTER DATABASE	estagio;// Altera o estagio do start

senha do root da VM: root123

desc dba_users  	// Mostra informações 
clear 			// Limpa memoria
clear screen 		// limpa a tela
spqplus 		// para entrar no modo sql
login: system senha: manager
connect sys as sysdba 	// entrar no modo sys
shutdown 		// desliga o banco, funciona somente no modo sys. Tem que esperar todos os processos para desligar
startup 		// liga o banco, funciona somente no modo sys
top 			// mostra os processos que estão rodando
01090 - shutdown in progress - Connection in not permitted
Instância		// Memoria !!! Buffers !!! Usuarios!!!

Processos START:
Estagio <NOMOUNT>	// Serve para a movimentação dos arquivos
Estagio <MOUNT>		// Monta o dba, mas não permite conexão com o usuario
Estagio <OPEN>		// Permite conexão com os usuarios
Estagio <PFILE>		// Permite que o arquivo de paramentros alternativo seje usuario para configurar a instacia

desc XXX		// describre (descrição da tabela qualquer) 
show user		// Mostra o usuario logado

Tipos de Startup:
FORCE			// Força a inicialização
RESTRICT		// Somente usuarios com permissão RESTRICT SESSION
RECOVER			// 

ALTER DATABASE	estagio;// Altera o estagio do start

senha do root da VM: root123

@ /home/oracle/Desktop/scott.sql	// Carrega script SQL

alter database open read only;	// Libera somente para leitura

login scott senha tiger

////////////////////////////////////////////////////////////////////////////////////////////////////////////


CREATE DATABASE			// CRIAR DATABASE

VARIAVEIS DE AMBIENTE PARA CONFIGURAR:
ORACLE_BASE
ORACLE_HOME
ORACLE_SID
ORA_NLS33
PATH
LD_LIBRARY_PATH


ARCHIVELOG		// Faz auditoria dos dados, faz log das alterações
DICIONARIO CATALOG.SQL 	// uTILIZADO PELO PROPRIO BANCO
PLSQL			// EXLCUSIVO ORACLE

3 VISÕES DO DICIONARIO DE DADOS:
DBA_XXX			// TODOS OS OBJETOS DO BANCO DE DADOS
ALL_xXX			// OBJETOS ACESSIVEIS PELO USUARIO ATUAL
USER_XXX		// OBJETOS DE PROPRIEDADE DO USUARIO ATUAL

////////////////////////////////////////////////////////////////////////////////
create user aaron
identified by soccer
default tablespace data
temporary tablespace temp
quota 15M on data
quota 10M ON users
password expire;


select tablespace_name from dba_tablespaces;


alter user aaron
quota 1M on data01;

drop user aaron; mata o usuario

drop user aaron cascade; mata o usuario e as tabelas

