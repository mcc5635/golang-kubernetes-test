# Prereq

## must have a DO cluster setup
## must have a DO registry created called **wdc_registry**


# Deploy

# 1. build container **docker build --platform=linux/amd64 -t registry.digitalocean.com/wdc-
# registry/key-value-app.**
# 2. push container **docker push registry.digitalocean.com/wdc-registry/key-value-app**
# 3. apply changes **kubectl apply -f k8s**


## Running Minikube

# 1. eval $(minikube docker-env)
# 2. build container **docker build --platform=linux/amd64 -t registry.digitalocean.com/wdc-
# registry/key-value-app.**
# 3. apply changes **kubectl apply -f k8s**
# 4. setup tunnel **minikube tunnel**
# 5. access localhost:80 for your service
# 6. dashboard **minikube dashboard** useful for debugging.


## Local Development

# 1. RABBIT_MQ_PASSWORD="BV5QxJAfupW1TZjy" RABBIT_MQ_HOST="localhost" FILE_PATH_PREFIX=./data air
# 2. POST@http://localhost:8080/keys/hello
# 3. GET@http://localhost:8080/keys/hello

## RabbitMQ

# 1. install **rabbitmq**

** helm repo add bitnami https://charts.bitnami.com/bitnami **
** helm install my-rabbitmq bitnami/rabbitmq **

# 1. forward ports for dashboard 
# 2. forward ports for dashboard kubectl port-forward svc/my-rabbitmq 15672:15672
# 3. forward this port too kubectl port-forward --namespace default svc/my-rabbitmq 5672:5672
# 4. open http://localhost:15672/
# 5. username: user
# 6. password: $(kubectl get secret --namespace default my-rabbitmq -o jsonpath="{.data.rabbitmq-password}" | base64 -d)
