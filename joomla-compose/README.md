## Criando Volume

docker volume create --driver local --opt type=overlay2 --opt device=overlay2 --opt o=size=300m,uid=100 site

## Levantando docker compose
docker-compose up 

## listando 
docker-compose ls 


