pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "mvn clean package"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Unit and Integration Tests"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "sonar-scanner"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Perform security scan using a tool like OWASP ZAP"
            }
            post {
                success {
                    echo 'Integration tests on staging passed'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests on staging environment'
            }
            post {
                success {
                    echo 'Integration tests on staging passed'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }

        post {
            always {
                // Send notification email at the end of test and security scan stages
                emailext(
                    subject: "Pipeline Status: ${currentBuild.result}",
                    body: "Pipeline execution ${currentBuild.result}: ${env.BUILD_URL}",
                    to: "aliceantonita@gmail.com",
                    attachLog: true
                )
            }
        }
    }
}
