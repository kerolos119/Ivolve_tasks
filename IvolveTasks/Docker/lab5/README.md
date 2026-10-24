#lab5 
#steps

1- cd lab4/
2- git clone https://github.com/Ibrahim-Adel15/TrivyImage.git
3- cd TrivyImage/
3-  docker build -t image3 .
4- trivy image image3
5- trivy image --severity HIGH,CRITICAL image3
6- wget https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/html.tpl
7- trivy image   --format template   --template "@html.tpl"   --severity HIGH,CRITICAL   -o report-v1.html   image3
8- vim Dockerfile  ( change to 22-alpine) 
9- npm install express@^4 --package-lock-only
10- docker build -t image3:v2 .
11- trivy image --severity HIGH,CRITICAL image3:v2
12- trivy image   --format template   --template "@html.tpl"   --severity HIGH,CRITICAL   -o report-v2.html   image3:v2
13- trivy image --severity HIGH,CRITICAL --ignore-unifixed --exit-code 1 ivolve-app:v2 echo$?

