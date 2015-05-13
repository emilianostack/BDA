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
