###### basic example using mongo-express

### create namespace

kubectl create namespace mongo-express

### apply kubernetes config files

kubectl apply -f ./basic-example/mongo-secret.yaml
kubectl apply -f ./basic-example/mongo-configmap.yaml
kubectl apply -f ./basic-example/mongo-express.yaml
kubectl apply -f ./basic-example/mongo.yaml

### service from minikube

minikube service list
minikube service -n mongo-express

### usefull commands

kubectl get pod -n mongo-express
kubectl get all -n mongo-express
kubectl describe service mongodb-service -n mongo-express

### test usinf default login

username: admin
password: pass

### clean

kubectl delete deployment mongo-express -n mongo-express
kubectl delete deployment mongodb-deployment -n mongo-express
kubectl delete service/mongodb-service -n mongo-express
kubectl delete service/mongo-express-service -n mongo-express

######

######

###### For ingest using minikube Dashboard

### enable ingress in minikube

minikube addons enable ingress

### start dashboard image

minikube dashboard

### setup fake host to test

### config file

sudo vim /etc/hosts

### add line to file <- dont forget to remove later

127.0.0.1 dashboard.com

### apply ingress

kubectl apply -f ./ingress/dashboard-ingress.yaml

### start tunnel

minikube tunnel

### check if ok

kubectl get ingress

should look something like this:
NAME                CLASS   HOSTS           ADDRESS        PORTS   AGE
dashboard-ingress   nginx   dashboard.com   192.168.49.2   80      106m

### test on browser with link:

dashboard.com

### TODO: CLEAN UP
