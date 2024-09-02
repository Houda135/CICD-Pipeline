pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing Code...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded'
            mail to: 'huda.uni@gmail.com',
                 subject: "Jenkins Build Successful: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                 body: "Good news! The build for ${env.JOB_NAME} succeeded.\nCheck it out at: ${env.BUILD_URL}"
        }
        failure {
            echo 'Pipeline failed'
            mail to: 'huda.uni@gmail.com',
                 subject: "Jenkins Build Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                 body: "Unfortunately, the build for ${env.JOB_NAME} failed.\nCheck it out at: ${env.BUILD_URL}"
        }
    }
}
