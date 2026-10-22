# Lab3 part 1
# steps
1- mkdir Docker 
2- cd Docker
3- mkdir Lab3p1
4- cd Lab3p1
5- git clone https://github.com/Ibrahim-Adel15/CalculatorMavenApp.git
6- cd CalculatorMavenApp
7- vim Dockerfile 
in Dockerfile
FROM maven:3.10.0-eclipse-temurin-17-alpine

WORKDIR /app

COPY . .

RUN adduser -D -h /home/appuser appuser 

RUN mvn package

USER appuser

CMD ["java", "-jar", "target/calculator.jar"]

8- docker build -t lab3 .
9- docker run -d --name container1 -p 8085:8080 lab3
10- docker image 
the docker size about 203MB

