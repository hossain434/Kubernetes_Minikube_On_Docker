1. Install Minikube: http://john-cd.com/cheatsheets/Containers/Minikube_Install_on_Windows/
2. start minikube: C:\MiniKube>minikube start --driver=docker
3. To build dockerfile: docker build -t arif/arifapp .
here arif/arifapp are docker image and tag is: latest.
4. Run Docker image locally: docker run -p 3000:3000 IMAGE-ID
5. (Optional) Push the image to docker hub: docker push arif/arifapp
6. Go to http://localhost:3000 to verify the working app
7. Create a pod in K8s: kubectl create -f pod-nodejs-docker-hw.yml
8. To see list of pod: kubectl get pods
9. To access the application on K8s: kubectl port-forward nodejs-docker-hw 8081:3000 (here the port 3000 of the container is exposed on port 8081 on the host system.)
curl http://localhost:8081
10. Go to http://localhost:8081 to access the application.
11. To access the application on K8s via service
kubectl expose pod nodejs-docker-hw --type=NodePort --name nodejs-hw-service
kubectl describe service nodejs-hw-service
Look for the port number defined for NodePort:
NodePort: <unset> 30469/TCP
Use the above port from local system to access the application: http://localhost:30469
12. (Alternate way of step 11) Expose the pod to the public internet using the kubectl expose command:kubectl expose deployment hello-node --type=LoadBalancer --port=8080
13. commands:
delete the Minikube VM:minikube delete, to stop: minikube stop, to clean up the resources you created: kubectl delete service hello-node, kubectl delete deployment hello-node, to get pod: kubectl get pod,svc -n kube-system, get services: kubectl get services.
14. Reference link:https://dzone.com/articles/get-your-first-application-on-kubernetes


