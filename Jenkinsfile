pipeline{
    agent any
    tools {
        nodejs 'NodeJS'
    }
    stages {
        stage ('Checkout Code from github') {
            steps {
                git branch: 'main', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'

            }
            
        }
        stage ('Unit Test') {
            steps {
                sh 'npm install test'

            }
            
        }

    }
}

