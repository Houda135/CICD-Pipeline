pipeline {
    agent any
    stages {
        stage('Send Test Email') {
            steps {
                emailext(
                    to: 'huda.uni@gmail.com',
                    subject: "Jenkins Email Extension Test",
                    body: "This is a test email sent from the Jenkins Email Extension Plugin.",
                    attachLog: true
                )
                echo 'Test email sent using emailext'
            }
        }
    }
}
