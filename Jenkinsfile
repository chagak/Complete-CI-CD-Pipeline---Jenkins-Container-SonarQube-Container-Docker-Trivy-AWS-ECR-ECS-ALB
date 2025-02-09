pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment{
        SONAR_SCANNER_KEY = 'complete-cicd-02'
        SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
    }


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', credentialsId: 'jen-git-token', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'
                
            }
        }
        stage('Unit Test') {
            steps{
                sh 'npm test'
                sh 'npm install'

            }
        }


        stage('SonarQube Analysis') {
            steps{
                withCredentials([string(credentialsId: 'complete-cicd-02', variable: 'SONAR_TOKEN')]) {
                withSonarQubeEnv('SonarQube') {
                    sh"""
                    ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
                    -Dsonar.projectKey=${SONAR_SCANNER_KEY} \
                    -Dsonar.sources=.\
                    -Dsonar.host.url=http://localhost:9000 \
                    -Dsonar.login=${SONAR_TOKEN}
                     """
    // some block
}
}


            }
        }
    }
}




