pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven...'
                // Tool: Maven
                // Task: Compile and package the code
                // Example command: mvn clean package
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit and integration tests...'
                // Tools: JUnit for unit tests, TestNG for integration tests
                // Task: Run unit and integration tests to ensure code quality
                // Example command: mvn test
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzing the code quality using Checkstyle...'
                // Tool: Checkstyle
                // Task: Perform static code analysis to enforce coding standards
                // Example command: mvn checkstyle:check
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Performing a security scan using OWASP Dependency Check...'
                // Tool: OWASP Dependency Check
                // Task: Scan the codebase for security vulnerabilities
                // Example command: mvn org.owasp:dependency-check-maven:check
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to a staging server...'
                // Task: Deploy the application to a staging environment (e.g., AWS EC2 instance)
                // Example command: scp target/my-app-1.0-SNAPSHOT.jar user@staging-server:/path/to/deploy/
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests on the staging environment...'
                // Task: Run integration tests to ensure the application works as expected in a production-like environment
                // Example command: mvn verify -Dtest=IntegrationTestSuite
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying the application to the production server...'
                // Task: Deploy the application to a production environment (e.g., AWS EC2 instance)
                // Example command: scp target/my-app-1.0-SNAPSHOT.jar user@production-server:/path/to/deploy/
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded'
            emailext(
                to: 'huda.uni@gmail.com',
                subject: "Jenkins Build Successful: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: "Build was successful. Check the build log.",
                attachLog: true
            )
            echo 'Success email sent with log attached'
        }
        failure {
            echo 'Pipeline failed'
            emailext(
                to: 'huda.uni@gmail.com',
                subject: "Jenkins Build Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: "Build failed. Check the build log.",
                attachLog: true
            )
            echo 'Failure email sent with log attached'
        }
    }
}
