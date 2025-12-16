pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Security Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
                      -Dsonar.projectKey=SecurityTest \
                      -Dsonar.projectName=SecurityTest \
                      -Dsonar.sources=. || true
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
