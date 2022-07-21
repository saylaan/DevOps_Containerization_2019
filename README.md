# DevOps_Containerization_2019

Simple poll web application.
Poll is a Python Flask web application that gathers the votes to push them into a Redis queue.
The JavaWorker consumes the votes stored in the Redis queue, then pushes it into a PostgreSQL database.
Finally, the Node.js Result web application fetches the votes from the DB and displays the result.

5 services:

1. poll:
    - build your poll image and redirect port 5000 of the host to the port 80 of the image.
2. redis:
    - use an existing image of redis and open port 6379
3. worker:
    - build your worker image.
4. db:
    - representing the database that will be used by the apps. You must use an existing image of
postgres. Database schema must be created during container first start.
5. result:
    - build your result image and redirect port 5001 of the host to the port 80 of the image.

3 networks:

- poll-tier to allow poll to communicate with redis
- result-tier to allow result to communicate with db
- back-tier to allow worker to communicate with redis and db

1 volume:

- db-data will make the database data persistent, if the container dies.

![alt text](https://github.com/saylaan/DevOps_Containerization_2019/blob/master/T-DOP-600_docker.jpg?raw=true)