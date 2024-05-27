#create a html file
#create a Dockerfile :
		``FROM httpd:latest
		COPY index.html /usr/local/apache2/htdocs/``
run command
		``docker build -t demobook:v .``
run command :
		``docker run -d --name demoapp -p 8080:80 demobook:v1``
#To push on docker hub:
    ``docker login -u <your dockerhub login>``
    ``run command : docker images and copy the image id``
   `` run command docker tag <image ID> <dockerhub login>/demobook:v1``
    ``run : docker push docker.io/<dockerhublogin>/demobook:v1``
-----------------------------------------------------------------------------------------------------------------------
#Open docker app on your pc , goto settings, enable kubernetes then write the following commands:
  1. ``kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml``
  2. ``kubectl get pods -n kubernetes-dashboard``
  3. ``kubectl get services -n kubernetes-dashboard``

------------------------------------------------------------------------------------------------------------------------
#Push to Kubernetes
create a file named : deployment.yaml 
create a file named : service.yaml
run following commands:
		``kubectl apply -f deployment.yaml``
		``kubectl apply -f service.yaml``
create file dashboard-adminuser.yaml
apply command 
	``kubectl apply -f dashboard-adminuser.yaml``
create file admin-user-clusterrolebinding.yaml
command : 
	``kubectl apply -f admin-user-clusterrolebinding.yaml``
create file : admin-user-secret.yaml
run command : 
	``kubectl apply -f admin-user-secret.yaml``
run command : 
	``kubectl -n kubernetes-dashboard get secret``
run command : 
	``kubectl -n kubernetes-dashboard describe secret admin-user-token``
-------------------
copy the token generated from above command
-------------------
run command : 
	``kubectl proxy``
open the link in browser : 
	http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
give the token in dashboard and login

