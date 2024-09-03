pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('CICD-Pipeline') {
                    echo 'Building the code using Maven...'
                    sh 'mvn clean package'
                }
            }
            post {
                success {
                    mail to: "huda.uni@gmail.com",
                         subject: "Build Status Email",
                         body: "Build was successful"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                dir('CICD-Pipeline') {
                    echo 'Running Unit and Integration Tests...'
                    sh 'mvn test'
                }
            }
            post {
                success {
                    mail to: "huda.uni@gmail.com",
                         subject: "Test Status Email",
                         body: "Tests were successful"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                dir('CICD-Pipeline') {
                    echo 'Analyzing code using Checkstyle...'
                    sh 'mvn checkstyle:check'
                }
            }
        }

        stage('Security Scan') {
            steps {
                dir('CICD-Pipeline') {
                    echo 'Running security scan using OWASP Dependency Check...'
                    sh 'mvn org.owasp:dependency-check-maven:check'
                }
            }
            post {
                success {
                    mail to: "huda.uni@gmail.com",
                         subject: "Security Scan Status Email",
                         body: "Security scan was successful"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                sh 'scp target/my-app-1.0-SNAPSHOT.jar user@staging-server:/path/to/deploy/'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging...'
                sh 'mvn verify -Dtest=IntegrationTestSuite'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                sh 'scp target/my-app-1.0-SNAPSHOT.jar user@production-server:/path/to/deploy/'
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
