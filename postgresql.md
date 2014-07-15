INSTALANDO O POSTGRESQL NO FEDORA    
===========

<strong>Se torne root</strong>
<strong>Para instalar digite no terminal:
- yum install postgresql-server

<strong>Inicialize o cluster initdb:</strong>
- service postgresql initdb 

<strong>Inicie o serviço:</strong>

- service postgresql start 

===========
Pulo do Gato \_(^⁻^)_/

<strong>Entre no postgres</strong>
- su -l postgres

<strong>Crie um usuário</strong>
- createuser --no-superuser --no-createdb --no-createrole --pwprompt "seu-nome-de-usuário-sem-aspas-duplas" 

<strong>Criando um banco de dados</strong>
- createdb --owner "seu-usuário-criado" "seu-banco-de-dados" 

<strong>Alterando conexões</strong>
- nano /var/lib/pgsql/data/pg_hba.conf

- Exemplo:
# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD  
local   jbpm3       jbpm3                             md5  
host    jbpm3       jbpm3       127.0.0.1/32          md5  
host    jbpm3       jbpm3       127.0.0.1/32          md5  

<strong>Reiniciando o serviço</strong>
- service postgresql reload

<strong>Criando Tabelas</strong>
- psql --username jbpm3 --file jbpm.jpdl.postgresql.sql


```					  					  
   INSTALANDO O PGADMIN    
```

-yum install pgadmin3

<strong>Instrumento de instalação de servidor</strong>
- yum install postgresql-contrib

<strong>Em seguida, execute o script adminpack.sql</strong>
- su -l postgres$ psql --file /usr/share/pgsql/contrib/adminpack.sql

<strong>Agendar tarefas de manutenção 
Coloque o seguinte script em / etc / cron.daily / pgsqlmntn</strong>
- !/bin/sh  
su -c 'vacuumdb --all --full --analyze' postgres  
su -c 'reindexdb --all' postgres

<strong>Instalar executáveis</strong>
- chmod a+x pgsqlmntn

<strong>Reiniciando o serviço do postgres</strong>
- service postgresql reload