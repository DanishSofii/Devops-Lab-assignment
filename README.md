1 create a html file
2 create a Dockerfile :
		FROM httpd:latest
		COPY index.html /usr/local/apache2/htdocs/
3 run command :
		docker build -t demobook:v .
4 run command :
		docker run -d --name demoapp -p 8080:80 demobook:v1
5 To push on docker hub:
	1: docker login -u <your dockerhub login>
	2: run command : docker images and copy the image id
	3: run command docker tag <image ID> <dockerhub login>/demobook:v1
	4: run : docker push docker.io/<dockerhublogin>/demobook:v1
-----------------------------------------------------------------------------------------------------------------------
Open docker app on your pc , goto settings, enable kubernetes then write the following commands:
  1. kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
  2. kubectl get pods -n kubernetes-dashboard
  3. kubectl get services -n kubernetes-dashboard

------------------------------------------------------------------------------------------------------------------------
6: create a file named : deployment.yaml 
7: create a file named : service.yaml
8: run following commands:
		kubectl apply -f deployment.yaml
		kubectl apply -f service.yaml
9: create file dashboard-adminuser.yaml
10 : apply command kubectl apply -f dashboard-adminuser.yaml
11 : create file admin-user-clusterrolebinding.yaml
12 : command : kubectl apply -f admin-user-clusterrolebinding.yaml
13 : create file : admin-user-secret.yaml
14 : run command : kubectl apply -f admin-user-secret.yaml
15 : run command : kubectl -n kubernetes-dashboard get secret
16 : run command : kubectl -n kubernetes-dashboard describe secret admin-user-token
-------------------
copy the token generated from above command
-------------------
17 : run command : kubectl proxy
18 : open the link in browser : http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
19: give the token in dashboard and login
