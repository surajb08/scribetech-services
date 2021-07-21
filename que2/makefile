docker-build:
    docker build -t suraj08/scribetech-python:v1 .

docker-push:
    docker push suraj08/scribetech-python:v1

python-deploy:
    kubectl apply -f manifests/deployment.yaml
    kubectl apply -f manifests/service.yaml
	
python-deploy:
    kubectl apply -f manifests/canary-ingress.yaml
	
python-deploy:
    kubectl apply -f manifests/blue-green-ingress.yaml
