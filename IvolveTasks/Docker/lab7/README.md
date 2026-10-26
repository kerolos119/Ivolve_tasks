#lab7
#steps

1- mkdir lab7
2- cd lab7/
3- git clone https://github.com/Ibrahim-Adel15/MicroserviceApp.git
4- cd MicroserviceApp/
5- docker build -t frontend ./frontend
6- docker build -t backend ./backend/
7- docker build -t notification ./notification/
8- docker images
9- docker network create --driver bridge --subnet 172.20.0.0/24 frontend-backend
10- docker network create --driver bridge --subnet 172.21.0.0/24 backend-notification
11- docker volume create backend-logs
12- docker volume create notification-logs
13- mkdir -p ~/backend-data
14- docker run -d --name notification --network backend-notification -v notification-logs:/app/logs notification
15- docker run -d   --name backend   --network backend-notification   -e NOTIFICATION_URL=http://notification:5001/notify   -v backend-logs:/app/logs   -v ~/backend-data:/app/data   backend
16- docker network connect frontend-backend backend 
17- docker run -d --name frontend --network frontend-backend -p 8080:3000 -e BACKEND_URL=http://backend:5000 frontend
18- in any browser open ("http://localhost:8080")
19- cat ~/backend-data/messages.json
20- docker exec notification cat /app/logs/notification.log
21- docker exec backend cat /app/logs/backend.log
22- docker volume inspect backend-logs
23- docker exec frontend python -c "import requests; requests.get('http://notification:5001/health', timeout=3)"

