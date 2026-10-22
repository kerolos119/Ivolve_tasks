# Lab3 part 2
# steps
 
1- cd Docker
2- mkdir Lab3p2
3- cd Lab3p2
4- git clone https://github.com/Ibrahim-Adel15/CalculatorMavenApp.git
6- cd CalculatorMavenApp
5- mvn package
7- vim Dockerfile 
8- nano Dockerfile 
FROM amazoncorretto:17-alpine3.21-full

WORKDIR /app

COPY target/calculator.jar .

RUN adduser -D -h /home/appuser2 appuser2

USER appuser2

CMD ["java", "-jar", "calculator.jar"]

8- docker build -t lab3p2 .
9- docker run -d --name cont1 -p 8085:8080 lab3p2
10- docker image 
the docker size about 153MB
