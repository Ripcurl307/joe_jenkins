pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'trey-cyber@talttem.com.au'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // Simulate build with Maven
                echo 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit'
                // Simulate tests
                echo 'mvn test'
            }
            post {
                always {
                    script {
                        def status = currentBuild.currentResult
                        mail bcc: '', body: "Stage 'Unit and Integration Tests' completed with status: ${status}\n\Log:\n ${BUILD_LOG, maxLines, escapeHtml}",
                             cc: '', from: '', mimeType: 'text/plain',
                             replyTo: '', subject: "Jenkins Pipeline - Unit and Integration Tests Status: ${status}",
                             to: "${env.EMAIL_RECIPIENT}"
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using SonarQube'
                // Simulate code analysis
                echo 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP'
                // Simulate security scan
                echo 'zap-cli scan'
            }
            post {
                always {
                    script {
                        def status = currentBuild.currentResult
                        mail bcc: '', body: "Stage 'Security Scan' completed with status: ${status}\n\Log:\n ${BUILD_LOG, maxLines, escapeHtml}", 
                             cc: '', from: '', mimeType: 'text/plain',
                             replyTo: '', subject: "Jenkins Pipeline - Security Scan Status: ${status}",
                             to: "${env.EMAIL_RECIPIENT}"
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server on AWS EC2'
                // Simulate deployment
                echo 'ssh user@staging-server "deploy_script.sh"'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment'
                // Simulate integration tests
                echo 'mvn verify'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server on AWS EC2'
                // Simulate deployment
                echo 'ssh joe@production-server "deploy_script.sh"'
                echo 'done'
            }
        }
    }
}
