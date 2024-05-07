pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Use Maven for building the code
                echo 'Building the code...'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Use JUnit for unit tests and tools like Selenium for integration tests
                echo 'Running unit and integration tests...'
            }
        }

        stage('Code Analysis') {
            steps {
                // Use SonarQube for code analysis
                echo 'Running code analysis...'
            }
        }

        stage('Security Scan') {
            steps {
                // Use OWASP ZAP for security scanning
                echo 'Running security scan...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Use AWS CLI to deploy to staging (EC2 instance)
                echo 'Deploying to staging server...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                echo 'Running integration tests on staging...'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Use AWS CLI to deploy to production (EC2 instance)
                echo 'Deploying to production server...'
            }
        }
    }
    
        // Define a delay before the pipeline stages are executed
    options {
        timestamps() // Show timestamps in build output
    }
    triggers {
        pollSCM('*/1 * * * *') // Poll the SCM (GitHub) every minute
    }
post {
        always {
            // Send email notification regardless of build result
            sendEmail("thenusan1997@gmail.com", "Pipeline Notification", "Pipeline execution completed.")
        }
        success {
            // Send email notification on successful build
            sendEmail("thenusan1997@gmail.com", "Pipeline Success", "Pipeline executed successfully.")
        }
        failure {
            // Send email notification on build failure
            sendEmail("thenusan1997@gmail.com", "Pipeline Failed", "Pipeline execution failed.")
        }
    }
}

def sendEmail(String to, String subject, String body) {
    mail to: to,
         subject: subject,
         body: body
}