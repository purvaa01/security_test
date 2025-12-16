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
                sh '''
                docker run --rm \
                -v "$(pwd):/usr/src" \
                sonarsource/sonar-scanner-cli \
                -Dsonar.projectKey=security-test \
                -Dsonar.projectName=SecurityTest \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://host.docker.internal:9000
                '''
            }
        }
    }
}
