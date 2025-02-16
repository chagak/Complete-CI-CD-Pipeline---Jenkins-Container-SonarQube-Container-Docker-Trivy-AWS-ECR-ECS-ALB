pipeline{
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment {
        SONAR_PROJECT_KEY
    }
    stages {
        stage ('Checkout Code from github') {
            steps {
                git branch: 'main', url: 'https://github.com/chagak/Complete-CI-CD-Pipeline---Jenkins-Container-SonarQube-Container-Docker-Trivy-AWS-ECR-ECS-ALB.git'

            }
            
        }
        // stage ('Unit Test') {
        //     steps {
        //         sh 'npm install test'

        //     }
            
        // }

//         stage ('SonarQube Analysis') {
//             steps {
//                 withCredentials([string(credentialsId: 'complete-cicd-02', variable: 'SONAR_TOKEN')]) {
//                     withSonarQubeEnv (SonarQube) {
//                         sh """
//                         ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
//                         -Dsonar.projectkey=${SONAR_PROJECT_KEY} \
//                         -Dsonar.sources. \
//                         -Dsonar.host.url=http://sonar:9000 \
//                         -Dsonar.login.${SONAR_TOKEN}
//                         """
//     // some block
// }
// }

//             }
            
//         }

    }
}

