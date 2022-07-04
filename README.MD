# POSTGRES LOCALIZAÇÃO PT_BR
</h1>

## Descrição do Projeto

Banco de dados Postgres versão 12.8 em container mais configuração de localização pt_BR e formato UTF-8 pt_BR.UTF-8.

<h1>

## Como Usar

Comando para criar o container com docker manifesto. Deve ser criado a .env de acordo com a necessidade. Utilize da .env-example como referencia para variaves necessarias. 

```
docker-compose -f postgres.yml --env-file=.env up -d
```
Obs: Caso tenha um script de inicialização ou back do banco adicione dentro da pasta abaixo.
```
db/init/seus_scripts
```
Comando para remover o container
```
docker-compose -f postgres.yml --env-file=.env down
```
Comando para remover o container junto com volumes de dados:
```
docker-compose -f postgres.yml --env-file=.env -v down
```
<h1>

## Comandos Extras
Obs: Os dados do banco de dados permanece local na pasta data. Para limpar completamente basta remover a pasta data.
```
 rm -R -f db\data\
```
Comando para verificar o logs do container.
```
docker logs container_name
```
Comando para fazer backup via terminal ssh do container
```
pg_dump -U usuario_db -h localhost banco_de_dados >> backup.sql
```
Comando para restaurar banco de dados. Obs: Vai enviar para pasta data.
```
psql -U usuario_db -d banco_de_dados -f /docker-entrypoint-initdb.d/dump-medbrasil.sql
```
Comando para acessar o container via bash.
```
docker exec -it container_name /bin/bash
```
Comando postgres restore
```
pg_restore -U usuario_db -f /docker-entrypoint-initdb.d/backup.sql
```