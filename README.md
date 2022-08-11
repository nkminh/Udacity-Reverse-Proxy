# Overview
This is a very simple NodeJS project created for you to know how to reverse proxy working.
SERVICE-BE inside call to proxy then proxy targe to SERVICE-BE with path /api/

# Local Setup
* cd service-be
* Install dependencies: `npm install`
* Run server: `node server.js`

# Container Setup
* Build image: `docker build -t DOCKER_HUB/REPO(minhnk/heath-node) .`
* push to HUB: `docker push minhnk/heath-node`
* Run container with image: `docker run {image_id}` where `image_id` can be retrieved by running `docker images` and found under the column `IMAGE ID`
# deploy kubectl for BE
* create deployment : `kubectl appy -f service-be/deployment.yaml`
* create service : `kubectl appy -f service-be/service.yaml`
# deploy kubectl for reverse-proxy
* create deployment : `kubectl appy -f deployment.yaml`
* create service : `kubectl appy -f service.yaml`

# TEST
* get pods: `kubectl get pods`
* go inside pod: `kubectl exec -it my-app-health-99d8c7976-6867j sh`
* test connect to proxy the proxy forward BE: `curl http://reverseproxy-svc:8080/api/health` -> result : `Hello health!` -> SUCCESSFULLY
* exit: `exit`
