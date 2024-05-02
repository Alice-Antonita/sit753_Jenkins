pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Use Maven to build the code
                sh 'mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                
                // Run integration tests
                // Use a test automation tool like Selenium or JUnit
                sh 'mvn integration-test'
            }
        }
        
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool like SonarQube
                // Execute code analysis
                sh 'sonar-scanner'
            }
        }
        
        stage('Security Scan') {
            steps {
                // Perform security scan using a tool like OWASP ZAP
                sh 'zap-cli --zap-url <your_application_url> --spider --full-scan'
            }
            post {
                success {
                    echo 'Integration tests on staging passed'
                }
                failure {
                    echo 'Integration tests on staging failed'
                }
        }
        
        stage('Deploy to Staging') {
            steps {
                // Deploy to staging server using deployment tool like AWS CLI
                sh 'aws deploy <staging_server_details>'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                sh 'mvn integration-test -Dstaging=true'
            }
            post {
                success {
                    echo 'Integration tests on staging passed'
                }
                failure {
                    echo 'Integration tests on staging failed'
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                // Deploy to production server using deployment tool like AWS CLI
                sh 'aws deploy <production_server_details>'
            }
        }
    }
    
    post {
        always {
            // Send notification email at the end of test and security scan stages
            emailext(
                subject: "Pipeline Status: ${currentBuild.result}",
                body: "Pipeline execution ${currentBuild.result}: ${env.BUILD_URL}",
                to: "aliceantonita@deakin.edu.au",
                attachLog: true
            )
        }
    }
}
