FROM ubuntu
WORKDIR /app
COPY requirements.txt /app/
COPY devops /app/
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install python3 && apt-get install pip
RUN pip install -r requirements.txt
RUN cd devops

ENTRYPOINT [ "python3" ]
CMD [ "manage.py", "runserver", "0.0.0.0:8080" ]