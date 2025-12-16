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
                /mnt/d/apps/sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner \
                -Dsonar.projectKey=security-test \
                -Dsonar.projectName=SecurityTest \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://localhost:9000
                '''
            }
        }
    }
}
