##Docker

### Delete all the images unused
docker system prune -a

### Run mongodb
docker run -it -p 27017:27017 --name mongodb -d mongo

### Connect to the container
* docker exec -it mongodb bash
  * mongo -host localhost -port 27017

### install in pop-os
https://linuxhint.com/install-docker-on-pop_os/
