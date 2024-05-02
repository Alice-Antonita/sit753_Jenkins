pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Placeholder step for build
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Placeholder step for unit tests
                echo 'Running unit tests...'
                // Placeholder step for integration tests
                echo 'Running integration tests...'
            }
            post {
                success {
                    emailNotification('Unit and Integration Tests', 'success')
                }
                failure {
                    emailNotification('Unit and Integration Tests', 'failure')
                }
            }
        }
        stage('Code Analysis') {
            steps {
                // Placeholder step for code
                echo 'Analyzing code...'
            }
        }
        stage('Security Scan') {
            steps {
                // Placeholder step for security 
                echo 'Scanning for security vulnerabilities...'
            }
            post {
                success {
                    emailNotification('Security Scan', 'success')
                }
                failure {
                    emailNotification('Security Scan', 'failure')
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Placeholder step for deployment to staging
                echo 'Deploying to staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Placeholder step for integration tests on staging
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Placeholder step for deployment to production
                echo 'Deploying to production server...'
            }
        }
    }

    post {
        always {
            // Archive the logs
            archiveArtifacts artifacts: 'logs/*.txt', allowEmptyArchive: true
        }
    }
}

def emailNotification(stageName, status) {
    emailext body: "Stage ${stageName} ${status}",
        subject: "Pipeline ${status.capitalize()}: ${stageName}",
        to: 'aliceantonita@deakin.edu.au',
        attachmentsPattern: 'logs/*.txt'
}
