pipeline {
    agent any

    environment {
        PROJECT_NAME = "${env.JOB_NAME}"
        BUILD_NUMBER = "${env.BUILD_NUMBER}"
        BUILD_STATUS = "${currentBuild.currentResult}"
        BUILD_URL = "${env.BUILD_URL}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Build code using Maven
            }
            post {
                success {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Success",
                             body: """
                             Hello, below is your test report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Success
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """
                }
                failure {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Failure",
                             body: """
                             Hello, below is your test report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Failure
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                script {
                    def timestamp = new Date().format("dd-MM-yyyy HH:mm:ss")
                    writeFile file: 'test-logs.txt', text: "Unit and Integration Tests Log\nTimestamp: ${timestamp} - ${status}"
                }
            }
            post {
                always {
                    archiveArtifacts artifacts: 'test-logs.txt', allowEmptyArchive: true
                }
                success {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Tests Success",
                             body: """
                             Hello, below is your test report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Tests Success
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """,
                             attachmentsPattern: 'test-logs.txt'
                }
                failure {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Tests Failure",
                             body: """
                             Hello, below is your test report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Tests Failure
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """,
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
                script {
                    def timestamp = new Date().format("dd-MM-yyyy HH:mm:ss")
                    writeFile file: 'security-scan-logs.txt', text: "Security Scan Log\nTimestamp: ${timestamp} - ${status}"
                }
            }
            post {
                always {
                    archiveArtifacts artifacts: 'security-scan-logs.txt', allowEmptyArchive: true
                }
                success {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Security Scan Success",
                             body: """
                             Hello, below is your security scan report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Security Scan Success
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """,
                             attachmentsPattern: 'security-scan-logs.txt'
                }
                failure {
                    emailext to: "s220577892@gmail.com",
                             subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Security Scan Failure",
                             body: """
                             Hello, below is your security scan report.
                             
                             ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Security Scan Failure
                             
                             Check console output at ${BUILD_URL} to view the results.
                             
                             Thanks,
                             Automation Team
                             """,
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
        always {
            script {
                def timestamp = new Date().format("dd-MM-yyyy HH:mm:ss")
                writeFile file: 'pipeline-status-logs.txt', text: "Pipeline Status Log\nTimestamp: ${timestamp} - ${status}"
            }
            archiveArtifacts artifacts: 'pipeline-status-logs.txt', allowEmptyArchive: true
        }
        success {
            emailext to: "s220577892@gmail.com",
                     subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Pipeline Success",
                     body: """
                     Hello, below is your pipeline report.
                     
                     ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Pipeline Success
                     
                     Check console output at ${BUILD_URL} to view the results.
                     
                     Thanks,
                     Automation Team
                     """,
                     attachmentsPattern: 'pipeline-status-logs.txt'
        }
        failure {
            emailext to: "s220577892@gmail.com",
                     subject: "${PROJECT_NAME} - Build # ${BUILD_NUMBER} - Pipeline Failure",
                     body: """
                     Hello, below is your pipeline report.
                     
                     ${PROJECT_NAME} - Build # ${BUILD_NUMBER} - PIPELINE Failure
                     
                     Check console output at ${BUILD_URL} to view the results.
                     
                     Thanks,
                     Automation Team
                     """,
                     attachmentsPattern: 'pipeline-status-logs.txt'
        }
    }
}
