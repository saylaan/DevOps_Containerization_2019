FROM python:3.7.1

WORKDIR /usr/src/app

COPY * ./

RUN pip install -r requirements.txt

COPY . /usr/src/app

EXPOSE 80

CMD flask run --host=0.0.0.0 --port=80

#BUILD
#docker build -t <your username>/docker_flask_app .
#RUN IMAGE
#docker run -p 49160:8080 -d <your username>/docker_flask_app
#Go into shell
#docker exec -it <container id> /bin/bash