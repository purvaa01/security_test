pipeline {
    agent any

    tools {
        sonarScanner 'SonarScanner'
    }

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
                    sonar-scanner \
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
