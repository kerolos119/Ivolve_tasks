#lab6
#steps
in Docker folder:
1- mkdir lab6
2- cd lab6
3- git clone https://github.com/Ibrahim-Adel15/PythonApp.git
4- cd PythonApp/
5- vim Dockerfile
6- docker build -t image5 .
7- docker run -d -p 5002:5000 --name cont2 -e APP_NAME=ivolveApp1 -e APP_ENV=stg --cpus="1.0" --memory="256m" image5
8- curl localhost:5002
9- vim env.txt
10- docker run -d -p 5003:5000 --name cont3 --memory="256m" image5
11- curl localhost:5003
12- docker rm cont3
13- docker run -d   -p 5003:5000   --name cont3   --memory="256m"   --env-file env.txt   image5
14- curl localhost:5003


## Screenshot

![Python App](screenshot/image-python.png)
