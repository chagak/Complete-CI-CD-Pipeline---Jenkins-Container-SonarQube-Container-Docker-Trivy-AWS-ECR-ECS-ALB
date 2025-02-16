pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment {
        SONAR_PROJECT_KEY = 'sonarqube-token'
        SONAR_SCANNER_HOME = tool 'SonarQubeScanner'
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
                withCredentials([string(credentialsId: 'sonarque-token', variable: 'SONAR_TOKEN')]) {
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
    }
}



// pipeline{
//     agent any
//     tools {
//         nodejs 'NodeJS'
//     }
//     environment {
//         SONAR_PROJECT_KEY = 'sonarqube-token'
//         SONAR_SCANNER_HOME = tool'SonarQubeScanner'
//     }
//     stages {
//         stage ('Checkout Code from github') {
//             steps {
//                 git branch: 'main', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'

//             }
            
//         }
//         stage ('Unit Test') {
//             steps {
//                 sh 'npm install test'

//             }
            
//         }

//         stage ('SonarQube Analysis') {
//             steps {
//                 withCredentials([string(credentialsId: 'jen-git-dind', variable: 'SONAR_TOKEN')]) {
//                     withSonarQubeEnv ('SonarQube') {
//                         sh """
//                             ${SONAR_SCANNER_HOME}/bin/sonar-scanner \\
//                             -Dsonar.projectKey=${SONAR_PROJECT_KEY} \\
//                             -Dsonar.sources=. \\
//                             -Dsonar.host.url=http://sonar:9000 \\
//                             -Dsonar.login=${SONAR_TOKEN}
//                             """

                       
//     // some block
// }
// }

//             }
            
//         }

//     }
// }

