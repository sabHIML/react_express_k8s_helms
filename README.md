
## How to run the API
`docker build ./api -f api/Dockerfile -t practice-exress-api:v1`

`docker run -d -p9001:9000 --name express-api  practice-exress-api:v1` (first time)

`docker start express-api` (later on)

Check http://localhost:9001

#### Into container:
`docker exec -it express-api sh`

#### Logs:
`docker logs express-api`

## How to run the Client
`docker build ./client -f client/Dockerfile -t practice-react-client:v1`

`docker run -d -p3001:3000 --name react-client  practice-react-client:v1`

`docker start react-client` (later on)

Check http://localhost:3001

#### Into container:
`docker exec -it react-client sh`

#### Logs:
`docker logs react-client`

## Check if they are connected
1. With the two apps running, open browser in http://localhost:3001.
2. If you see a webpage saying `Welcome to React`, it means the FrontEnd is working.
3. If the same webpage has the phrase `API is working properly`, it means the API is working.
4. Enjoy!


### How to run the nginx
`docker build ./nginx -f nginx/Dockerfile -t practice-nginx:v1`

`docker run -d --p8090:80 --name nginx practice-nginx:v1`

`docker start practice-nginx` (later on)


### Minikube

`minikube start -p himel-local-profile --driver=docker`

`minikube dashboard -p himel-local-profile`

`eval $(minikube docker-env -p himel-local-profile)`

Run the above docker build commands again in cluster. otherwise cluster will not find the images.

## apply deployment and service files
cd to each of 3 service and run the following commands on each:

`kubectl apply -f <service>/deployment.yaml`

`kubectl apply -f <service>/services.yaml`

#### Check services and deployments with:
`kubectl get services`
`kubectl get deployments`

#### Access each service with:
`kubectl exec -it svc/<service-name> sh`

## Allocate LoadBalancer external ip for nginx service

`minikube service nginx-service -p himel-local-profile`

## Replace localhost url with service name in api calls and nginx config
then run all build commands again with new version.

