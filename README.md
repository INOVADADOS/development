Development of a kit InovaDados
===========
Autor: Desenvolvimento do InovaDados
Atualizado em: 28 de Junho de 2014 
Função:Kit de desenvolvimento
===========
____________________________________________
||					  					  ||
||   INSTALANDO O POSTGRESQL NO FEDORA    ||
||								          ||

<strong>Para instalar digite no terminal:</strong>
yum install postgresql postgresql-server -y

<strong>Inicialize o cluster initdb:</strong>
postgresql-setup initdb

<strong>Coloque na inicialização e inicie o PostgreSQL:</strong>

systemctl start postgresql.service 
systemctl enable postgresql.service
<strong>PRONTO! INSTALADO COM SUCESSO</strong>
=========================================== 
