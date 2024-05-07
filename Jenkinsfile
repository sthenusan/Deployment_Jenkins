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
        success {
            echo '=== Pipeline successfully executed ==='
            emailext body: "Pipeline execution succeeded. Check logs for details.", 
                     subject: "$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:", 
                     to: "thenusan.dev@gmail.com",
                     attachLog: true
        }
        failure {
            echo '=== Pipeline execution failed ==='
            emailext body: "Pipeline execution failed. Check logs for details.", 
                     subject: "$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:", 
                     to: "thenusan.dev@gmail.com",
                     attachLog: true
        }
    }
}