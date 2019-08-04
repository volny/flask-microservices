# following this presentation: <https://mherman.org/presentations/microservices-flask-docker/#23>

consisting of 4 "microservices"

* Main <https://github.com/testdrivenio/flask-microservices-main>
* Users <https://github.com/testdrivenio/flask-microservices-users>
* Client <https://github.com/testdrivenio/flask-microservices-client>
* Swagger <https://github.com/testdrivenio/flask-microservices-swagger>
* Eval <https://github.com/testdrivenio/flask-microservices-eval>


## Steps

* install users db: `docker-compose up -d --build users-db`
* check if it worked `docker exec -ti users-db psql -U postgres -W`
