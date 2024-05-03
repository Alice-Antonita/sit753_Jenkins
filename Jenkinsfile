pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven."
                // Maven is used for building the project
                // Example: sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests."
                // JUnit or TestNG for unit and integration tests
                // Example: sh 'mvn test'
            }
            post {
                always {
                    echo "Sending email notification."
                    emailext attachLog: true,
                        attachmentsPattern: '**/logs/*.txt', // Attach log files
                        to: "aliceantonita@gmail.com",
                        subject: "Jenkins Pipeline Notification: Unit and Integration Tests | Success",
                        body: "Unit and integration tests completed with status: Success. Check attached logs for details."
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube."
                // SonarQube for code analysis
                // Example: sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan."
                // OWASP ZAP or SonarQube for security scanning
                // Example: sh 'zap-cli -r report.html -t http://example.com'
            }
            post {
                always {
                    echo "Sending email notification."
                    emailext attachLog: true,
                        attachmentsPattern: '**/logs/*.txt', // Attach log files
                        to: "aliceantonita@gmail.com",
                        subject: "Jenkins Pipeline Notification: Security Scan | Success",
                        body: "Security scan completed with status: Success. Check attached logs for details."
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 staging server."
                // AWS CLI or custom deployment script for deploying to staging
                // Example: sh 'aws deploy ...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging server."
                // Selenium or Postman for integration tests
                // Example: sh 'newman run collection.json'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 production server."
                // AWS CLI or custom deployment script for deploying to production
                // Example: sh 'aws deploy ...'
            }
        }
    }
    post {
        always {
            echo "Cleaning up after the pipeline execution."
        }
    }
}
