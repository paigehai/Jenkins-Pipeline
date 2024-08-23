pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Build code using Maven
            }
            post {
                success {
                    mail to: "s220577892@gmail.com",
                         subject: "Build Status Email",
                         body: "Build was successful."
                }
                failure {
                    mail to: "s220577892@gmail.com",
                         subject: "Build Failure Email",
                         body: "Build failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Generate dummy log for unit and integration tests
                writeFile file: 'test-logs.txt', text: 'Unit and Integration Tests Log\nTimestamp: ${new Date()}'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'test-logs.txt', allowEmptyArchive: true
                    emailext to: "s220577892@gmail.com",
                             subject: "Test Status Email",
                             body: "Unit and Integration Tests were successful. See attached logs.",
                             attachmentsPattern: 'test-logs.txt'
                }
                failure {
                    archiveArtifacts artifacts: 'test-logs.txt', allowEmptyArchive: true
                    emailext to: "s220577892@gmail.com",
                             subject: "Test Failure Email",
                             body: "Unit and Integration Tests failed. Check the attached logs for more details.",
                             attachmentsPattern: 'test-logs.txt'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analysing Code...'
                // Code analysis steps
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scanning for Vulnerabilities...'
                // Generate dummy log for security scan
                writeFile file: 'security-scan-logs.txt', text: 'Security Scan Log\nTimestamp: ${new Date()}'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'security-scan-logs.txt', allowEmptyArchive: true
                    emailext to: "s220577892@gmail.com",
                             subject: "Security Scan Status Email",
                             body: "Security scan completed successfully. See attached logs.",
                             attachmentsPattern: 'security-scan-logs.txt'
                }
                failure {
                    archiveArtifacts artifacts: 'security-scan-logs.txt', allowEmptyArchive: true
                    emailext to: "s220577892@gmail.com",
                             subject: "Security Scan Failure Email",
                             body: "Security scan failed. Check the attached logs for more details.",
                             attachmentsPattern: 'security-scan-logs.txt'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy application to staging server (AWS EC2)
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Integration tests steps
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy application to production server (AWS EC2)
            }
        }
    }

    post {
        success {
            echo 'Pipeline Completed Successfully!'
            // Generate dummy log for pipeline status
            writeFile file: 'pipeline-status-logs.txt', text: 'Pipeline Status Log\nTimestamp: ${new Date()}'
            emailext to: "s220577892@gmail.com",
                     subject: "Pipeline Status Email",
                     body: "Pipeline completed successfully. See attached logs.",
                     attachmentsPattern: 'pipeline-status-logs.txt'
        }
        failure {
            echo 'Pipeline Failed!'
            // Generate dummy log for pipeline status
            writeFile file: 'pipeline-status-logs.txt', text: 'Pipeline Status Log\nTimestamp: ${new Date()}'
            emailext to: "s220577892@gmail.com",
                     subject: "Pipeline Failure Email",
                     body: "The pipeline failed. Please check the attached logs for more details.",
                     attachmentsPattern: 'pipeline-status-logs.txt'
        }
    }
}
