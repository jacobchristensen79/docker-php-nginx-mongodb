
## config it:
set VOLUMENES(2) where public to the PATH of your installation, phpfpm and nginx.

## start it:
docker-compose up -d --build


## build data:
* bash-3.2$ docker exec -ti lemp_phpfpm_1 bash
* sh dev-cleanstart.sh 
* As there is no git there will be thrown an error.

## Database
connect from your pc to: `localhost:27018`