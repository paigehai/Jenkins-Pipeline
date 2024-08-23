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
                // Run unit and integration tests using JUnit
            }
            post {
                success {
                    mail to: "s220577892@gmail.com",
                    subject: "Test Status Email",
                    body: "Unit and Integration Tests were successful."
                }
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Test Failure Email",
                    body: "Unit and Integration Tests failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analysing Code...'
                // Analyse code using ESLint
            }
            post {
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Code Analysis Failure Email",
                    body: "Code analysis failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scanning for Vulnerabilities...'
                // Perform security scan using OWASP ZAP
            }
            post {
                success {
                    mail to: "s220577892@gmail.com",
                    subject: "Security Scan Status Email",
                    body: "Security scan completed successfully."
                }
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Security Scan Failure Email",
                    body: "Security scan failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy application to staging server (AWS EC2)
            }
            post {
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Staging Deployment Failure Email",
                    body: "Deployment to staging failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Run integration tests on staging environment using JUnit
            }
            post {
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Staging Integration Test Failure Email",
                    body: "Integration tests on staging failed. Check Jenkins logs for more details."
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Deploy application to production server (AWS EC2)
            }
            post {
                failure {
                    mail to: "s220577892@gmail.com",
                    subject: "Production Deployment Failure Email",
                    body: "Deployment to production failed. Check Jenkins logs for more details."
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline Completed Successfully!'
            mail to: "s220577892@gmail.com",
            subject: "Pipeline Status Email",
            body: "Pipeline completed successfully."
        }
        failure {
            echo 'Pipeline Failed!'
            mail to: "s220577892@gmail.com",
            subject: "Pipeline Failure Email",
            body: "The pipeline failed. Please check the Jenkins logs for more details."
        }
    }
}
