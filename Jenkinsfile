pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Building...'
            }
            post {
                success{
                    mail to: "s220577892@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was successful."
                }
            }
        stage('Unit and Integration Testing'){
            steps{
                echo 'Testing...'
            }
        stage('Code Analysis'){
            steps{
                echo 'Analysing Code...'
            }
        stage('Security Scan'){
            steps{
                echo 'Scanning for Vulnerabilities...'
            }
        stage('Integration Tests on Staging'){
            steps{
                echo 'Testing Staging Environment...'
            }
        stage('Deploy to Production'){
            steps{
                echo 'Deploying...'
            }
        }
    }
}
