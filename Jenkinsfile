pipeline {
    agent any   
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                bat 'python -m py_compile app.py' 
                sleep time: 15, unit: 'SECONDS'
                milestone(1)
            }
        }
        stage('Send Notification') {
            steps {
                script {
                    def recipient = "manikandanrenu3@gmail.com"
                    def emailSubject = "Build Notification: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}"
                    def emailBody = "The build details can be found here: ${env.BUILD_URL}"         
                    try {
                        mail to: recipient,
                             subject: emailSubject,
                             body: emailBody
                    } catch (Exception e) {
                        echo "--- SMTP Not Configured. Simulating Email Notification ---"
                        echo "To: ${recipient}"
                        echo "Subject: ${emailSubject}"
                        echo "Body: ${emailBody}"
                        echo "--------------------------------------------------------"
                    }}}}}}
