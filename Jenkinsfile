pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven."
                // shell or script step to use Maven
                // sh <<call a exceutable file>> 
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests using <<tools to use>>"
                // shell or script step for running tests
                // sh <<call a exceutable file>>
            }
            post {
                always {
                        emailext attachLog: true, attachmentsPattern: 'logs.txt',
                        to: "aliceantonita@gmail.com",
                        subject: "Jenkins Pipeline Notification: Security Scan Stage",
                        body: "Security Scan stage completed. Check attached logs for details."
                    }
                }
            }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube."
                // Example: SonarQube scanner step
                // sh <<call a exceutable file>>
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using <<write a tool>>"
                // Example: security scan script or tool command
                // sh <<call a exceutable file>>
            }
            post {
                    always {
                        emailext attachLog: true, attachmentsPattern: 'logs.txt',
                        to: "aliceantonita@gmail.com",
                        subject: "Jenkins Pipeline Notification: Security Scan Stage",
                        body: "Security Scan stage completed. Check attached logs for details."
                    }
                }
            }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 staging server."
                // Example: Deployment script or tool command
               // sh <<call a exceutable file>>
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging server."
                // Example: Integration test script or tool command
                // sh <<call a exceutable file>>
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 production server."
                // Example: Deployment script or tool command
                // sh <<call a exceutable file>>
            }
        }
    }
    post {
        always {
            echo "Cleaning up after the pipeline execution."
        }
    }
}
