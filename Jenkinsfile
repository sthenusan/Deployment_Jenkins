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
            post {
                success {
                    // Send success email with logs as attachment
                    sendNotification('Unit and Integration Tests', 'SUCCESS')
                }
                failure {
                    // Send failure email with logs as attachment
                    sendNotification('Unit and Integration Tests', 'FAILURE')
                }
            }
        }

        stage('Code Analysis') {
            steps {
                // Use SonarQube for code analysis
                echo 'Running code analysis..'
            }
        }

        stage('Security Scan') {
            steps {
                // Use OWASP ZAP for security scanning
                echo 'Running security scan...'
            }
            post {
                success {
                    // Send success email with logs as attachment
                    sendNotification('Security Scan', 'SUCCESS')
                }
                failure {
                    // Send failure email with logs as attachment
                    sendNotification('Security Scan', 'FAILURE')
                }
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

    options {
        timestamps()
    }
    triggers {
        pollSCM('*/1 * * * *') // Poll the SCM (GitHub) every minute
    }
}

def sendNotification(stageName, status) {
    emailext (
        subject: "Pipeline Stage: ${stageName} ${status}",
        body: "Pipeline stage ${stageName} ${status.toLowerCase()}ed. Check logs for details.",
        to: "thenusan.dev@gmail.com",
        attachLog: true // Attach all log files in workspace
    )
}

