#the base image 
FROM python:2.7-stretch

#maintainer info
MAINTAINER oualid_ilyass

#copying api source code file to the container root path
COPY student_age.py  /
#COPY student_age.json /data

#running prerequisites
RUN apt-get update -y && apt-get install python-dev python3-dev libsasl2-dev python-dev libldap2-dev libssl-dev -y
RUN pip install flask flask_httpauth flask_simpleldap python-dotenv

#creating a file to be mounted
WORKDIR /data

#mouting the created file
VOLUME /data

#opening port 5000
EXPOSE 5000

#running the api when starting the container
CMD [ "python", "./student_age.py" ]
