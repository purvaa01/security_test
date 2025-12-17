pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Security Scan') {
            environment {
                SONAR_TOKEN = credentials('sonar-token')
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    /opt/sonar-scanner/sonar-scanner-7.3.0.5189-linux-x64/bin/sonar-scanner \
                      -Dsonar.projectKey=SecurityTest \
                      -Dsonar.projectName=SecurityTest \
                      -Dsonar.sources=. \
                      -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'SonarQube security scan executed'
        }
    }
}
