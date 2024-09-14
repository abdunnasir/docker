# Run a laravl project

We have two services in the docker-compose file
php-apache and mysql.


php-apache build an image using the Dockerfile. The Dockerfile
uses the image php:8.2-apache and then instal all the dependencies 
required for the laravel app.

nd then we create an image using the Docker file, as we have the below 
entry in the docker-compose

`
build:
      context: .
      dockerfile: Dockerfile
`


and the next service is mysql, which pull an image mysql:5.7,
and set up mysql with root passwod specified as enviourment variables.


Also we have a volume 

`
mysql_data_st:/var/lib/mysql
`

To save the database data.