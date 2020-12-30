
# Build the image
docker build -t guigo13/web-server-image:v1 .

# test the image
docker run -d -p 80:80 --name web-server-container guigo13/web-server-image:v1
curl localhost:80

# Commit the image
docker commit web-server-container guigo13/web-server-image:v1

# Push the image to DockerHub
docker push guigo13/web-server-image:v1

minikube start

kubectl create -f webserver.yaml

kubectl get pods
kubectl get pods --show-labels
kubectl get pods -L creation_method,env

kubectl expose pod web-server --type LoadBalancer --port 80 --target-port 80

kubectl logs web-server

kubectl delete pod web-server

kubectl delete all --all






