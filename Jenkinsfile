pipeline {
    agent any
    tools {
        nodejs "NodeJS"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', credentialsId: 'jen-git-token', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'
                
            }
        }
        stage(Unit Test)
            steps{
                sh 'npm test'
                sh 'npm install'

            }
    }
}



