# scribetech-services

These 2 ques are assignments.

1. Create a deployment running nginx version 1.16.1 that will run 2 pods that uses /var/www as its root dir. Nginx should run on port 8090. It should mounts a volume and the volume should have a dir /var/www and contain a file "Hello SCRIBETECH" html.
2. Write a simple python program, that would expose itself to port 80 with HELLO SCRIBETECH message. Then, write yaml manifest for it, deploy it to K8S and expose it using nginx ingress. Create a Canary and blue-green deployment for it. This Pod should load before Nginx (you need to prove this).

___

### For Question 1

1. Upload the config files using the following command.
      
       kubectl create configmap nginx-config --from-file=default.conf

   This `default.config` is having the root location as `/var/www` for Nginx to load the html files from and the port `8090` on which Nginx will accept the traffic on.
2. Now you can apply the other things sequentially,
     - Deployment
     - Service  
     - Ingress
3. In the case of this Deployment, there's Init-container which waits for python service to up and running. And then it'll start the pod.
> [Apply.sh](que1/apply.sh) file can be found with the commands.
___

### For Question 2

1. You can use the Dockerfile to build the python code. This will be first install the requirements and then the run the python [app.py](que2/app.py) file using CMD. This is self hosted on port `80`.
2. Now you can go ahead and deploy the other files for python service,
      - Deployment
      - Service
3. For Canary Deployment, the file called [canary-ingress.yaml](que2/manifests/canary-ingress.yaml) will be executed. Which routes traffic on this service with weight on the new service.
4. For Blue-Green Deployment, the file called [blue-green-ingress.yaml](que2/manifests/blue-green-ingress.yaml) will be executed. This will modify existing Ingress with the new backend service, in our case it's python service.

   > [Makefile](que2/makefile) can found in the folder.