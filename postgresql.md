INSTALANDO O POSTGRESQL NO FEDORA    
===========

<strong>Se torne root</strong>
<strong>Para instalar digite no terminal:
- sudo yum install postgresql-server

<strong>Uma vez instalado, vamos trocar a senha do usuário postgres</strong>
- sudo passwd postgres
- digite a nova senha: ‘minhasenha’

<strong>Feito isso, inicie a sua base de dados</strong>
- service postgresql initdb 

===========
Pulo do Gato \_(^⁻^)_/

<strong>Agora você já configurou a senha do super usuário (postgres) do Banco, mas ainda é necessário editar o arquivo de configuração do postgres para que possamos nos conectar</strong>
- sudo nano /var/lib/pgsql/data/postgresql.conf
<strong>No arquivo de configuração, procure a linha que contém as seguintes linhas abaixo, se estiverem comentadas com um "#" descomente:</strong>
- listen_adress = ‘localhost’
- port = 5432

<strong>Se você não fizer o próximo passo, não conseguirá se conectar com o banco. 
Agora que alteramos as configurações para que possamos nos conectar localmente, vamos alterar as configurações para autenticação no arquivo ‘pg_hba.conf’</strong>
<strong>Navegue até o arquivo: </strong>
sudo nano /var/lib/pgsql/data/pg_hba.conf
<strong>localize a linha: </strong>
- host all all 127.0.0.1 ident
<strong>substitua por: </strong>
- host all all 127.0.0.1 md5

<strong>Inicie o serviço:</strong>
- service postgresql start 

===========
<strong>Entre no postgres</strong>
- su -l postgres

<strong>Crie um banco de dados</strong>
- createdb proesc

<strong>Entre no banco de dados</strong>
- psql proesc

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
