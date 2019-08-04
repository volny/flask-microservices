# following this presentation: <https://mherman.org/presentations/microservices-flask-docker/#23>

consisting of 4 "microservices"

* Main <https://github.com/testdrivenio/flask-microservices-main>
* Users <https://github.com/testdrivenio/flask-microservices-users>
* Client <https://github.com/testdrivenio/flask-microservices-client>
* Swagger <https://github.com/testdrivenio/flask-microservices-swagger>
* Eval <https://github.com/testdrivenio/flask-microservices-eval>


## Steps

### users db

* install users db: `docker-compose up -d --build users-db`  
  (or just install all services at once with `docker-compose up -d --build`)
* check if it worked `docker exec -ti users-db psql -U postgres -W`

### users app

* `docker-compose up -d --build users-service`
* start, seed, test

```sh
# create and seed the db
docker-compose run users-service python manage.py recreate_db
docker-compose run users-service python manage.py seed_db

# run unit and integration tests
docker-compose run users-service python manage.py test
```

### client

* build

```sh
# add env variable
export REACT_APP_USERS_SERVICE_URL=localhost

# build and run:
docker-compose up -d --build web-service
```

* test it works by visiting `http://localhost:9000`

### swagger

* `docker-compose up -d --build swagger`
* check the auto-generated docs at `http://localhost:8080/`


