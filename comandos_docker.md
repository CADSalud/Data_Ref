
#### lista bases de datos 

docker exec -i "some-postgres" psql  -U postgres -l 

o tambien:  docker run -it --rm --link some-postgres:postgres postgres psql -l -h postgres -U postgres

#### carga base de datos

##### a) primero crea la base de datos que recibirá la informacion

docker exec -i "some-postgres" createdb -U postgres censo2010 

o tambien:  docker run -it --rm --link some-postgres:postgres postgres createdb ent_urb2010 -h postgres -U postgres

##### b) carga los datos

docker exec -i "some-postgres" pg_restore -C -U postgres -O -d censo2010 < censo2010.backup

#### abrir la terminal psql 

docker run -it --rm --link some-postgres:postgres postgres psql -d censo2010 -h postgres -U postgres  

#### muestra los repositorios activos

docker ps -a

####  inicia el servicio

docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres

o es este???  docker run -it --rm --link some-postgres:postgres postgres psql -h postgres -U postgres   

#### termina la maquina. la apaga en forma ordenada 

docker rm -f some-postgres

#### taerse el docker postgresql 

docker pull postgres

#### conocer la IP asociada a un repo docker activo

docker inspect <container id>

docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)

###### el conteiner id se obtiene con docker ps -a

#### para conectar a R es igual que cualquier coneccion nada mas se agrela la IP

#### conviene instalar el docker.img  en mac ya que contiene una pestaña donde se puede direccionar todo el docker a un disco externo

####


