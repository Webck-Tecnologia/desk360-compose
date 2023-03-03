# Desk360

Desk360 é uma aplicação web para gerenciamento de tickets e suporte ao cliente. Esse arquivo docker-compose contém a configuração para rodar a aplicação e para realizar backups e restores do banco de dados PostgreSQL.

## Pré-requisitos

Antes de iniciar, você precisará ter o Docker e o Docker Compose instalados na sua máquina. Consulte a documentação oficial do Docker para instruções de instalação.

## Iniciando a aplicação

Para iniciar a aplicação, execute o seguinte comando na pasta onde está localizado o arquivo docker-compose.yml: docker-compose up -d

Isso irá baixar as imagens necessárias, criar os containers e iniciar a aplicação na porta 80. Certifique-se de que as portas 80, 5432 e 9200 não estão sendo usadas por outras aplicações na sua máquina.

## Realizando backups

O backup do banco de dados é realizado automaticamente pelo container `backup`. O backup é salvo em um arquivo `zammad_production.dump` na pasta `./backup` na sua máquina host. Certifique-se de que a pasta `./backup` exista e tenha permissão de escrita antes de iniciar o backup.

Para iniciar o backup manualmente, execute o seguinte comando: docker-compose run --rm backup

Isso irá executar o comando `pg_dump` para criar um arquivo de backup em formato `.dump`.

## Restaurando backups

Para restaurar um backup, coloque o arquivo `.dump` na pasta `./backup` na sua máquina host e execute o seguinte comando: docker-compose run --rm restore

Isso irá executar o comando `pg_restore` para restaurar o backup.

## Customização

Você pode customizar a aplicação alterando as variáveis de ambiente no arquivo docker-compose.yml. Consulte a documentação oficial da aplicação para saber quais variáveis podem ser alteradas.

Além disso, você pode alterar a configuração de backup e restore no arquivo docker-compose.yml. Por exemplo, você pode alterar a pasta onde o backup é salvo e a pasta de destino do restore. Certifique-se de que as pastas existam e tenham as permissões necessárias.

## Parando a aplicação

Para parar a aplicação, execute o seguinte comando na pasta onde está localizado o arquivo docker-compose.yml: docker-compose down

Isso irá parar e remover os containers criados pelo comando `docker-compose up`.





