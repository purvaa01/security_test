pipeline {
    agent any

    tools {
        sonarScanner 'SonarScanner'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/purvaa01/security_test.git'
            }
        }

        stage('SonarQube Security Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=security-test \
                    -Dsonar.projectName=SecurityTest \
                    -Dsonar.sources=.
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'SonarQube security scan completed successfully'
        }
        failure {
            echo 'SonarQube security scan failed'
        }
    }
}
