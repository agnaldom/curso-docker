## Criando Volume

docker volume create --driver local --opt type=overlay2 --opt device=overlay2 --opt o=size=300m,uid=100 site

## Levantando docker compose
docker-compose up 

## listando 
docker-compose ls 

## inspeciando
docker-compose inspect

## Lendo Logs
docker-compose logs

## Demostraçao de como scala containes
https://github.com/vegasbrianc/docker-compose-demo.git

Criando Variaveis de ambiente com .env
DB_CONNECTION=mysql
DB_HOST=database
DB_PORT=3306
DB_DATABASE=cursodocker
DB_USERNAME=root
DB_PASSWORD=a_good_strong_password
MYSQL_ROOT_PASSWORD=a_good_strong_password

