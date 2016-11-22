
## Config it:
set VOLUMENES(2) where public to the PATH of your installation, phpfpm and nginx.

## Start it:
docker-compose up -d --build


## Build information:
* user$ docker exec -ti lemp_phpfpm_1 bash
* if you have a bash code you can run it `sh dev-cleanstart.sh`
* Git client and composer is installed

## Database
connect from your pc to: `localhost:27018`
from "code" mongodb.default.server.uri: 'mongodb://mongodb:27017'
