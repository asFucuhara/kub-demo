
### apply kubernetes config files
kubectl apply -f mongo-secret.yaml 
kubectl apply -f mongo-configmap.yaml 
kubectl apply  -f mongo-express.yaml
kubectl apply -f mongo.yaml 

### service from minikube
minikube service list
minikube service mongo-express-service

### usefull commands
kubectl get pod
kubectl get all
kubectl describe service mongodb-service

### default login 
username: admin
password: pass


### clean 
kubectl delete deployment mongo-express
kubectl delete deployment mongodb-deployment
kubectl delete service/mongodb-service
kubectl delete service/mongo-express-service