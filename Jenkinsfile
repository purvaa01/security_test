pipeline {
    agent any

    tools {
        sonarScanner 'SonarQubd'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Security Scan') {
            steps {
                sh '''
                sonar-scanner \
                -Dsonar.projectKey=security-test \
                -Dsonar.projectName=SecurityTest \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://localhost:9000
                '''
            }
        }
    }
}
