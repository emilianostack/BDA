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


create user Bob
identified by ALONG
default tablespace DATA01
temporary tablespace temp
quota 100M on DATA01
quota 100M on INDX01;

create user Kay
identified by MARY
default tablespace DATA01
temporary tablespace temp
quota 100M on DATA01
quota 100M on INDX01;

REVOKE CREATE TABLE FROM Kay;

select tablespace_name from dba_users;


SELECT username FROM dba_users WHERE username = 'Bob' or username = 'Kay';

SELECT username FROM dba_ts_qutoas WHERE username = 'Bob';

ALTER USER Bob
QUOTA 0 ON DATA01;

DROP USER Kay CASCADE;

ALTER USER Bob
IDENTIFIED BY SAM;


ALTER USER Bob
IDENTIFIED BY OLINK
PASSWORD EXPIRE;



SYSOPER PRIVILEGES WITH ADMIN OPTION
CREATE DATABASE
ALTER TABLESPACE BEGIN/END BACKUP
RESTRICTED SESSION
RECOVER DATABASE UNTIL

STARTUP
SHUTDOWN
ALTER DATABASE OPEN | MOUNT
ALTER DATABASE BACKUP CONTROLFILE TO
RECOVER DATABASE
ALTER DATABASE ARCHIVELOG
RESTRICTED SESSION

REVOKE CREATE TABLE FROM emi;



audit table; 	// para tabela
audit create any trigger;	 //por privilegio
audit select on emi.orders;		//objeto


parametro aduit_trail

none= auditoria desativada
DB = auditoria ativa e direciona todos os registros para a trilha do bd
SO = auditoria ativa e direciona os registro para um log do SO


alter system set audit_trail = "DB" scope = spfile;	// ativa a auditoria


alter system set audit_trail = "DB" scope = spfile;	// ativa a auditoria

audit select on scott.emp by access whenerver successful;  toda vez q alguem fizer select gera log


select username, to_char(timestamp, 'DD/MM/YYYY HH21:MI:SS') timestamp, 
obj_name, action_name
from dba_audit_trail
where obj_name = 'EMP';



audit statment [, statment] ..
on { [schema] object|default}
[by {session|access}]
[whenever [not] successful]

onde:
 statement: instrução sql
 schema_object: objeto escolhido
 default: define opções do objeto especifico como default para objetos posteriores
 by session: um registro onserido a cada sessão
 access: um registro toda vez que a instrução é executada
 whanever: auditoria deve ser executada somente na instrução ou onde com sucesso
 
 
 noaudit select on scott.emp;
 
 

1-Execute auditoria na tabela dept para insert de registro
Dica: Ative a auditoria e exercute o comado de inserção
R: audit insert on scott.dept whenever successful;


2-Execute auditoria na tabela emp para delete faça atualização e veja as auditorias
R: audit delete on scott.dept whenever successful;


3-Execute auditoria na tabela sal para inserção, update e delete
R: audit update,delete,insert on scott.salgrade whenever successful;




connect system/manager as sysdba

shutdown 

rman target /dados/oracle
rman target /

startup

run {
allocate channet t1 type disk format '/home/oracle/BKP_CF_28102015.rman';
backup current controlfile tag BKP_CF;
release channet t1;
}

cd $ORACLE_DATA

mv control.dbf control.db2

rman target /

startup nomount;

restore controlfile from '/home/oracle/BKP_CF_28102015.rman';



//////////////////////////////////////////////////////////////////////////////////////////

explain plan for
select * from scott.emp
where job like 'M%'

select * from table(DBMS_XPLAN.DISPLAY);
