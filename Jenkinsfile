pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                // Run integration tests
                sh 'mvn integration-test'
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
                // Integrate SonarQube for code analysis
                // (steps to run SonarQube analysis)
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using OWASP ZAP or SonarQube
                // (steps to run security scan)
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
                // Deploy application to AWS EC2 staging server
                // (steps to deploy using Jenkins deployment plugin or Ansible)
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                // (steps to run integration tests on staging)
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy application to AWS EC2 production server
                // (steps to deploy using Jenkins deployment plugin or Ansible)
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
        to: 'recipient@example.com',
        attachmentsPattern: 'logs/*.txt'
}
