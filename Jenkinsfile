pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment {
        SONAR_PROJECT_KEY = 'sonarqube-token'
        SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
        DOCKER_HUB_REPO = 'kkouevi/complete-cicd-02'

    }
    stages {
        stage('Checkout Code from github') {
            steps {
                git branch: 'main', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'npm install test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'sonarqube-token', variable: 'SONAR_TOKEN')]) {
                    // Use the SonarQube installation name defined in Jenkins configuration.
                    withSonarQubeEnv('SonarQube') {
                        sh """
                            ${SONAR_SCANNER_HOME}/bin/sonar-scanner \\
                            -Dsonar.projectKey=${SONAR_PROJECT_KEY} \\
                            -Dsonar.sources=. \\
                            -Dsonar.host.url=http://sonar:9000 \\
                            -Dsonar.login=${SONAR_TOKEN}
                        """
                    }
                }
            }
        }


        stage('Build Docker image') {
            steps {
                //sh "docker build -t ${DOCKER_HUB_REPO}:latest . "
                sh "docker build -t chaganote ."
            }
        }

        stage('Trivy Scan') {
            steps {
                sh """
                trivy image --no-progress -o trivy-report.html ${DOCKER_HUB_REPO}:latest
                """
            }
        }


        stage('Login to ECR') {
            steps {
                sh """
                aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 871909687521.dkr.ecr.us-east-1.amazonaws.com

                """
            }
        }

        stage('Login to ECR') {
            steps {
                sh """
                docker tag chaganote:latest 871909687521.dkr.ecr.us-east-1.amazonaws.com/chaganote:latest

                docker push 871909687521.dkr.ecr.us-east-1.amazonaws.com/chaganote:latest

                """
            }
        }
    }
}
