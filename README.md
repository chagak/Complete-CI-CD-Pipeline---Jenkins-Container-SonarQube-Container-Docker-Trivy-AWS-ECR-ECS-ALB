# Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB
Complete CI/CD Pipeline - Jenkins Container, SonarQube Container, Docker, Trivy, AWS ECR, ECS &amp; ALB

Install docker
https://docs.docker.com/engine/install/linux-postinstall/

Install, minikube
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/


docker run -d --name jenkins \
-p 8080:8080 \
-p 50000:50000 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/bin/docker \
-u root \
-e DOCKER_GID=$(getent group docker | cut -d: -f3) \
--network minikube \
jenkins/jenkins:lts


docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword

