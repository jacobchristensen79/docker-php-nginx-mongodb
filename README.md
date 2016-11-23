# Docker development environment
* Nginx 1.10, out of the box
* PHP FPM 5.6, with some additional needed packages
* MongoDB 3.2, out of the box


## Config it:
* By default a simple php "app_dev.php" script will be run from pubklic folder 
* Change the 2 VOLUMENES paths  where ./public to the /full-path of your installation, phpfpm and nginx.
* As this is a Symfony 2 intended installation, point it to your root, folder "web" is mapped in vhost of nginx

## Start it:
docker-compose up -d --build

## Build information:
* List running instances: `docker ps`
* Login to machine: `docker exec -ti phpfpm_machine_name bash`
* if you have a bash code you can run it `sh dev-cleanstart.sh`
* Git client and composer is installed. If you use private git you do still need to configure.

## Database
* From host to docker db: `localhost:27018`
* From php: mongodb.default.server.uri: 'mongodb://mongodb:27017'
* No username nor password, can be configured.

## X-Debug
* I followed instructions given here for php-storm: hope it helps
* https://blog.jetbrains.com/phpstorm/2015/10/docker-support-in-phpstorm/

## Performance
* docker-machine stop
* VBoxManage modifyvm default --cpus 4
* VBoxManage modifyvm default --memory 6144
* docker-machine start